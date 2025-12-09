# Engeto Projekt 1 – Úkol 1

## Důkaz
- Virtuální stroj běží ve VirtualBoxu
- VM má privátní IP adresu `192.168.0.214`
- Úspěšný ping je vidět na snímku níže

![VM ping screenshot](01_VMping.png)
# Engeto Projekt 1 – Úkol 2

## Cíl
Zprovoznit SSH přístup pro uživatele `sysadmin` pomocí veřejného klíče, s povoleným heslovým přihlášením pro běžné uživatele a zakázaným root heslem.

## Důkaz
- Vygenerovaný klíč pro `sysadmin` (RSA 4096)  
  ![SSH keygen screenshot](02_id_rsa_sysadmin_keygen.png)
- Nasazení veřejného klíče do `/home/sysadmin/.ssh/authorized_keys`  
  ![Authorized keys screenshot](03_sysadmin_authorized_keys_permissions.png)
- Konfigurace SSH (`sshd_config`)  
  ![sshd_config screenshot](04_sshd_config_pubkey_and_password.png)
- Restart služby a ověření běhu  
  ![systemctl status ssh screenshot](05_systemctl-status-ssh.png)
- Úspěšné přihlášení uživatele `sysadmin` přes SSH  
  ![SSH login screenshot](06_successful-ssh-login-sysadmin.png)
- Ověření konfigurace příkazem `grep`  
  ![grep ssh config screenshot](07_grep-ssh-config.png)
  
# Engeto Projekt 1 - Úkol 3

## Cíl
Zprovoznit Apache webový server s podporou PHP a ověřit funkčnost pomocí `phpinfo()`.

## Důkaz
- Instalace Apache a PHP modulu (`libapache2-mod-php`)
- Vytvoření souboru `info.php` v `/var/www/html`
- Ověření funkčnosti přes `http://localhost/info.php`
- Screenshot s výpisem PHP konfigurace (`phpinfo()`)
![phpinfo_screenshot](08_phpinfo.png)

---

# Engeto Projekt 1 - Úkol 4

## Cíl
Nakonfigurovat Apache tak, aby běžel na portu 8081 s vlastním VirtualHostem a PHP skriptem.

## Důkaz
- Úprava konfigurace: `Listen 8081` v `000-default.conf`  
![apache_listen_screenshot](09_apache_listen_8081.png)

- Vytvořen VirtualHost v `/etc/apache2/sites-available/engeto.conf`:
  ```apache
  <VirtualHost *:8081>
      DocumentRoot /srv/www/engeto
      <Directory /srv/www/engeto>
          Require all granted
      </Directory>
  </VirtualHost>
  
