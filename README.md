# Ritual

Aplicativo pessoal de rotina semanal de skincare, banho, corpo e sono.
HTML estático, sem build, sem dependências.

## Estrutura

```
index.html              ← app principal (servido pelo GitHub Pages)
manifest.webmanifest    ← metadados pra instalar como app
icons/                  ← ícones (favicon, apple-touch, Android)
README.md
```

## Publicar no GitHub Pages

1. Crie um repositório público no GitHub (ex.: `ritual`).
2. Faça o commit destes arquivos na branch `main`:
   ```bash
   git init
   git add .
   git commit -m "primeiro ritual"
   git branch -M main
   git remote add origin https://github.com/<seu-usuario>/ritual.git
   git push -u origin main
   ```
3. No GitHub, vá em **Settings → Pages**:
   - **Source**: `Deploy from a branch`
   - **Branch**: `main` · `/ (root)`
   - Salvar.
4. Aguarde ~1 minuto. O site fica disponível em:
   `https://<seu-usuario>.github.io/ritual/`

> Quer um domínio próprio? Em **Settings → Pages → Custom domain** você aponta um domínio que você possua (precisa configurar o DNS).

## Instalar como app no celular

### iPhone (Safari)
1. Abra a URL no **Safari** (não Chrome).
2. Toque no botão de **compartilhar** (□↑).
3. Escolha **"Adicionar à Tela de Início"**.
4. Confirme o nome "Ritual" e toque em **Adicionar**.
5. O ícone aparece na home como um app — abre em tela cheia, sem barra do Safari.

### Android (Chrome)
1. Abra a URL no Chrome.
2. Toque no menu **⋮** no canto superior.
3. Escolha **"Instalar app"** ou **"Adicionar à tela inicial"**.
4. Confirme. O Chrome usa o ícone maskable automaticamente.

## Editar conteúdo

Tudo está em `index.html`. Para mudar produtos, dias, frequências:
- **Dias da semana e o ativo da noite**: array `DAYS` no `<script>`.
- **Frequências dos ativos**: tabela `$('freqBox').innerHTML = [...]` no fim do script.
- **Itens de cada momento**: função `buildShift(day, shift, opts)` — manhã e noite são construídas ali.

## Comportamento automático

- O **dia atual** é detectado ao carregar a página.
- O **turno** alterna automaticamente:
  - 00h–17h59 → **Dia ☀**
  - 18h–23h59 → **Noite ☾**
- A virada acontece a cada **reload** da página. Se você quiser que mude sozinho com a aba aberta, posso adicionar um timer.

## Privacidade

Nada é enviado pra lugar nenhum. As marcações de check ficam só em memória — recarregou a página, zerou. Sem cookies, sem tracking, sem analytics.
