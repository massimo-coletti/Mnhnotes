<hr>

Loops and dictionaries

https://stackoverflow.com/questions/61039955/ansible-inline-jinja-templating-out-to-a-list

```
set_fact:
  vm_disks: >-
     {%- set results = [] -%}
     {%- for disk in additional_disks|default([]) -%}
     {%-   set d = {"datastore": datastore_name} -%}
     {%-   set _ = d.update({"size_gb": disk.size_gb} if (disk.size_gb is defined) else {}) -%}
     {%-   set _ = results.append(d) -%}
     {%- endfor -%}
     {{ results }}
```

And also:

```
- name: "Get facts for named template"
  vmware_guest_disk_info:
    hostname: "{{ vcenter_server }}"
    username: "{{ vcenter_user }}"
    password: "{{ vcenter_pass }}"
    validate_certs: False
    datacenter: "{{ datacenter_name }}"
    name: "{{ template_name }}"
  register: template_disk
  delegate_to: localhost

- name: "Define new disk structure"
  set_fact:
    vm_disks: >-
      {%- set results = [] -%}
      {%- for osdisk in ( template_disk.guest_disk_info | dictsort ) -%}
        {%- set od = { "size_kb": osdisk[1].capacity_in_kb } -%}
        {%- set _ = od.update({ "datastore": osdisk[1].backing_datastore }) -%}
        {%- set _ = results.append(od) -%}
      {%- endfor -%}
      {%- for disk in additional_disks|default([]) -%}
        {%- if (disk.size_gb is defined) -%}
          {%- set d = {"size_gb": disk.size_gb} -%}
        {%- elif (disk.size_mb is defined) -%}
          {%- set d = {"size_mb": disk.size_mb} -%}
        {%- elif (disk.size_kb is defined) -%}
          {%- set d = {"size_kb": disk.size_kb} -%}
        {%- endif -%}
        {%- set _ = d.update({"datastore": disk.datastore_name}) -%}
        {%- set _ = results.append(d) -%}
      {%- endfor -%}
      {{ results }}
```

<hr>
