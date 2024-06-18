from time import sleep
import requests

#cores ->
null = "\033[m"
amarelo = "\033[33m"
azul = "\033[34m"
vermelho = "\033[31m"
roxo = "\033[35m"
#========

seus_dirrtorios = []

tipo_arquivo = []
with open("arquivo.txt", "r") as arquivo:
    for linha in arquivo:
        linha = linha.strip("\n")
        tipo_arquivo.append(linha)

diretorios = []
with open("caminhos.txt", "r") as caminhos:
    for linha in caminhos:
        linha = linha.strip("\n")
        diretorios.append(linha)

on_off = False
while not on_off:
    try:
        escolha = int(input("""
[01] YOUR LIST
[02] AUTOMATIC LIST
|
\______[ """))
        #MODO AUTOMATICO (world list do script)
        if escolha == 2:
            try:
                url = str(input(f"\nURL [ Ex.: http://exemplo.com/ ] : "))
            except:
                print("\nerror")

            for dir in diretorios:
                sleep(1)
                resposta = requests.get(f"{url}{dir}")
                status = resposta.status_code
                if status == 404:
                    print(f"\n{vermelho}acess refused /{dir} 404{null}")
                elif status == 403:
                    print(f"\n{amarelo}permission danied {dir}{null}")
                elif status == 200 or status == 201:
                    print(f"\n{azul}success {url}{dir}{null}")
                elif status == 301 or status == 300:
                    print(f"\n{amarelo}redirected {url}{dir}{null}")
                else:
                    print(f"{roxo}status.code[ {status} ] {url}{dir}{null}")
            for file in tipo_arquivo:
                sleep(1)
                resposta = requests.get(f"{url}{dir}{file}")
                status = resposta.status_code
                if status == 404: pass
                elif status == 403:
                    print(f"\n{amarelo}permission danied {dir}{file}{null}")
                elif status == 200 or status == 201:
                    print(f"\n{azul}success {url}{dir}{file}{null}")
                elif status == 301 or status == 300:
                    print(f"\n{amarelo}redirected {url}{dir}{file}{null}")
                else:
                    print(f"{roxo}status.code[ {status} ] {url}{dir}{file}{null}")
        elif escolha == 1:
            # SUA WORLD LIST
            try:
                meu_arquivo = str(input("\nfile name: "))
                url = str(input(f"\nURL [ Ex.: http://example.com/ ] : "))
            except:
                print("\nerror")
            #try:
                with open(meu_arquivo, "r") as caminhos:
                    for linha in caminhos:
                        linha = linha.strip("\n")
                        seus_diretorios.append(linha)
            #except:
            #    print("\nerror opening file")

            for dir in meus_diretorios:
                resposta = requests.get(f"{url}{dir}")
                status = resposta.status_code
                if status == 404:
                    print(f"\n{vermelho}acess refused /{dir} 404{null}")
                elif status == 403:
                    print(f"\n{amarelo}permission danied {dir}{null}")
                elif status == 200 or status == 201:
                    print(f"\n{azul}success {url}{dir}{null}")
                elif status == 301 or status == 300:
                    print(f"\n{amarelo}redirected {url}{dir}{null}")
                else:
                    print(f"{roxo}status.code[ {status} ] {url}{dir}{null}")

            for file in tipo_arquivo:
                resposta = requests.get(f"{url}{dir}{file}")
                status = resposta.status_code
                if status == 404: pass
                elif status == 403:
                    print(f"\n{amarelo}permission danied {dir}{file}{null}")
                elif status == 200 or status == 201:
                    print(f"\n{azul}success {url}{dir}{file}{null}")
                elif status == 301 or status == 300:
                    print(f"\n{amarelo}redirected {url}{dir}{file}{null}")
                else:
                    print(f"{roxo}status.code[ {status} ] {url}{dir}{file}{null}")
        else:
            pass
    except:
        print("\nERROR. TRY AGAIN.\n")
