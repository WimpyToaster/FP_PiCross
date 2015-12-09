# Grupo 18:
# Antonio Terra - 84702
# Miguel Viegas - 84747

                   #-------------------------#
                   #         Imports         #
                   #-------------------------#

import operator
import functools
import ast

                  #--------------------------#
                  #  Funcoes TAD auxiliares  #
                  #--------------------------#


def lenmax(t):
    '''Funcao lenmax: tuple/lista -> inteiro
       Recebe um argumento do tipo tuple, com dois tuples ou listas dentro deste.
       Devolve um inteiro correspondente ao comprimento maior dos seus tuples ou listas interiores'''
    
    lenmax = len(t[0])
    for i in range(len(t)):
        if lenmax < len(t[i]):
            lenmax=len(t[i])
    return lenmax

def acrescenta_tuple_colunas(t, n):
    '''Funcao acrescenta_tuple_colunas: tuple x inteiro -> tuple
       Recebe um argumento 't' do tipo tuple e um argumento 'n' do tipo inteiro.
       Devolve um tuple com os seus tuples interiores com o comprimento n (acrescentando zeros)'''
    
    s=()
    for i in range(len(t)):
        l=t[i]
        while len(l)<n:
            l=(0,)+l
        s+=(l,)
    return s

def acrescenta_tuple_linhas(t, n):
    '''Funcao acrescenta_tuple_colunas: tuple x inteiro -> tuple
       Recebe um argumento 't' do tipo tuple e um argumento 'n' do tipo inteiro.
       Devolve um tuple com os seus tuples interiores com o comprimento n (acrescentando zeros)''' 
    
    s=()
    for i in range(len(t)):
        l=t[i]
        while len(l)<n:
            l=l+(0,)
        s+=(l,)
    return s

def soma_tuple(x):
    '''Funcao soma_tuple: tuple -> inteiro
       Recebe um argumento do tipo tuple (constituido por inteiros)
       Devolve um inteiro referente a soma dos elementos do tuple'''
    
    res=0
    for i in range(len(x)):
        res += x[i]
    return res

def divisao_lista(x):
    '''Funcao divisao_lista: lista -> lista de listas
       Recebe um argumento do tipo lista, em que se separam as sequencias de '2'.
       Devolve uma lista de listas em que cada uma das listas interiores sao constituidas pelo valor 2'''
    
    if not isinstance(x, list):
        raise ValueError('divisao_lista: argumento invalido')
    l=[]
    nova_lista=[]
    for i in range(len(x)):
        if x[i] == 2:
            nova_lista.append(2)
            if i == (len(x)-1):
                l.append(nova_lista)
        elif x[i] == 1:
            if nova_lista==[]:
                nova_lista=[]
            else:
                l.append(nova_lista)
                nova_lista = []
    return l


def lista_linhas(t):
    '''Funcao lista_linhas: lista -> lista
       Recebe um argumento do tipo lista, que representa a matriz do tabuleiro e cria listas com os valores de cada linha.
       Devolve uma lista de listas, em que cada lista interior corresponde aos valores das linhas do tabuleiro'''
    
    l=[]
    lista_nova=[]
    for i in range(0, tabuleiro_dimensoes(t)[0]):
            for j in range(0, tabuleiro_dimensoes(t)[1]):
                lista_nova.append(t[1][j][i])
            l.append(lista_nova)
            lista_nova=[]
    return l

                 #---------------------------#
                 #  Funcoes TAD coordenadas  #
                 #---------------------------#

def e_coordenada(uni):      # Reconhecedor
    '''Funcao e_coordenada: universal -> logico
       Recebe um unico argumento.
       Devolve True caso esse argumento seja do tipo coordenada e False 
       em caso contrario'''   
    
    if (isinstance(uni,tuple) and len(uni) == 2):
        if (isinstance(uni[0],int) and isinstance(uni[1],int)):
            if (uni[0] > 0 and uni[1] > 0):
                return True
    return False



