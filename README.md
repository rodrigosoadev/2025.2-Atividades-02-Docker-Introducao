# S.O. 2025.2 - Atividade 01 - Introdução a linux usando docker no windows

## Informações gerais

- **Objetivo do repositório**: Repositório da disciplina para atividade avaliativa dos alunos
- **Assunto**: Introdução a docker/linux
- **Público alvo**: alunos da disciplina de SO (Sistemas Operacionais) do curso de TADS (Superior em Tecnologia em Análise e Desenvolvimento de Sistemas) no CNAT-IFRN (Instituto Federal de Educação, Ciência e Tecnologia do Rio Grande do Norte - Campus Natal-Central).
- disciplina: **SO** [Sistemas Operacionais](https://github.com/sistemas-operacionais/)
- professor: [Leonardo A. Minora](https://github.com/leonardo-minora)

---

## Sumário

1. [Tutorial introdutório Linux](https://github.com/sistemas-operacionais/2025-2-Notas-03-Linux-Intro)
2. Prática e atividade avaliativa

---

## Parte 2. Prática e atividade avaliativa

Atividades práticas com Linux em um contêiner Docker (Fedora).

**Objetivo**: realizar exercícios práticos com comandos básicos do Linux em um contêiner Docker baseado no Fedora. Ao final, os alunos devem gerar um relatório com imagens das atividades realizadas.  

---

### 2.1. Pré-requisitos
- Docker instalado ([Guia de instalação](https://docs.docker.com/engine/install/))  
- Terminal (Linux/macOS) ou PowerShell/WSL (Windows)  

---

### 📌 2.2. Atividades

#### 📌 2.2.1. Iniciar um contêiner Fedora

**Objetivo:** Baixar imagem do Fedora e executar um contêiner.

Execute o seguinte comando para baixar a imagem do Fedora e iniciar um contêiner interativo:  

```bash
docker run -it --name fedora-tutorial fedora:latest /bin/bash
```

Descrevendo as opções do comando:
- `-it` → Modo interativo  
- `--name fedora-tutorial` → Nome do contêiner  
- `fedora:latest` → Imagem utilizada  

---

#### 📌 2.2.2. Navegação básica

**Objetivo:** Familiarizar-se com comandos de navegação.  

1. Verifique em qual diretório você está:  
   ```bash
   pwd
   ```
2. Acesse o diretório home do usuário
   ```bash
   cd ~
   ```
3. Liste os arquivos e pastas do diretório atual:  
   ```bash
   ls
   ```
4. Crie uma pasta chamada `atividades`:  
   ```bash
   mkdir atividades
   ```
5. Entre na pasta `atividades`:  
   ```bash
   cd atividades
   ```
6. Volte para o diretório anterior (`/`):  
   ```bash
   cd ..
   ```

**📝 Registre:** Tire um print do terminal após cada comando.  

---

#### 📌 2.2.3. Manipulação de arquivos

**Objetivo:** Criar, copiar, mover e excluir arquivos, trabalhando com diretórios home e subpastas.  

1. Acesse o diretório home do usuário:
   ```bash
   cd ~
   ```
   - Verifique se está no home:  
     ```bash
     pwd
     ```
2. Crie um arquivo `arquivo1.txt` no diretório home:  
   ```bash
   touch arquivo1.txt
   ```
3. Renomeie o arquivo para `documento.txt`:  
   ```bash
   mv arquivo1.txt documento.txt
   ```
4. Acesse a pasta `atividades` (criada na Atividade 1):  
   ```bash
   cd atividades
   ```
5. Dentro de `atividades`, crie um subdiretório chamado `backup`:  
   ```bash
   mkdir backup
   ```
6. Copie `documento.txt` (do home) para `backup`:  
   ```bash
   cp ~/documento.txt backup/
   ```
   - Verifique se o arquivo foi copiado:  
     ```bash
     ls backup/
     ```
7. Volte ao diretório home usando `cd ~`:  
   ```bash
   cd ~
   ```
   - Confirme o local atual:  
     ```bash
     pwd
     ```
8. Exclua o `documento.txt` original (no home):  
   ```bash
   rm documento.txt
   ```
9. Verifique se o arquivo ainda existe em `backup`:  
   ```bash
   ls atividades/backup/
   ```

---

 **Exemplo de Saída Esperada:**  
```bash
[root@fedora ~]# cd ~  
[root@fedora ~]# pwd  
/home/root  
[root@fedora ~]# touch arquivo1.txt  
[root@fedora ~]# mv arquivo1.txt documento.txt  
[root@fedora ~]# cd atividades  
[root@fedora atividades]# mkdir backup  
[root@fedora atividades]# cp ~/documento.txt backup/  
[root@fedora atividades]# cd ~  
[root@fedora ~]# rm documento.txt  
[root@fedora ~]# ls atividades/backup/  
documento.txt  
```

---

- **`cd ~`**: Introduz o conceito de diretório home (importante para organização).  
- **Subdiretório `backup`**: Prática adicional de criação e navegação em subpastas.  
- **Cópia entre diretórios**: Reforça caminhos absolutos (`~/`) e relativos.  

**Dica:** Use `tree` (instale com `dnf install tree`) para visualizar a estrutura de pastas!

#### 📌 2.2.4. Gerenciamento de pacotes

**Objetivo:** Instalar e remover pacotes usando `dnf`.  

1. Atualize a lista de pacotes:  
   ```bash
   dnf update -y
   ```
2. Instale o editor de texto `nano`:  
   ```bash
   dnf install nano -y
   ```
3. Verifique se o `nano` foi instalado:  
   ```bash
   nano --version
   ```
4. Remova o `nano`:  
   ```bash
   dnf remove nano -y
   ```

**📝 Registre:** Mostre prints da instalação e remoção.  

---

#### 📌 2.2.5. Permissões de arquivos
**Objetivo:** Modificar permissões de arquivos.  

1. Crie um arquivo `script.sh`:  
   ```bash
   touch script.sh
   ```
2. Dê permissão de execução ao dono:  
   ```bash
   chmod u+x script.sh
   ```
3. Verifique as permissões:  
   ```bash
   ls -l script.sh
   ```

**📝 Registre:** Mostre o antes e depois das permissões.  

**📝 Dica:** para um pouco mais de informações sobre permissões e o comando `chmod` ver o [tutorial](https://github.com/sistemas-operacionais/2025-1-atividade-02-docker-linux-introducao/blob/main/chmod.md).
---

#### 📌 2.2.6. Processos em execução

**Objetivo:** Monitorar e encerrar processos.  

1. Liste processos em execução:  
   ```bash
   ps aux
   ```
2. Execute um processo em segundo plano (ex: `sleep 60`):  
   ```bash
   sleep 60 &
   ```
3. Encontre o **PID** do processo `sleep`:  
   ```bash
   ps aux | grep sleep
   ```
4. Encerre o processo:  
   ```bash
   kill <PID>
   ```

**📝 Registre:** Mostre prints do `ps` e do `kill`.  

---


#### 📌 2.2.7. Encerrando o contêiner

1. Saia do contêiner:  
   ```bash
   exit
   ```
2. Remova o contêiner após o uso:  
   ```bash
   docker rm fedora-tutorial
   ```

---

### 3. Relatório Final

#### 📌 3.1. Instruções para o relatório
1. Faça um fork desse repositório para a sua conta do github
2. Organize os prints no repositório na pasta `imagens` e descreva o relato no documento `relato.md` no formato [markdown](https://docs.github.com/pt/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax).
3. Inclua seções:  
   - **Cabeçalho**: título da atividade, nome, data
   - **Introdução**: objetivo do exercício
   - **Relato**: descreva as suas atividades e mostre os resultados com as imagens capturadas
   - **Conclusão**: O que aprendeu? Dificuldades?
