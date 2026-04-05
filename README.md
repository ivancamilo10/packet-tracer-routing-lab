# Laboratorio: Subnetting, VLANs, Trunking y ACLs en Cisco 

Este repositorio contiene la resolución del laboratorio de la Semana 5 sobre redes empresariales. El proyecto demuestra la configuración práctica de una topología básica utilizando equipos Cisco, segmentación lógica mediante VLANs, enrutamiento inter-VLAN (Router-on-a-Stick) y políticas de seguridad a través de Listas de Control de Acceso (ACLs).

## 🛠️ Tecnologías y Herramientas Utilizadas
- **Simulador:** Cisco Packet Tracer
- **Dispositivos:** 1x Switch Cisco 2960, 1x Router Cisco 1941, 8x PCs
- **Protocolos y Tecnologías:** 802.1Q (Trunking), IPv4, ICMP

## 📋 Arquitectura de la Red

La red está segmentada en 4 VLANs distintas, cada una con su propia subred y puerta de enlace configurada en las subinterfaces del router:

- **VLAN 10 (Ventas):** `192.168.10.0/24`
- **VLAN 20 (Ingeniería):** `192.168.20.0/24`
- **VLAN 30 (DMZ):** `192.168.30.0/24`
- **VLAN 40 (Contabilidad):** `192.168.40.0/24`

##  Políticas de Seguridad Aplicadas (ACLs)

Para garantizar la seguridad de la red y cumplir con los requerimientos del laboratorio, se implementaron las siguientes restricciones de tráfico:

1. **ACL Estándar (Lista 10):**
   - **Objetivo:** Restringir el acceso total de la red de Ventas hacia la red de Contabilidad por motivos de privacidad financiera.
   - **Acción:** Deniega el tráfico desde `192.168.10.0/24` aplicado en la interfaz de salida de la VLAN 40.

2. **ACL Extendida (Lista 100):**
   - **Objetivo:** Proteger la zona desmilitarizada (DMZ).
   - **Acción:** Deniega los paquetes ICMP (Ping) desde la red de Ingeniería (`192.168.20.0/24`) hacia la DMZ (`192.168.30.0/24`), pero permite cualquier otro tipo de tráfico IP.

---
*Laboratorio desarrollado por Ivan Mejia - Estudiante de Ingeniería de Sistemas*