def cria_coordenada(l,c):      # Construtor
    '''Funcao cria_coordenada: inteiro x inteiro -> coordenada
       Recebe 2 argumentos.
       Devolve um tuplo com 2 de comprimento contendo os inteiros fornecidos.'''   
    
    if not (isinstance(l,int) and isinstance(c,int) and l*c > 0 ):
        raise ValueError('cria_coordenada: argumentos invalidos')
    return (l,c)



def coordenada_linha(coor):     # Seletor
    '''Funcao coordenada_linha: coordenada -> inteiro
       Recebe um unico argumento do tipo coordenada.
       Devolve um inteiro, correspondente a primeira entrada da coordenada''' 
    
    if not e_coordenada(coor):
        raise ValueError('coordenada_linha: argumentos invalidos')
    return coor[0]



def coordenada_coluna(coor):    # Seletor
    '''Funcao coordenada_coluna: coordenada -> inteiro
       Recebe um unico argumento do tipo coordenada.
       Devolve um inteiro, correspondente a segunda entrada da coordenada'''
    
    if not e_coordenada(coor):
        raise ValueError('coordenada_coluna: argumentos invalidos')
    return coor[1]



def coordenadas_iguais(coor1,coor2):      # Teste
    '''Funcao coordenadas_iguais: coordenada x coordenada -> logico
       Recebe dois argumentos do tipo coordenada.
       Devolve o valor logico de True se as coordenadas forem iguais e False caso contrario.'''
    
    if not (e_coordenada(coor1) and e_coordenada(coor2)):
        raise ValueError('coordenadas_iguais: argumentos invalidos')
    return ((coor1[0] == coor2[0]) and (coor1[1] == coor2[1]))




def coordenada_para_cadeia(coor):
    '''Funcao coordenada para cadeia: coordenada -> cadeia de caracteres
       Recebe um unico argumento do tipo coordenada.
       Devolve a cadeia de caracteres da forma '(x : y)' '''
    
    if not e_coordenada(coor):
        raise ValueError('coordenada_para_string: argumentos invalidos')
    return ('(' + str(coordenada_linha(coor)) + ' : ' + str(coordenada_coluna(coor)) + ')')


                 #-------------------------#
                 #  Funcoes TAD tabuleiro  #
                 #-------------------------#
                 
                 
def e_tabuleiro (t):           # Reconhecedor
    '''Funcao e_tabuleiro: universal -> logico
       Recebe um unico argumento.
       Devolve True caso esse argumento seja do tipo tabuleiro e False 
       em caso contrario'''
    
    if len(t)==3:
        if isinstance (t, list):
            if isinstance (t[0], tuple) and isinstance (t[1], list) and isinstance (t[2], tuple):
                if len(t[0])==len(t[2]):
                    if all(isinstance(x, list) for x in t[1][:]):
                        if all(isinstance(x, int) and (0<=x<=2) for x in functools.reduce(operator.add, t[1])):
                            return True
                    
    return False
    
def cria_tabuleiro (t):         # Construtor
    '''Funcao cria_tabuleiro: tuple -> tabuleiro
       Recebe um argumento do tipo tuple, constituido por dois tuples, o primeiro com as especificacoes das linhas do tabuleiro e o segundo com as especificacoes das colunas do tabuleiro.
       Devolve tabuleiro de acordo com a representacao interna escolhida'''
    
    if not (isinstance  (t, tuple) and isinstance (t[:], tuple) and len(t)==2 and len(t[0])==len(t[1])):
        raise ValueError('cria_tabuleiro: argumentos invalidos')  
    
    linhas = t[0]
    colunas = t[1]
    matriz = []
    
    for k in range(len(linhas)):
        matriz.append([0]*len(linhas))
    
    return [colunas, matriz, linhas]

def tabuleiro_dimensoes (t):
    '''Funcao tabuleiro_dimensoes: tabuleiro -> tuple 
       Recebe um argumento do tipo tabuleiro, de acordo com a representacao interna escolhida.
       Devolve um tuple, com dois elementos do tipo inteiro, sendo um o numero de linhas e outro o numero de colunas, respetivamente''' 
    
    if not e_tabuleiro(t):
        raise ValueError('tabuleiro_dimensoes: argumento invalido')
    return (len(t[-1]), len(t[0]))

