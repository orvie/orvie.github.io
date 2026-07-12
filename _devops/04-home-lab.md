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