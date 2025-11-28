# Documentação: Criando um bucket S3 e publicando site estático

Este repositório contém **prints** e um passo-a-passo de como criar um bucket no Amazon S3 e ativar a hospedagem de um site estático. Atividade prática de laboratório para preparação da certificação AWS Cloud Practitioner através do programa **AWS re/Start da Escola da Nuvem**.

---

## Estrutura do Repositorio


├── imagens-do-console-aws/

├── arquivos-do-site-estatico/

└──README.md

---

🧠 Habilidades adquiridas: 
- Criação e configuração de um bucket do Amazon S3 no AWS Console
- Realização de upload de arquivos (HTML, CSS, JPG)
- Ativar hospedagem de site específico no S3
- Configuração de permissões e políticas para acesso público
- Acessar a URL pública do site

---

🛠️ Tecnologias Utilizadas

<img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" width="80"/><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" width="60"/><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" width="60"/>


---

## Sumário
1. Criar bucket no S3 desativando bloqueio de acesso público (Block Public Access)
3. Fazer upload dos arquivos (index.html, style.css, assets/)
4. Ativar Static Website Hosting
5. Definir bucket policy
6. Acessar o endpoint do site

---

## Passo a passo (resumo)

### 1) Criar bucket no S3 desativando Block Public Access
- Abra o Console AWS > S3 > Create bucket
  
![Acessando o console](Imagens%20do%20console%20AWS/01-acessar-servico-s3.jpg)
![Iniciando a criacao](Imagens%20do%20console%20AWS/02-iniciar-criacao-do-bucket.jpg)

- Nome do bucket usado no exemplo: `meu-bucket-portfolio-aws`

![Nome do bucket](Imagens%20do%20console%20AWS/03-adicionar-tag-nome.jpg)
  
- Desabilite ACLs

![ACLs](Imagens%20do%20console%20AWS/04-configurar-propriedade.jpg)

- Desmarque *Block all public access* para obter acesso ao site público.

![Desativar bloqueio](Imagens%20do%20console%20AWS/05-desativar-bloqueio-publico.jpg)

- Crie o bucket

![Crie o bucket](Imagens%20do%20console%20AWS/06-criar-bucket.jpg)


### 2) Fazer upload dos arquivos
- Acesse o bucket criado
 
![Acesse o bucket](Imagens%20do%20console%20AWS/07-bucket-criado.jpg)

- Faça o upload de arquivos/pastas

![Iniciando upload](Imagens%20do%20console%20AWS/08-iniciar-upload.jpg)
![Tipo de upload](Imagens%20do%20console%20AWS/09-escolher-tipo-de-upload.jpg)
![Subindo arquivos](Imagens%20do%20console%20AWS/10-fazer-upload.jpg)
![Arquivos no bucket](Imagens%20do%20console%20AWS/11-upload-feito.jpg)

### 3) Ativar Static Website Hosting
- Ao acessar o bucket criado, acesse a tab **Properties**

![Bucket criado](Imagens%20do%20console%20AWS/12-selecionando-bucket.jpg)
![Propriedades](Imagens%20do%20console%20AWS/13-acessando-propriedades-do-bucket.jpg)

- Na opção Static Website Hosting, selecionde **Edit**

![Editando hospedagem](Imagens%20do%20console%20AWS/14-acessando-edicao-de-site.jpg)

- Selecione **Activate** e coloque o nome do arquivo index.html no campo **Document index**

![Ativando hospedagem](Imagens%20do%20console%20AWS/15-ativando-hospedagem-de-site.jpg)

- Ao salvar, a URL do endpoint para acessar o site estático hospedado no bucket aparece na tela seguinte

![Endpoint](Imagens%20do%20console%20AWS/16-url-de-acesso-ao-site-no-bucket.jpg)

### 4) Definir Bucket Policy para leitura pública
- Em **Permissions → Bucket policy** cole a policy:
```json
{
  "Version":"2012-10-17",
  "Statement":[
    {
      "Sid":"PublicRead",
      "Effect":"Allow",
      "Principal":"*",
      "Action":"s3:GetObject",
      "Resource":"arn:aws:s3:::meu-bucket-portfolio-aws/*"
    }
  ]
}
```
![Permissoes](Imagens%20do%20console%20AWS/17-acessando-permissoes-do-bucket.jpg)
![Editar politica](Imagens%20do%20console%20AWS/18-acessando-edicao-de-politicas.jpg)
![Criar politica](Imagens%20do%20console%20AWS/19-inserindo-politica-de-acesso-publico.jpg)
![Politica criada](Imagens%20do%20console%20AWS/20-politica-de-bucket-criada.jpg)

### 5) Acessar a URL pública do site
- Copie a URL do endpoint adquirida anteriormente e cole em uma nova aba do seu navegador para acessar o site hospedado (atenção no protocolo http e não https)

![Site](Imagens%20do%20console%20AWS/21.Site%20portfolio.jpg)

---

⚠️ Observação

O site exibido não está mais disponível , pois a tarefa foi realizada em um sandbox da AWS com tempo limitado de execução. O laboratório tem duração de cerca de 3 horas, após o tempo corrido os recursos são automaticamente encerrados.
