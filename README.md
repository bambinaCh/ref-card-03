# Dokumentation zu "Ref-Card-3-mit-Ansible-und-MaaS"

Author: Chaimaa El Jarite

## Einleitung
Diese Aufgabe besteht darin eine Automatisierte Installation von Zwei MAAS-Instanzen mithilfe von Ansible Multipass zu machen.

### Ziel der Aufgabe:
  -  Zwei MaaS instanzen: Datenbank und Webserver
  -  JokesDB auf der Datenbank konfigurieren
  -  Schlussendlich soll eine Verbindung der beiden Instanzen erstellt werden, damit man Zugriff auf die Ref-Card-3.0 hat.

### Projektstrucktur
Folgende Komponenten werden in der Aufsetzungs des Projekts gebraucht:
```
- ansible.cfg: um Konfigurationseinstellungen für Ansible zu definieren und anzupassen.

- Cloud-init.yml: um die Instanzen mit definierte Kriterien (mit BBW-Maas) zu erstellen

- hosts: um Hostnamen oder IP-Adressen von Zielsystemen zu definieren, auf denen Ansible-Aufgaben oder Playbooks ausgeführt werden sollen.

- playbook.yml: automatisierte Aufgaben und Konfigurationsschritte für die Ausführung auf Zielsystemen.
```

## Projekt

### Aufsetzung
- Virtuelle Maschinen in der BBW Maas Aufsetzen 
![Alt text](image-1.png)

- WireGuard runterladen und Aktivieren
![Alt text](image-2.png)

- Installieren von Ansible
```
$ sudo apt update
$ sudo apt install ansible
```


- SSH Key generieren
```
$ ssh-keygen
```
![Alt text](image.png)

- SSH Public Key anzeigen
```
$ cd /home/user/.ssh
$ cat id_rsa.pub
```


- Ansible Configuration File (ansible.cfg)
```
Ein "ansible.cfg"-Datei wird verwendet, um Konfigurationseinstellungen für Ansible zu definieren und anzupassen.
```
![Alt text](image-3.png)


- Hosts File
```
Ein "hosts"-Datei in Ansible wird verwendet, um Hostnamen oder IP-Adressen von Zielsystemen zu definieren, auf denen Ansible-Aufgaben oder Playbooks ausgeführt werden sollen.
```

```
Version 1 hosts -> FALSCH
```
![Alt text](image-4.png)


```
Version 2 hosts -> Richtig
```
![Alt text](image-5.png)



- Cloud Init File (cloud-init.yml)
```
Ein "cloud-init.yml"-Datei wird genutzt, um automatisierte Konfigurationen für virtuelle Maschinen in Cloud-Umgebungen festzulegen. 

Diese Datei enthält YAML-formatierte Anweisungen, die beim Starten einer VM durch das Cloud-Init-Tool interpretiert werden, um beispielsweise Benutzer, Netzwerkeinstellungen und Skriptausführungen zu konfigurieren.
```

![Alt text](image-6.png)


- Virtual Maschine ping

```
Fehler
```
![Alt text](image-7.png)

![Alt text](image-8.png)


```
Lösung
```
![Alt text](image-9.png)

![Alt text](image-10.png)




### AUTOMATIZIERUNG - ROLLE VERZEICHNIS


- Make Ansible Role
![Alt text](image-11.png)


- main.yml - tasks

![Alt text](image-12.png)
![Alt text](image-13.png)


- main.yml - meta

![Alt text](image-14.png)



- install_instances.yml

![Alt text](image-15.png)


- Error bei der erstellung my_ansible_role

![Alt text](image-16.png)

