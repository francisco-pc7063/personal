
#Reinciando
shutdown -r now OU reboot
shutdown
shutdown -h OU halt -> Desliga forcadamente
shutdown now -> desliga no momento
shutdown 1 -> desliga daqui a um minuto

#dpkg -> "gerenciador de pacotes?"
dpkg -l -> lista pacotes instalados


#ls
ls -ltr
ls -1 -> 1 arquivo por linha


#ps -> minha sessao
ps aux -> SAIDA:
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0   9116   308 ?        Ssl  Apr19   0:01 /init


#touch -> testa se arquivo existe ou nao e altera a data de modificacao
touch -f -> test file


#echo -> "print"
echo -n -> nao quebra linha (\n)
echo -e -> permite o uso de tabulacao (backslash escapes \n \a \t"
	\a -> espaco
	\b -> backspace
	\f -> form feed
	\n -> quebra de linha
	\r -> return
	\t -> tab
	\v -> vertical tab
	


#mkdir -> cria diretorio
mkdir -p -> cria toda a arvore de diretorio $ mkdir -p diretorio1/diretorio2


#rm -> remove arquivo
rm -f -> forca a remocao do arquivo (nao aparece error e mensagens de confirmacao)
rm -r -> remove tudo dentro do diretorio


#rmdir -> remove apenas o diretorio (tem que estar vazio)


#sleep 10 -> aguarda 10s esperando


#cat -> le o arquivo carregando ele todo em memoria
cat -b -> numero todas as linhas, menos a em branco
cat -n -> numera todas as linhas, inclusive as em branco
cat -A -> mostra caracteres de tabulacao e especiais

#tac -> cat invertido, da ultima para a primeira linha


#tail -> mostra ultimas linhas do arquivo
tail -n 5 -> ultimas 5 linhas
tail 2 -> ultimas 2 linhas
tail -f -> acompanha novas linhas escritas no arquivo


#head-> mostra primeiras linhas do arquivo
head -n 5 -> primeiras 5 linhas
head 2 -> primeiras 2 linhas
head -c -> pega quantidade especifica de caracteres


#wc -> conta quantidade de bytes, caracteres e linha
	ps aux | wc
	18L;   210 palavras; 1405 caracteres
	18     210    1405
wc -l -> so numero de linhas
wc -w -> so numero de palavras
wc -m -> so numero de caracteres
wc -c -> so numero de bytes
wc -m e wc -c geralmente apresentam o mesmo numero!!!!!!


#sort -> ordena o arquivo
sort -r -> ordena ao contrario
sort -k 2 -> ordena pelo segundo campo
sort -u -> ordena com uniquer

#uniq -> filtra resultados iguais em sequencia
sort | uniq -> melhor utilizacao, ordena e filtra resultados em sequencia
sort -u -> mesma coisa do anterior
sort | uniq -c -> conta o numero de aparicoes


#tr a-z A-Z -> "translate"
tr aei AEI -> troca a->A e->E i->I
tr ' ' '\t' -> troca espaço por tab
tr -d aei -> deleta letras a,e,i
tr -s 'l' -> suprime repeticoes
tr [:lower:] [:upper:] -> transforma todas as lower-case para upper-case


#sed '1,3 d' -> deleta as linha 1 e 3
sed '/Rafael/d' -> remove as linhas que tem ocorrencia de Rafael
sed 's/Paulo/Joao/' -> substitui uma ocorrencia de Paulo por Joao
sed 's/Linux/Unix/g' -> substitui TODAS as ocorrencias de Linux por Unix



#cut -cl-5 -> mostra toda as linha ate o caracter 5 dela
cut -c1,2,3 -> mostra os caracteres 1, 2 e 3 de cada linha
cut -c1-10 -> mostra caracteres de 1 a 10
cut -c5- -> mostra a partir do caracter 5
cut -c1,2,10- -> mostra caracteres 1, 2 e a partir do 10
cut -f1 -> mostra o campo 1
cut -d " " -f1 -> mostra o campo 1, sendo a separacao dos campos o \n " "
cut -d " " -f1,3- -> mostra campo 1 e a partir do 3, sendo a separacao dos campos: \n, " "


#diff "arquivo1" "arquivo2" -> compara o conteudo dos arquivos
3c3
< Ricardo
---
> Ricardo Prudenciato
7c7
< Maria$
...
> Maria $ #visivel com cat -A
9d8 #d= possui em um arquivo, mas nao possui no outro
< Maria

xax -> diferenca no arquivo <
xby -> diferenca entre os dois arquivos
xcx -> diferenca no arquivo >

diff -w -> ignora diferenca de espacos em branco
diff -r -> compara com diretorios


#grep "string" "arquivo" -> retorna a linha que aparece "string"
grep -i -> remove o case sensitive
grep -c -> conta quantas ocorrencias
grep -v -> exclui o que apareceu
grep -r -> procura recursivamente em todos os diretorios e nos arquivos
grep -l -> lista o arquivo que encontrou a string
grep -A3 Carlos -> mostra as 3 linhas depois da ocorrencia tambem
grep -B3 Carlos -> mostra as 3 linhas ANTES da occorrencia tambem

fgrep -> strings simples (MAIS LEVE)

egrep -> expressoes regulares (MAIS PESADO)


#whatis -> descricao do comando


#more -> divide em paginas


#less -> mostra uma parte do arquivo
	n -> proxima ocorrencia
	N -> ocorrencia anterior


#find "path" -> procura arquivos
find -name "string" -> procura pelo nome "string"
find -user "string" -> procura arquivos do usuario "string"
find ./ -exec ls {} +


#date -> retorna a data do sitema
"dia da semana" "mes" "dia dos mes" "hora:min:s" "???" "ano"
date +%H -> retorna hora
date +%M -> retorna minuto
date +%m -> retorna mes
date +%D -> retorna data (01/01/2001)
date +%d/%m -> retorna data/mes (01/01)

#cal -> CALENDARIO

#seq -> retorna sequencia de numeros
seq 5 -> retorna 1 2 3 4 5
sec 5 7 -> retorna 5 6 7
sec 3 3 9 -> retorna 3 6 9


#expr -> faz contas
expr 5 - 2 -> 2 (apenas inteiros
expr 5 \* 2 -> 10


#bc -> faz contas
echo 3+2 | bc -> 5
echo 3 + 2 | bc -> 5
echo "(3 + 2)\* 5" -> 25


#Sequencia de comandos
cat alunos.txt | wc -l

date ; echo Linux ; ls
-> qui ago 16:38:38 -03 2017
Linux
alunos2.txt alunos3.txt alunos.txt

ls alunos.txt || echo Linux
-> alunos.txt
ls alunos.txt2 || echo Linux
-> ls : cannot acess 'alunos.txt2': No such file or directory
Linux

ls alunos.txt && echo Linux
-> alunos.txt
Linux

ls alunos.txt2 && echo Linux
-> ls : cannot acess 'alunos.txt2': No such file or directory

~$ ( cd .. ; ls -l )
drwxr-xr-x 1 fpc-deb fpc-deb 512 Apr 21 17:57 fpc-deb
~$




#REDIRECIONAMENTO DE ENTRADA E SAIDA

SAIDA DE ERRO
ls -l alunos.txt3 2> log.out
ls -l alunos.txt3 2>> log.out

SAIDA NORMAL
ls -l alunos.txt 1> log.out #E A MESMA COISA Q >

TRATANDO SAIDAS
ls -l alunos.txt3 >> log.out 2>> log-erro.out #saida em arquivos diferentes
ls -l alunos.txt >> log.out 2>&1

SAIDA NULA
ls -l alunos.txt 2> /dev/null


tr 'a' 'Z' < alunos.txt



#VARIAVEIS DE AMBIENTE
env | less -> 


set | less -> 



#VARIAVEIS RESERVADAS
$0-9
$[@]
$#
$HOME
$PATH
$USER

####


echo $HOME -> variavel do home do usuario atual
VARIAVEL1=Valor
VARIAVEL2="Curso de Shell Script"
echo $VARIAVEL1 -> $Valor
echo $$ -> pid do BASH atual


export VARIAVEL1 -> permite a visualizacao da variavel em processos filhos
export VARIAVEL2=batata -> atribui e exporta

.bashrc .profile -> ARQUIVOS DE INICIALIZACAO



echo \* -> "\" protege o proximo caracter de ser interpretado pelo shell
$ *

"" -> $ `` / NAO PROTEGE
'' -> $ `` / PROTEGE
`` -> executa comando e retorna stdout como texto
$() -> mesma coisa que aspas









VIM
Ctrl + B -> sobe uma pagina
Ctrl + F -> desce uma pagina
/ -> procura de cima pra baixo
? -> procura de baixo pra cima
n -> proximo
N -> anterior
dd -> recorta linha
y -> copia
p -> cola
v -> visual
h -> move para esquerda
l -> move para direita
j -> move para cima
k -> move para baixo 
q -> sai
q! -> sai sem salvar
x -> salva e sai
w -> salva
wq -> salva e sai

:set number







File Globbing
* -> tudo
[12345], [1-5] -> qualquer um que faça parte da lista
[Ll]inux -> linux ou Linux
{aula,AULA} -> qualquer um com algum dos dois
? -> qualquer caractere






REGEX
^Linux -> toda linha que comeca com: Linux
Linux$ -> toda linha que termina com: Linux
^$ -> toda linha que tem "vazio"
ba* -> qualquer linha que tenha a nenhuma, uma ou varias vezes
b+ -> qualquer linha que tenha b uma ou mais vezes
b? -> qualquer linha que tenha b uma ou apenas uma vez
a.b -> qualquer coisa entre a e b
a.*b -> exista qualquer coisa OU NAO entre a e b
\. -> "\" protege o caractere especial (expressa "." no caso)





BASH
. *.sh -> executa no bash atual
source *.sh -> executa no bash atual
./*.sh -> abre um subshell
bash *.sh -> executa no subshell com o shell especificado
DATAHORA=$(date +%H:%M) -> executa o comando em um subshell

VARIAVEL DE AMBIENTE
NOME -> procura a variavel de ambiente
PATH="$PATH:/PATH/TO/SCRIPT"


PADRAO DE INICIO DE SCRIPT
##########################################
#
# DESCRICAO DO SCRIPT
#
# Autor: Nome do autor (email_de_contato@email.com)
# Data de criacao: DD/MM/YYYY
#
# Descriao: o que o script faz
#
# Exemplo de uso: ./script.sh parametro1 parametro...
#
# Alteracoes:
#	Dia X - Inclusao da funcao de ordenacao
#	Dia Y - Correcao da funcao de leitura
#
#######################################################


EXIT CODE
0 - 255
0 -> sucesso
1 - 255 -> ERROR
$? -> retorna exit code do ultimo comando









read -> le uma entrada do usuario
read VAR ; echo $VAR -> Adicionar a $VAR o valor stdin
read -p -> sem newline
read -s -> le entrada sem mostra-la na tela
read "Texto> " -> printa texto antes da entrada
read -p "Isso vai alterar o escape de ENTER para SPACE" '-d '
read -s -p 'Para utilizar o SAFE: '















#CONDICIONAIS

#######test
test
-eq -> equal
-nq -> not equal
-gt -> greater then
-ge -> greater then or equal
-lt -> less then
-le -> less then or equal
test -f -> try file existence
test "$V1" = "$V2" -> string of both variables are equal?
[] = test
[ -f /tmp/test ] -> test -f /tmp/test
[ 50 -gt 100 ] -> test 50 -gt 100

&& -> e (executa o segundo ao executar corretamente o primeiro)
|| -> ou (executa o segundo ao falhar o primeiro)
! -> negacao


########if
 
if
then
	echo "Opcao 1"
elif
	echo "Opcao 2"
else
	echo "Opcao de Excessao"
fi


#####
if grep "fpc-ubut" /etc/passwd > /dev/null
then
	echo "Usuario existe"
else
	echo "Usuario nao existe"
fi

########case 

case $VAR in
[0-9])
	echo "DO 1"
;;

[a-z])
	echo "DO 2"
;;

[A-Z])
	echo "DO 3"

*)
	echo "DO 4"
;;

esac





################## LOOPS



for number in 1 2 3 4 5
do
	echo "$NUMBER"
done

###
for FILE in files*
do
	echo "$FILE"
done

### $(seq 1 5 50) - 1 a 50 em intervalos de 5
for NUM in $(seq 5 10)
do
	echo "$NUM"
done

###{1..50..5}
for NUM in {5..0}
do
	echo "$NUM"
done

###
for LINE in $(cat arquivo)
do
	echo "$LINE"
done

###
for (( i=5; i <= 20; i++))
do
	echo "$i"
done


#### while

while <condicao>
do
	echo "Executando!!!"
done

###
while [ $(ps aux | wc -l) -lt 300 ]
do
	echo "Tudo OK"
	sleep 30
done

###
while ls /var/lock/process.lock > /dev/null
do
	echo "Processo em execucao"
	sleep 30
done

###
x=1
while [ $x -le 20 ]
do
	echo "O valor de x: $x"
	x=$(expr $x + 1)
done

###### until

until <condicao>
do
	comando 1
	comando 2
done

###
x=1
until [ $x -eq 20 ]
do
	echo "O valor atual e $x"
	x=$( $x + 1 )
done

###
until ls /var/lock/processo.lock > /dev/null
do
	echo "Aguardando processo"
	sleep 30
done


#### break
while ls /var/lock/process.lock > /dev/null
do
	if [ $(date +%H) -gt 18 ]
	then
		break
	fi
	echo "Processo em execucao"
	sleep 30
done

#### continue
while ls /var/lock/process.lock > /dev/null
do
	if [ $(date +%H) -gt 18 ]
	then
		continue
	fi
	echo "Processo em execucao
	sleep 30
done



########## FUNCTIONS

func () {
	VAR1='OI'
	local VAR2='TCHAU'
}
func
echo "$VAR1"
echo "$VAR2" -> vai dar erro



########## LOGGING

./script.sh >> log.out 2>&1 log.out
./script.sh >> log.out 2>> log_error.out
./script.sh &> log.out
./script.sh | tee -a log.out

<script.sh>
exec &> log.out
OU
exec 1>> log.out
exec 2>> log.out
OU
##PROCESS SUBSTITUTION
exec 1>> >(tee -a "$LOG")


logger -p service_defined_in_syslog.criticity "Mensagem"
logger -p service.criticity -t [Minha tag] "Mensagem"
echo "Mensagem" | logger -p service.criticity -t [Minha tag]



############## MAIL ou MUTT ou SENDEMAIL
apt install bsd-mailx
# Usa um postfix

#Encaminha o log.out
mail -s "Assunto" meusuario@dominio.com.br < log.out

#Le o email
mail
1


# mutt permite enviar mensagens a partir de servidores de email externo
# sendemail permite tambem


############# DEBUGGING
bash -n myscript.sh parametro1
bash -x -> mostra os comandos executados
ou
#!/bin/bash
+ -> executa um comando
++ -> executa um novo shell para o comando

bash -v -> comando + resultado de execucao
bash -xv -> comando/bash + resultado de execucao

set -xv -> entra em modo debug
set +xv -> sai do modo debug



############ TRAP
trap read DEBUG
trap "" DEBUG -> execucao linha a linha









#REDES
netstat -nat | awk '{print $6}' | sort | uniq -c | sort -n
