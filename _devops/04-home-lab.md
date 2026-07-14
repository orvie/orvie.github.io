---
layout: page
title: Home Laboratory
---

# Guía de Configuración de Acceso Remoto Seguro (Cloudflare Tunnels & SSH)

Este documento resume la arquitectura y los pasos exactos realizados para configurar el acceso remoto seguro a tu ThinkCentre utilizando **Cloudflare Tunnels**. Con esta configuración, puedes conectarte de forma segura desde cualquier red del mundo por SSH o HTTP sin abrir puertos en tu router (CGNAT-proof) mediante una arquitectura de red zero-trust.

## 1. Configuración de la Placa Base (Hardware)
Para garantizar que el servidor vuelva a la vida automáticamente ante un corte de energía o caída de tensión:
1. Reiniciar la máquina y pulsar repetidamente `F1` (o `Enter`) para entrar a la **BIOS**.
2. Navegar hasta la pestaña **Power**.
3. Cambiar la opción **After Power Loss** (o *AC Power Recovery*) de *Power Off* a **Power On**.
4. Guardar cambios con `F10` y arrancar el sistema operativo de forma normal.

## 2. Configuración en la Computadora Cliente (Tu Laptop/PC)
Para interceptar el tráfico local SSH y enrutarlo de forma transparente a través de la infraestructura perimetral de Cloudflare:

### Paso A: Instalar el cliente del túnel
Ejecutar en la terminal local (según tu sistema operativo):

```bash
# En Windows (usando PowerShell o CMD limpio)
winget install Cloudflare.cloudflared
```

## 99. Ia lab local
[Install gemma4 guide](https://fair-fruitadens-35f.notion.site/KireBot-Gu-a-Completa-Monta-Tu-Propio-Departamento-de-Inteligencia-Artificial-Local-Desde-Cero-33cf5d11703680deb5fcdbc85ca3ab11)

## 100. Infra IA lab

![Infra preview]({{ "/public/local_ai_infra.jpg" | relative_url }})

| Componente / Parte | Tipo de Elemento | Especificación Clave | Plataforma de Compra | Precio Estimado (COP) |
| :--- | :--- | :--- | :--- | :--- |
| **AMD Ryzen 7 7700X - Zen 4 8-Core 4.5 GHz - Socket AM5 - 105W Desktop Processor** | Procesador (CPU) | 8 Núcleos / 16 Hilos, 5.3 GHz Max Boost, Socket AM5, incluye gráficos integrados (para dar video a tu monitor). | ebay | $770,000 |
| **MSI MAG B850 Tomahawk MAX WiFi Motherboard, ATX - Compatible con procesadores AMD Ryzen 9000/8000/7000, AM5-80A SPS VRM, DDR5 Memory Boost 8400+ MT/s (OC), PCIe 5.0 x16, M.2 Gen5, Wi-Fi 7, LAN 5G** | Tarjeta Madre (Motherboard) | Socket AM5, soporte PCIe 5.0, Wi-Fi 7 nativo, excelente disipación en VRM y Shield Frozr para el SSD. | amazon | $1'000,000 |
| **G.SKILL Trident Z5 Royal Neo 32GB (2x16GB) DDR5 6400 CL30 AMD EXPO RAM Silver** | Memoria RAM (Kit 2 x 16GB) | Frecuencia ideal de 6000 MHz, Latencia baja CL30, **Certificación AMD EXPO** obligatoria. | ebay | $1'610,000 |
| **SAMSUNG 990 PRO SSD 1TB PCIe 4.0 M.2 2280 Internal Solid State Hard Drive, Seq.** | Almacenamiento SSD M.2 | NVMe PCIe 4.0, velocidades de lectura de hasta 7.450 MB/s. **Versión plana sin disipador** (usas el de la placa). | ebay | $1'010,000 |
| **NVIDIA Tesla P40 24GB GDDR5 PCIe 3.0 x16 GPU Accelerator Card 900-2G610-0000-000** | Tarjeta Gráfica (GPU para IA) | 24GB GDDR5, 3484 CUDA Cores, arquitectura Pascal. Ideal para LLMs locales y procesamiento pesado. | eBay | $1'500,000 |
| **Msi Mag A850gl 850w 80+ Gold Atx 3.1 Modular / MSI MAG 850W A850GL PCIE 5.0 80+ GOLD Fully Modular Gaming PSU, 12VHPWR Cable** | Fuente de Poder | 850W, Certificación 80+ Gold, Totalmente Modular, compatible con el estándar moderno **ATX 3.1 / PCIe 5.1**. | MercadoLibre | $550,000 |
| **Chasis Xpg Valor Air Pro + 4 Fan Argb** | Chasis (Gabinete) | Tamaño ATX, **panel frontal de malla (Mesh)** para flujo de aire masivo, incluye 4 ventiladores de fábrica. | MercadoLibre Colombia | $409,000 |
| **Enfriador De Cpu Thermalright Royal Knight 120 Se, 155 Mm** | Disipador para CPU | Enfriamiento por aire de doble torre, 6 heatpipes, altura de 155mm (entra perfecto en el chasis). | MercadoLibre | $178,000 |
| **NVIDIA Tesla Graphics Card Power Cable 8 Pin PCIE for P40 P100 K80 M40 M60 V100** | Accesorio Eléctrico | Cable especial **Dual PCIe de 8 pines (Hembra) a EPS de 8 pines (Macho)** para conectar la Tesla a la fuente MSI. | eBay | $30,000 |
| **Ventilador Portátil Para Barbacoa De 12 V 5300 Rpm** | Refrigeración GPU | Ventilador extractor tipo turbina de 12V 2.94A con potenciómetro y **clavija para conectar directo a la pared**. | mercado libre | $35,000 |
| **Adaptador Plástico (Shroud P40)** | Canalizador de Aire | Embudo plástico que une la Tesla P40 con la turbina Blower 9733. | eBay / Impresión 3D Local | $20,000 |
| **Total** |  |  |  | **$7,112,000** |