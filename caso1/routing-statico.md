## Scenario 1 – Tre reti LAN PRIVATE con router collegati ad anello (Routing Statico)

### Topologia

Lo scenario prevede un'architettura **multi-router** con ridondanza dei percorsi:

- **3 router** (esempio: modello 1941)
- **3 switch** (esempio: modello 2960)
- **3 reti LAN PRIVATE (RFC 1918) distinte** (una per ogni router)
- Ogni LAN è collegata a uno switch, a sua volta connesso a un'interfaccia del router
- I router sono interconnessi tramite **link punto-punto** seriali (3 reti /30)
- **Topologia ad anello (ring)**: ogni router è collegato ad altri due, garantendo ridondanza

Questa configurazione permette di avere percorsi alternativi in caso di guasto di un link.

---
