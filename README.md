# 📦 ghaction-k8s-setup

> Instala y configura herramientas esenciales para Kubernetes + SOPS:  
> 🔐 [SOPS](https://github.com/mozilla/sops) • 🔧 [KSOPS](https://github.com/viaduct-ai/kustomize-sops) • 🔑 [age](https://github.com/FiloSottile/age)

---

## 🚀 ¿Qué hace esta acción?

- Instala:
  - KSOPS (plugin para usar `sops` con `kustomize`)
  - Mozilla SOPS
  - Age + configura la clave privada (`SOPS_AGE_KEY`)
- Prepara el entorno para Kustomize con secretos cifrados.

---

## 🧩 Uso

### 1. Añade esta acción a tu workflow

```yaml
jobs:
  setup:
    runs-on: ubuntu-latest
    steps:
      - uses: migbertweb/ghaction-k8s-setup@main
        with:
          ksops_version: "4.3.3"
          sops_version: "latest"
          age_version: "1.2.1"
        env:
          SOPS_AGE_KEY: ${{ secrets.SOPS_AGE_KEY }}