def tabuleiro_especificacoes (t):
    '''Funcao tabuleiro_especificacoes: tabuleiro -> tuple
       Recebe um argumento do tipo tabuleiro, de acordo com a representacao interna escolhida.
       Devolve um tuple, com dois elementos do tipo tuple, sendo um as especificacoes das linhas e o outro as especificacoes das colunas, respetivamente'''
    
    if not e_tabuleiro(t):                      
            raise ValueError('tabuleiro_dimensoes: argumento invalido')    
    return (t[-1], t[0])
    
def tabuleiro_celula (t, c):               # 
    '''Funcao tabuleiro_celula: tabuleiro x coordenada -> {0, 1, 2}
       Recebe como argumento um elemento 't' do tipo tabuleiro, um elemento 'c' do tipo coordenada e verifica qual o valor no tabuleiro na posicao da coordenada c
       Devolve um inteiro (entre 0 e 2) sendo este o valor na posicao 'c' no tabuleiro 't' '''
    
    if not (e_coordenada(c) and e_tabuleiro(t) and coordenada_linha(c)<= tabuleiro_dimensoes(t)[0] and coordenada_coluna(c)<= tabuleiro_dimensoes(t)[1]):
        raise ValueError('tabuleiro_celula: argumentos invalidos')
    return t[1][coordenada_coluna(c)-1][coordenada_linha(c)-1]

def tabuleiro_preenche_celula (t, c, e):         # Modificador
    '''Funcao tabuleiro_preenche_celula: tabuleiro x coordenada x {0, 1, 2} -> tabuleiro
       Recebe um argumento 't' do tipo tabuleiro, um argumento 'c' do tipo coordenada e um argumento 'e' do tipo inteiro, o tabuleiro 't' e modificado na coordenada 'c' pelo inteiro 'e' 
       Devolve um tabuleiro ja modificado'''
    
    if not (e_coordenada(c) and e_tabuleiro(t) and isinstance(e, int) and e <=2 and e >=0  and coordenada_linha(c)<= tabuleiro_dimensoes(t)[0] and coordenada_coluna(c)<= tabuleiro_dimensoes(t)[1]):
        raise ValueError('tabuleiro_preenche_celula: argumentos invalidos')
    t[1][(coordenada_coluna(c)-1)][(coordenada_linha(c)-1)]=e
    return t


def tabuleiros_iguais (t1, t2):       # Teste
    '''Funcao tabuleiros_iguais: tabuleiro x tabuleiro -> logico
       Recebe dois argumentos do tipo tabuleiro
       Devolve o valor logico, se os tabuleiros forem iguais devolve True, caso contrario devolve False'''
    if not (e_tabuleiro(t1) and e_tabuleiro(t2)):
        raise ValueError('tabuleiros_iguais: argumentos invalidos')
    
    if t1==t2:
        return True
    else:
        return False
    
    
def escreve_tabuleiro (t):        # Transformador de saida
    '''Funcao escreve_tabuleiro: tabuleiro -> {}
       Recebe um argumento 't' do tipo tabuleiro e representa-o graficamente.
       Devolve a representacao grafica do tabuleiro'''
    
    if not e_tabuleiro(t):
        raise ValueError('escreve_tabuleiro: argumento invalido')
    
    colunas = acrescenta_tuple_colunas(tabuleiro_especificacoes(t)[1], lenmax(tabuleiro_especificacoes(t)[1]))
    linhas = acrescenta_tuple_linhas(tabuleiro_especificacoes(t)[0], lenmax(tabuleiro_especificacoes(t)[0]))
    
    for i in range(len(colunas[0])):                     #Escreve as especificacoes das colunas com os espacamentos corretos
        for j in range(len(colunas)):
            r = colunas[j][i]
            if r==0:
                print(' ', end='    ')
            else:
                print('  %d' %r, sep='', end='  ')
        print('  ')
      
    for i in range(1,(tabuleiro_dimensoes(t)[0])+1):         #Escreve cada linha com a respetiva especificacao 
        for j in range(1, (tabuleiro_dimensoes(t)[1])+1):
            c = cria_coordenada(i,j)
            
            if tabuleiro_celula(t, c) == 0:
                print('[ %c ]' % '?' , sep='', end='')
            elif tabuleiro_celula(t, c)==1:
                print('[ %c ]' % '.' , sep='', end='')
            else:
                print('[ %c ]' % 'x' , sep='', end='')
                
        for k in range(len(linhas[0])):
            linha=linhas[(coordenada_linha(c))-1][k]
            if linha==0:
                print('  ', end='')
            else:
                print(' %d' % linha, end='')
        print('|')
    print('')
        

        
        
