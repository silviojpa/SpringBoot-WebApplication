## Tecnoligias utilizadas 
- Ubuntu ou Intancia na provide Azure / AWS obs: Utilize uma T2 larger para usar Jenkins e Sonarqube
- Docker
- Jenkins
- Sonarqube
- Dempendency Checks
- Trivy
  
1 Verifica o arquivo step.txt para baixar e atualizar os programas necessario.


## Análise Detalhada das Etapas do Pipeline
# Compreendendo o Fluxo de Trabalho

O pipeline apresentado automatiza o processo de desenvolvimento, teste, construção e implantação de uma aplicação Java. Ele integra diversas ferramentas e tecnologias para garantir a qualidade e a eficiência do processo de entrega.

# Descrição Detalhada de Cada Etapa

- stage('Git Checkout ') Checkout do Git:

Objetivo: Baixar o código fonte do repositório Git para a máquina onde o pipeline está sendo executado.
Detalhes: Especifica o branch main e a URL do repositório.

- stage('Code Compile') Compilação do Código:

Objetivo: Compilar o código fonte Java em bytecode.
Detalhes: Utiliza o Maven para executar o comando compile.

- stage('Run Test Cases') Execução dos Testes:

Objetivo: Executar os testes unitários e de integração para garantir a qualidade do código.
Detalhes: Utiliza o Maven para executar o comando test.

- stage('Sonarqube Analysis') Análise SonarQube:

Objetivo: Analisar o código em busca de problemas de qualidade, segurança e cobertura de testes.
Detalhes: Utiliza o SonarQube Scanner para analisar o código e gerar um relatório detalhado.

- stage('OWASP Dependency Check') Verificação de Dependências OWASP:

Objetivo: Verificar se as dependências do projeto possuem vulnerabilidades conhecidas.
Detalhes: Utiliza a ferramenta OWASP Dependency Check para analisar as dependências e gerar um relatório.

- stage('Maven Build') Construção do Projeto:

Objetivo: Construir o projeto em um artefato final, como um JAR ou WAR.
Detalhes: Utiliza o Maven para executar o comando clean package.

- stage('Docker Build & Push') Construção e Envio da Imagem Docker:

Objetivo: Criar uma imagem Docker com a aplicação e enviá-la para um registro Docker.
Detalhes: Utiliza o Docker para construir a imagem, taguea-la e enviá-la para o registro.

- stage('Trivvy Docker Image scan') Análise de Vulnerabilidades da Imagem Docker:

Objetivo: Verificar se a imagem Docker possui vulnerabilidades conhecidas.
Detalhes: Utiliza a ferramenta Trivy para analisar a imagem e gerar um relatório.

- stage('Docker Deploy') Implantação da Imagem Docker:

Objetivo: Executar um container Docker com a imagem recém-construída.
Detalhes: Utiliza o Docker para executar um container e mapear a porta 8081 da máquina host para a porta 8081 do container.

# Resumo

O pipeline automatiza todo o processo de desenvolvimento, desde o checkout do código até a implantação da aplicação em um container Docker. Ele utiliza diversas ferramentas para garantir a qualidade do código, a segurança das dependências e a eficiência do processo de entrega.

# Pontos Chave:

Integração contínua: O pipeline é executado automaticamente a cada alteração no código.
Entrega contínua: A aplicação é implantada em um ambiente de produção de forma automatizada.
Qualidade do código: O SonarQube e o OWASP Dependency Check garantem a qualidade e a segurança do código.
Contêinerização: A aplicação é empacotada em um container Docker para facilitar a portabilidade e a escalabilidade.

---------------------------

MIT License

Copyright (c) 2022 vidushidocker

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
