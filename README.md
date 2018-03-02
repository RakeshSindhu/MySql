# MySql
Install Mysql and start mysql services
---
- name: Install MySql
  hosts: 172.18.124.149
  user: root
  become: true
  tasks:
  - name: Copy repo file
    copy: src=/etc/yum.repos.d/rhel.repo dest=/etc/yum.repos.d/rhel.repo

  - name: Install mysqld
    action: yum pkg={{item}} state=present
    with_items:
        - mysql
        - mysql-server
        - mysql-test
        - mysql-bench
        - mysql-connector-java
        - mysql-connector-odbc
        - mysql-devel


  - name: Start mysqld
    service:
      name: mysqld
      state: started
