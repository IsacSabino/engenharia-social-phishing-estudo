# Engenharia Social e Phishing — Entendendo para Defender

> Projeto de estudo da formação **Cybersecurity Specialist (DIO)**
> Autor: **Isac Sabino Alves** — [LinkedIn](https://www.linkedin.com/in/isacsabino/)
> Foco: **segurança defensiva (Blue Team)**

---

## 🎯 Objetivo do projeto

Este projeto documenta meu estudo sobre **engenharia social** e **phishing** dentro de um
ambiente de laboratório controlado, usando o **Kali Linux**.

O objetivo **não** é aprender a atacar pessoas, e sim **entender como o ataque funciona por
dentro para saber reconhecê-lo, detectá-lo e defender usuários e empresas** — que é o trabalho
de um analista de SOC / Blue Team.

> ⚠️ **Aviso ético e legal**
> Todo o estudo foi feito em uma **máquina virtual isolada**, contra uma **página de teste
> própria**, sem envolver sites, serviços ou credenciais de terceiros. Clonar páginas reais e
> capturar senhas de outras pessoas é **crime** (Lei 12.737/2012 e Lei 14.155/2021) e
> **violação de ética profissional**. Este repositório é educacional e defensivo.

---

## 🧪 Ambiente de laboratório

| Item | Configuração |
|---|---|
| Virtualizador | Oracle VirtualBox |
| Sistema | Kali Linux (VM dedicada ao estudo) |
| Rede | Rede isolada / host-only, sem exposição à internet |
| Acesso | Apenas eu mesmo, dentro da própria VM |

**Decisão técnica:** mantive o laboratório **isolado da internet**. Um teste de phishing nunca
deve ficar acessível para fora, para não haver risco de alguém real cair na página.

---

## 🔍 O que é phishing (o conceito)

**Phishing** é um ataque de **engenharia social**: em vez de explorar uma falha técnica, ele
explora a **confiança e a pressa das pessoas**. O atacante se passa por alguém confiável (um
banco, uma rede social, o RH da empresa) para induzir a vítima a:

- digitar login e senha em uma página falsa;
- clicar em um link malicioso;
- baixar um anexo infectado;
- aprovar um pagamento ou transferência.

### Por que funciona
- Usa **urgência** ("sua conta será bloqueada em 24h");
- Usa **autoridade** (finge ser o chefe ou o banco);
- Imita o **visual** de marcas conhecidas;
- Aproveita a **distração** do dia a dia.

---

## ⚙️ Como a técnica funciona (visão de alto nível)

Ferramentas como o **SET (Social-Engineer Toolkit)**, presentes no Kali, automatizam a criação
de páginas falsas. Em termos gerais, o fluxo de um ataque de *credential harvesting* é:

1. O atacante **hospeda uma página de login falsa** parecida com a verdadeira;
2. **Distribui o link** por e-mail, SMS ou mensagem (a parte de engenharia social);
3. A vítima digita as credenciais achando que é o site real;
4. Os dados são **enviados para o atacante** em vez do serviço legítimo.

> Descrevo o **mecanismo** para fins de defesa. Não publico o passo a passo de clonagem de um
> site real nem de captura de credenciais, justamente por ser conteúdo ofensivo utilizável.

O que observei no laboratório, com minha página de teste, foi **como o dado digitado trafega** e
**por que a vítima não percebe** — informação que uso na seção de defesa abaixo.

---

## 🛡️ Como reconhecer um phishing (o que mais importa)

| Sinal | O que verificar |
|---|---|
| **URL / domínio** | `faceb00k-login.com`, domínios estranhos, subdomínios longos |
| **Cadeado / HTTPS** | HTTPS **não** garante que o site é legítimo, mas a falta dele é alerta |
| **Erros de português** | Textos mal escritos, tradução estranha |
| **Urgência** | "Aja agora ou perca o acesso" |
| **Remetente** | E-mail que não bate com o domínio oficial |
| **Link encurtado** | Esconde o destino real — passar o mouse antes de clicar |

---

## 🧰 Como defender (usuário e empresa)

**Usuário**
- Desconfiar de urgência e conferir o domínio antes de digitar senha;
- Nunca clicar em link de e-mail para acessar banco/serviço — digitar o endereço direto;
- Ativar **MFA (autenticação de dois fatores)** em todas as contas.

**Empresa / SOC**
- **MFA obrigatório** — mesmo com a senha vazada, o atacante não entra;
- **Filtros de e-mail** (anti-phishing, SPF, DKIM, DMARC);
- **Conscientização** — treinar e simular phishing com os próprios colaboradores;
- **Monitoramento no SIEM** — logins de locais/horários incomuns, muitos erros de senha;
- **Bloqueio de domínios** recém-registrados e parecidos com os da empresa.

---

## 📚 O que aprendi

- Phishing depende mais de **psicologia** do que de tecnologia;
- Entender o ataque é o que permite **criar defesas eficazes**;
- A camada mais forte de defesa continua sendo a **pessoa bem treinada** somada ao **MFA**.

---

## 🔗 Referências

- Formação Cybersecurity Specialist — DIO
- OWASP — Phishing
- CISA — Recognizing and Avoiding Phishing

---

*Projeto de estudo. Uso exclusivamente educacional e defensivo, em ambiente isolado.*
