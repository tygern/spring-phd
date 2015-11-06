## Instructions to connect to HAWQ

1. Download Pivotal HD 3.0 VM from https://github.com/tzolov/vagrant-pivotalhd/.
2. Install the VM with the default blueprint following instructions in the readme.
3. Start the VM with `vagrant up`.
4. Change the postgres config on `phd3`.

  ```bash
  vagrant ssh phd3
  sudo vi /data/hawq/master/gpseg-1/pg_hba.conf
  ```

  add the following line

  ```
  host     all         gpadmin         10.211.55.1/32       trust
  ```

5. Use Ambari to restart the HAWQ service.
6. To check that everthing is configured correctly, try to connect with `psql`

  ```bash
  psql -h10.211.55.103 -Ugpadmin
  ```