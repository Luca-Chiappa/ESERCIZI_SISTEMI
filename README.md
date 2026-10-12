# Cheat sheet

## Esercitazioni essenziali su Cisco Packet Tracer v8.2+ 

compatibili con la ver. 9.0.0.0810 in uso a scuola.

# Casi d'Uso

1. [Routing tra reti: Configurare la comunicazione completa tra 3 diverse sottoreti](caso1/routing-statico.md).
2. Servizio DHCP: Configurare un server DHCP all'interno di una delle sottoreti.
3. DHCP Relay Agent: Configurare il relay agent (ip helper-address) per servire le subnet sprovviste di server DHCP locale.
4. Servizio DNS & Web: Configurare un server DNS essenziale

# Configurazione VLAN su Switch Cisco (SW1)

Questa guida rapida mostra i passaggi fondamentali per configurare le VLAN su uno switch Cisco, assegnare le porte alle rispettive reti virtuali e verificare il corretto funzionamento.

## Operazioni Preliminari

```text
Switch> enable
Switch# configure terminal
Switch(config)# hostname SW1

show interfaces status  <- Usare spesso per verificare lo stato delle porte
```

---

## Fase 1 - Creazione delle VLAN
Creiamo tre VLAN distinte assegnando a ciascuna un numero identificativo e un nome descrittivo.

```text
SW1(config)# vlan 10
SW1(config-vlan)# name STUDENTI
SW1(config-vlan)# exit

SW1(config)# vlan 20
SW1(config-vlan)# name DOCENTI
SW1(config-vlan)# exit

SW1(config)# vlan 30
SW1(config-vlan)# name SEGRETERIA
SW1(config-vlan)# exit
```

---

## Fase 2 - Associazione delle porte alle VLAN
Configuriamo le interfacce in modalità di accesso (*access*) e le associamo alle relative VLAN precedentemente create.

### VLAN 10 (STUDENTI)
```text
SW1(config)# interface range fa0/1, fa0/2
SW1(config-if-range)# switchport mode access
SW1(config-if-range)# switchport access vlan 10
SW1(config-if-range)# exit
```

### VLAN 20 (DOCENTI)
```text
SW1(config)# interface range fa0/3, fa0/4
SW1(config-if-range)# switchport mode access
SW1(config-if-range)# switchport access vlan 20
SW1(config-if-range)# exit
```

### VLAN 30 (SEGRETERIA)
```text
SW1(config)# interface range fa0/5-8
SW1(config-if-range)# switchport mode access
SW1(config-if-range)# switchport access vlan 30
SW1(config-if-range)# exit
```

---

## Fase 3 - Verifica e Salvataggio
Usciamo dalla modalità di configurazione globale, verifichiamo la configurazione attiva e salviamo tutto nella memoria permanente dello switch.

```text
SW1(config)# end

SW1# show vlan brief
SW1# copy running-config startup-config