def tabuleiro_completo (t):       # Reconhecedor
    '''Funcao tabuleiro_completo: tabuleiro -> logico
       Recebe um argumento 't' do tipo tabuleiro.
       Devolve True se o tabuleiro estiver completo corretamente conforme as especificacoes, e False em caso contrario'''
    
    if not e_tabuleiro(t):
        raise ValueError('tabuleiro_completo: argumento invalido')
    
    linhas = lista_linhas(t)
    
    if not all((x!=0) for x in functools.reduce(operator.add, t[1])):   #Aglumera todas as listas da matriz do tabuleiro numa so lista e confima se existe algum valor 0
        return False
    else:
        for i in range(0, tabuleiro_dimensoes(t)[1]):             #Confirma se as colunas estao conforme as especificacoes das colunas
            if soma_tuple(t[0][i]) != t[1][i].count(2):
                return False
            for j in range(len(t[0][i])):
                l = divisao_lista(t[1][i])
                if t[0][i][j] != len(l[j]):
                    return False
        for k in range(0, tabuleiro_dimensoes(t)[0]):             #Confirma se as linhas estao conforme as especificacoes das linhas
            if soma_tuple(t[2][k]) != linhas[k].count(2):
                return False
            for w in range(len(t[2][k])):
                l = divisao_lista(linhas[k])
                if t[2][k][w] != len(l[w]):
                    return False
    return True


                    #---------------------------#
                    #    Funcoes TAD jogadas    #
                    #---------------------------#


def cria_jogada(coor,n):
    '''Funcao cria_jogada: coordenada x {1,2} -> jogada
       Recebe dois argumentos, um do tipo coordenada e outro pertencente ao conjunto {1,2}
       Devolve um elemento do tipo jogada com a coordenada e o valor da jogada fornecida.'''
    if not e_jogada(((coor),n)):
        raise ValueError('cria_jogada: argumentos invalidos')
    return (coor,n)


def e_jogada(uni):
    '''Funcao e_jogada: universal -> logico
       Recebe um argumento de qualquer tipo.
       Devolve o valor logico True se o universal for do tipo 'jogada'. '''
    
    if (isinstance(uni,tuple) and len(uni) == 2):
        if (e_coordenada(uni[0]) and (uni[1] == 1 or uni[1] == 2)):
            return True
    return False


def jogada_coordenada(jog):
    '''Funcao jogada_coordenada: jogada -> coordenada
       Recebe um argumento do tipo jogada
       Devolve a coordenada da jogada.'''
    
    if not e_jogada(jog):
        raise ValueError('jogada_coordenada: argumentos invalidos')
    return jog[0]


def jogada_valor(jog):
    '''Funcao jogada_coordenada: jogada -> {1,2}
       Recebe um unico argumento do tipo jogada
       Devolve o valor da jogada (1 ou 2).'''
    
    if not e_jogada(jog):
        raise ValueError('jogada_valor: argumentos invalidos')
    return jog[1]


def jogadas_iguais(jog1,jog2):
    '''Funcao jogadas_iguais: jogada x jogada -> logico
       Recebe dois argumentos do tipo jogada
       Devolve o valor logico True se as jogadas forem iguais e False caso contrario'''
    
    if not (e_jogada(jog1) and e_jogada(jog2)):
        raise ValueError('jogadas_iguais: argumentos invalidos')
    if (coordenadas_iguais(jogada_coordenada(jog1),jogada_coordenada(jog2)) and (jogada_valor(jog1) == jogada_valor(jog2))):
        return True
    return False

