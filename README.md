# SeniorNet

Red inalámbrica y plataforma web educativa para el desarrollo de competencias digitales en adultos mayores en Colombia.

Proyecto desarrollado como trabajo final de la materia **Redes de Computadores** — Universidad Nacional de Colombia, Facultad de Ingeniería, Bogotá, 2025.

---

## Descripción

SeniorNet es un sistema integrado compuesto por dos partes:

1. **Infraestructura de red local (WLAN)** — Red inalámbrica segmentada por VLANs con portal cautivo y políticas de calidad de servicio (QoS), diseñada para espacios comunitarios como salones comunales, bibliotecas o centros de día.

2. **Plataforma web educativa** — Sitio web local que funciona sin conexión a internet externa, accesible desde cualquier celular conectado a la red. Contiene lecciones paso a paso adaptadas para adultos mayores con conocimiento tecnológico básico.

El objetivo es reducir la brecha digital en adultos mayores colombianos, enseñándoles a usar herramientas digitales cotidianas y a protegerse de fraudes electrónicos.

---

## Módulos de aprendizaje

| Módulo | Tema | Herramientas |
|--------|------|--------------|
| 01 | Comunicación digital | WhatsApp |
| 02 | Movilidad urbana | Google Maps, TransMiSITP |
| 03 | Documentos en la nube | Gmail, Google Drive |
| 04 | Seguridad digital | Identificación de fraudes, CAI Virtual |

---

## Arquitectura de red

```
Internet (ISP)
      |
   Router          Gateway + DHCP
      |
   Switch          Segmentación por VLANs
      |
  WiFi AP          Cobertura del espacio comunitario
      |
  Servidor local   Plataforma web SeniorNet (offline-first)
      |
  Celulares        Participantes, tutores
```

**VLANs configuradas:**

- `VLAN 10` — Participantes: acceso a la plataforma e internet básico
- `VLAN 20` — Tutores: seguimiento del progreso de los participantes
- `VLAN 30` — Administración: configuración completa de la red

---

## Estructura del repositorio

```
seniornet/
├── index.html          # Plataforma web educativa (archivo único)
├── README.md
└── docs/
    └── SeniorNet_Guia_Visual.docx   # Guía completa del proyecto
```

---

## Cómo usar la plataforma web

La plataforma está contenida en un solo archivo `index.html`. Para desplegarla localmente:

```bash
# Opción 1: Python (sin instalación adicional)
python3 -m http.server 8080

# Opción 2: Node.js
npx serve .
```

Luego abrir `http://localhost:8080` en el navegador, o en cualquier celular conectado a la misma red.

Para desplegarla en el servidor local de la red comunitaria (Raspberry Pi o PC reciclado):

```bash
# Instalar Nginx
sudo apt install nginx

# Copiar el archivo
sudo cp index.html /var/www/html/index.html

# Iniciar el servicio
sudo systemctl start nginx
```

---

## Requisitos de infraestructura

| Componente | Especificación |
|------------|----------------|
| Router | TP-Link Archer AX23 o similar |
| Switch gestionable | TP-Link TL-SG108E (8 puertos) |
| Puntos de acceso WiFi | TP-Link EAP225 (1-2 unidades) |
| Servidor local | Raspberry Pi 4 o PC reciclado con Linux |
| Regulador de voltaje | UPS 650VA |

Costo estimado de infraestructura: entre $1.500.000 y $2.500.000 COP (pago único).

---

## Autor

**Manuel Federico Castro Suárez**  
Universidad Nacional de Colombia — Facultad de Ingeniería  
Redes de Computadores — Bogotá, 2025
