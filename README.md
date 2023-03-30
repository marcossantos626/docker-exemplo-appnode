Docker = 
Porque os containert vai ajudar a gente 
Nginx Java C#
Colocar elas em uma maquina, para nossa aplicação possa rodar
Nginx 
 - Porta = 80 
 - Versão = 1.17.0 
Java 
 - Porta = 80
 - Versão = 17 
C# 
 - Porta = 80
 - Versão = 9

Principais problemas:
 - Conflito de portas?
 - Alterar as versões de maneira pratica?
 - Controle de recursos de memoria e CPU?
 - Processo de manutenção?

Solução (SIMPLES) inicial: 
 - Uma maquina para cada recurso. 
 # Probleme > Recursos financeiro 
 
 - Máquina Virtual 
 * Isolado do SO orginal 
 # Realmente é necessario


 - Container
 * Não tem a camada de Hypervison

Por que são mais leves?
 - Um conteiner trabalha com processos

   

Como garante o isolamento?
   # Namescapes  -> Com a utilização de namespaces, os containers conseguem garantir isolamento em diversas camadas.
   * PID -> Provê isolamento dos processos rodando dentro do container
   * NET -> Provê isolamento das interfaces de rede
   * IPC -> Provê isolamento da comunicação entre processos e memoria compartilhada 
   * MNT -> Provê isolamento do sistema de arquivos / ponto de montagem
   * UTS -> Provê isolamento do kernel. Age como se o container fosse outro host 

Como funcionam sem "instalar um SO"?
   * UTS -> Provê isolamento do kernel. Age como se o container fosse outro host 
   Provê isolamento do kernel. Age como se o container fosse outro host 
   * Ele tem acesso ao KERNEL do sistema original isoladamente

Como fica a divisão de recursos do sistema?
   * Cgroups -> 

O que são imagens?
 # Um conjunto de camadas, quando juntamos essas camadas fomamos uma imagem, cada camada tem o seu identificados.
 * R/O não podemos modificar a imagem
 * R/W é criada quando executamos um container (temporaria)

Como imagens viram containers?

como criamos nossas próprias imagens?

Qual porta nossa aplicação esta sendo execuitada?
 EXPOSE > podemos usar para expor qual é a saida da nossa aplicação
 A instrução ARG carrega variáveis apenas no momento de build da imagem,
 enquanto a instrução ENV carrega variáveis que serão utilizadas no container.
 Desta maneira, é possível diferenciar o que é necessário para a etapa de build e para a etapa de execução.

COMANDOS:
sudo service docker start
 * Iniciar o docker

docker images

docker inspect IMAGE ID 
 * Descreve a imagem

docker history IMAGE ID 

docker stop $(docker container ls -q)
 * para todos os container 
 * $ valor de entrada
 * docker container ls lista os containers em execução
 * -q pegar do o ID

