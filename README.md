# README import os
import sys
 
linha1 =  [' ',' ',' ']
linha2 =  [' ',' ',' ']
linha3 =  [' ',' ',' ']
 
print('JOGO DA VELHA')
 
def tabuleiro():
    print(f' {linha1[0]} | {linha1[1]} | {linha1[2]} ')
    print(f'___|___|___')
    print(f' {linha2[0]} | {linha2[1]} | {linha2[2]} ')
    print(f'___|___|___')
    print(f' {linha3[0]} | {linha3[1]} | {linha3[2]} ')
    print(f'   |   |   ')
 
jogador = 'O'
jogadas = 0
 
def vitoria():
    os.system('cls')
    tabuleiro()
    print(f"Vitoria do: {jogador}")
    sys.exit()
 
def conferirVitoria():
        #Conferindo Vitoria Por Linhas
        if linha1[0] == jogador and linha1[1] == jogador and linha1[2] == jogador or linha2[0] == jogador and linha2[1] == jogador and linha2[2] == jogador or linha3[0] == jogador and linha3[1] == jogador and linha3[2] == jogador:
            vitoria()
        #Conferindo Vitoria Por Colunas
        elif linha1[0] == jogador and linha2[0] == jogador and linha3[0] == jogador or linha1[1] == jogador and linha2[1] == jogador and linha3[1] == jogador or linha1[2] == jogador and linha2[2] == jogador and linha3[2] == jogador:
            vitoria()
        #Conferindo Diagonais
        elif linha1[0] == jogador and linha2[1] == jogador and linha3[2] == jogador or linha3[0] == jogador and linha2[1] == jogador and linha1[2] == jogador:
            vitoria()
        elif jogadas >= 8:
          os.system('cls')
          tabuleiro()
          print('empate')
          sys.exit()
 
while True:
        tabuleiro()
        print(f"Vez do jogador: {jogador}")
 
        coluna = input("Coluna: ")
        linha = input("Linha: ")
 
        if coluna.isdigit() and linha.isdigit():
            if int(coluna) > 0 and int(coluna) < 4 and int(linha) > 0 and int(linha) < 4:
                match linha:
                    case '1':
                        if linha1[int(coluna) - 1] == ' ':
                            linha1[int(coluna) - 1] = jogador
                            conferirVitoria()
                            if jogadas%2 == 0:
                                jogador = 'X'
                            else:
                                jogador = 'O'
                            jogadas += 1
                        else:
                            print("Posição Inválida")
 
                    case '2':
                        if linha2[int(coluna) - 1] == ' ':
                            linha2[int(coluna) - 1] = jogador
                            conferirVitoria()
                                                 
                            if jogadas%2 == 0:
                                jogador = 'X'
                            else:
                                jogador = 'O'
                            jogadas += 1
                        else:
                            print('Posição Inválida')
 
                    case '3':
                        if linha3[int(coluna) - 1] == ' ':
                            linha3[int(coluna) - 1] = jogador
                            conferirVitoria()
                            if jogadas%2 == 0:
                                jogador = 'X'
                            else:
                                jogador = 'O'
                            jogadas += 1
                        else:
                            print('Posição Inválida')          
           
            else:
                print("Jogada Inválida")
        else:
            print("Jogada Inválida")
