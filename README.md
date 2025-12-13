# Engeto Projekt 1 – LAMP stack na vlastní VM

Tento repozitář obsahuje důkazy k jednotlivým úkolům projektu.  
Všechny snímky jsou uloženy ve složce `./screenshots/`.

---

## Úkol 1 – Ověření dostupnosti VM a přihlášení přes SSH

### Cíl
Ověřit, že VM je dostupná v síti a že se lze přihlásit přes SSH jako uživatel `milan`.

### Důkaz
- `screenshots/Ukol1_ping_a_SSH_milan.png`  
  Obsahuje úspěšný ping na IP `192.168.0.214` a následné přihlášení přes SSH jako `milan`.

---

## Úkol 2 – SSH pro uživatele sysadmin

### Cíl
Zprovoznit SSH přístup pro uživatele `sysadmin` pomocí veřejného klíče, zakázat heslové přihlášení a nepovolit přímý root login.

### Důkazy
- `screenshots/Ukol2_SSH_keygen.png`  
  Generování a nastavení privátního klíče pro uživatele `sysadmin`.
- `screenshots/Ukol2_sshd_config_root_no.png`  
  Konfigurace SSH: `PermitRootLogin no`, `PasswordAuthentication no`, `PubkeyAuthentication yes`.
- `screenshots/Ukol2_SSH_password_fail.png`  
  Neúspěšný pokus o přihlášení heslem: `Permission denied (publickey)`.
- `screenshots/Ukol2_SSH_key_success.png`  
  Úspěšné přihlášení klíčem jako `sysadmin` a následné `sudo -i` → prompt `root@milan:~#`.
- `screenshots/Ukol2_sysadmin_user_check.png`  
  Kontrola účtu `sysadmin`, skupin a složky `.ssh` s právy `600`.

---

## Shrnutí

- Úkol 1: VM dostupná, přihlášení jako `milan` přes SSH → splněno ✅  
- Úkol 2: SSH pro `sysadmin` jen přes klíč, zákaz hesla a root login → splněno ✅  

---

## Poznámky

- Všechny snímky jsou uloženy ve složce `screenshots/`.  
- README obsahuje odkazy na konkrétní snímky pro každý úkol.  
- Konfigurace byla ověřena příkazy `id`, `groups`, `ls -la`, `systemctl restart ssh` a testovacími přihlášeními.
