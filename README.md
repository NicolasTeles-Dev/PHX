# PHX — PHP Version Manager (Linux x64)

Gerenciador de versões do PHP simples, rápido e direto ao ponto.

---

## Recursos
- Instala versões específicas do PHP via CDN
- Alterna globalmente (`phx use`)
- Alterna por projeto com `.php_version`
- Lista versões instaladas e remotas
- Verifica SHA256 antes de instalar
- Sem dependências externas além de `curl`, `tar` e `jq`

---

## Instalação (provisória)
```bash
git clone https://github.com/NicolasTeles-Dev/phx-binaries.git phx
cd phx
chmod +x phx.sh
```
Opcional mover para PATH:
```bash
sudo mv phx.sh /usr/local/bin/phx
```

---

## Shell Integration
```bash
phx init >> ~/.bashrc
source ~/.bashrc
```

---

## Comandos
### Listar versões remotas
```bash
phx list-remote
```
### Instalar
```bash
phx install 8.2.12
```
### Listar instaladas
```bash
phx list
```
### Usar global
```bash
phx use 8.2.12
```
Adicionar ao PATH:
```bash
export PATH="$PHX_DIR/current/bin:$PATH"
```

### Local por projeto
```bash
phx local 8.1.27
```
Gera `.php_version`.

### Ver versão ativa
```bash
phx current
```

### Remover instalação
```bash
phx uninstall 8.2.12
```

---

## Estrutura
```
phx/
 ├ phx.sh
 ├ current -> versions/8.x.x
 └ versions/
      ├ 8.2.12/
      ├ 8.1.27/
      └ ...
```

---

## Como funciona
1. Busca `versions.json` no CDN
2. Seleciona versão
3. Baixa tar.gz
4. Valida SHA256
5. Extrai em `versions/<versão>`
6. Atualiza `current`

---

## ⚙️ GitHub Actions — Compilação Automática das Versões 8.x do PHP

[github - phx-binaries](https://github.com/NicolasTeles-Dev/phx-binaries)

Este repositório inclui um workflow do **GitHub Actions** responsável por **compilar, empacotar e publicar** versões do **PHP 8.x** no formato `.tar.gz`, prontas para uso direto com o **PHX**.

A automação garante que cada build seja:

* **Consistente**
* **Reprodutível**
* **Verificado por SHA256**
* **Disponível imediatamente via CDN** para instalação pelo CLI

Essa estrutura reduz o trabalho manual e torna o processo de distribuição de versões PHP muito mais simples para toda a comunidade.

---

### 🤝 Como contribuir

Você pode contribuir melhorando ou expandindo a pipeline. Algumas ideias:

* **Adicionar suporte ARM64** (Apple Silicon, servidores ARM etc.)
* **Incluir extensões extras no build**
* **Criar pipelines para PHP 7.x ou 5.x**
* **Otimizar caching e tempo de build**
* **Reduzir o tamanho final dos binários**
* **Automatizar a atualização do `versions.json`**

Pull Requests são bem-vindos — o foco é fortalecer a comunidade PHP e manter o projeto evoluindo de forma colaborativa.


## Contribuindo
Pull requests são bem-vindos.

Sugestões:
- Novos binários PHP
- Ajustes no script
- Melhorias CLI
- Documentação
- Testes

---

## Licença
MIT — mantenha o crédito.