def jogada_para_cadeia(jog):
    '''Funcao jogada_para_cadeia: jogada -> cadeia
       Recebe um unico argumento do tipo jogada
       Devolve uma cadeia do tipo '(x : y) --> z'. '''
    if not (e_jogada(jog)):
        raise ValueError('jogada_para_cadeia: argumentos invalidos')
    return (str(coordenada_para_cadeia(jogada_coordenada(jog))) + ' --> ' + str(jogada_valor(jog)))



                        #--------------------------#
                        #    Funcoes Adicionais    #
                        #--------------------------#
                        
                        

def le_tabuleiro(fich):
    '''Funcao le_tabuleiro: ficheiro -> especificacao
       Recebe um unico argumento do tipo string que corresponde ao nome do 
           ficheiro que contem as especificacoes do tabuleiro
       Devolve um tuplo do tipo especificacao do tabuleiro'''
    
    f = open(fich,'r')
    l = f.readline()
    f.close()
    return ast.literal_eval(l)


def pede_jogada(tab):
    '''Funcao pede_jogada: tabuleiro -> jogada
       Recebe um unico argumento do tipo tabuleiro
       Devolve um tuplo do tipo jogada.'''
    
    if not (e_tabuleiro(tab)):
        raise ValueError('pede_jogada: argumentos invalidos')
    
    dim = tabuleiro_dimensoes(tab)[0]
    c = input('Introduza a jogada\n' + '- coordenada entre (1 : 1) e '\
        + coordenada_para_cadeia(cria_coordenada(dim,dim)) + ' >> ')
    
    a = str(c)                      #Copia do input da "coordenada"

    c = str(c[1:-1])                #Recebe a string no formato do retorno do
    coor1 = c.split(':')[0]         #   coordenada_para_cadeia e obtem os dois
    coor2 = c.split(':')[1]         #   inteiros introduzidos.
    v = input('- valor >> ')

    if (v.isdigit):
        v = int(v)
    
    if coor1.isdigit:
        coor1 = int(coor1)
        if coor2.isdigit:
            coor2 = int(coor2)
            if not (coordenada_para_cadeia(cria_coordenada(coor1,coor2))) == a:  
                return False                    
        else:    
            return False        
    else:    
        return False


    if ((coor1 <= dim) and (coor2 <= dim)):
        return cria_jogada(cria_coordenada(coor1,coor2),v)
    return False


def jogo_picross(fich):
    '''Funcao jogo_picross: string -> logico
       Recebe um argumento do tipo string, sendo este o nome do ficheiro que contem as especificacoes do tabuleiro a jogar.
       Devolve True caso o tabuleiro esteja completo (conforme as especificacoes), e False em caso contrario'''
    
    print('JOGO PICROSS')
    f = le_tabuleiro(fich)
    t = cria_tabuleiro(f)
    
    def matriz(t):              #Cria uma lista com todos os valores das entradas do tabuleiro
        '''Funcao matriz: tuple -> lista
           Recebe um argumento do tipo tuple que representa o tabuleiro
           Devolve uma lista com as celulas do tabuleiro'''
        l=[]
        for i in range(1,(tabuleiro_dimensoes(t)[0])+1):
            for j in range(1, (tabuleiro_dimensoes(t)[1])+1):
                c = cria_coordenada(i,j)
                l.append(tabuleiro_celula(t, c))
        return l    
        
    
    while not (all((x != 0) for x in matriz(t))):    #testa se existe algum 0 nos valores das celulas do tabuleiro
        
        escreve_tabuleiro(t)
        j = pede_jogada(t)
          
        while j == False:
            print('Jogada invalida.')
            j=pede_jogada(t)
            
        c = jogada_coordenada(j)
        v = jogada_valor(j)
        tabuleiro_preenche_celula(t, c, v)
    
    escreve_tabuleiro(t)    
    if tabuleiro_completo(t) == True:
        print('JOGO: Parabens, encontrou a solucao!')
        return True
    else:
        print('JOGO: O tabuleiro nao esta correto!')
        return False
