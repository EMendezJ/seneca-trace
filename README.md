# Seneca Trace — Landing

Landing estática para [senecatrace.com](https://senecatrace.com).

## Preview local

```bash
cd ~/Projects/seneca-trace
python3 -m http.server 8080
# Abre http://localhost:8080
```

## 1. Formulario (Formspree)

1. Crea cuenta en [formspree.io](https://formspree.io) (gratis hasta ~50 envíos/mes).
2. **New form** → pon tu email (ej. el de Gmail/Tec).
3. Copia el endpoint: `https://formspree.io/f/xxxxxx`
4. En `index.html`, reemplaza `YOUR_FORM_ID` en el `action` del formulario.

## 2. Deploy en Vercel

1. Sube el repo a GitHub (desde esta carpeta):

   ```bash
   git add .
   git commit -m "Add Seneca Trace landing"
   gh repo create seneca-trace --public --source=. --push
   ```

   (O crea el repo manualmente en github.com y `git push`.)

2. Ve a [vercel.com](https://vercel.com) → **Add New Project** → importa `seneca-trace`.
3. Framework: **Other** (es HTML estático, sin build).
4. Deploy. Te dará una URL tipo `seneca-trace.vercel.app`.

## 3. Conectar senecatrace.com (Porkbun → Vercel)

En **Vercel** → Project → **Settings** → **Domains** → Add `senecatrace.com` y `www.senecatrace.com`.

Vercel te muestra los registros DNS. En **Porkbun**:

1. Domain Management → `senecatrace.com` → **DNS**
2. Agrega:
   - **A** `@` → `76.76.21.21` (IP de Vercel; confirma en el panel de Vercel)
   - **CNAME** `www` → `cname.vercel-dns.com`
3. Espera 5–30 min (propagación DNS).

## 4. Email hello@senecatrace.com (opcional)

Porkbun incluye **email forwarding** gratis:

- Porkbun → senecatrace.com → Email → Forward `hello@senecatrace.com` → tu Gmail.

## Stack

- HTML + Tailwind CDN
- Formspree (waitlist)
- Vercel (hosting)
