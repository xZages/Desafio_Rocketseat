import time

contatos = []

while True:
    print('\n==== AGENDA ====')
    print('1. Adicionar contato')
    print('2. Ver contatos')
    print('3. Editar contato')
    print('4. Favoritar contato')
    print('5. Ver favoritos')
    print('6. Apagar contato')
    print('7. Sair')

    opcao = input('\nEscolha uma opção: ')

    if opcao == '1':

        nome = input('Nome: ')
        telefone = input('Telefone: ')
        email = input('Email: ')

        contato = {
            'nome': nome,
            'telefone': telefone,
            'email': email,
            'favorito': False
        }

        contatos.append(contato)

        print('\nContato adicionado com sucesso!')

    elif opcao =='2':
        
        if len(contatos) == 0:
            print('Nenhum contato encontrado.')

        else:
            for indice, contato in enumerate(contatos):
                favorito = "★" if contato['favorito'] else ''
                print(f'\nID: {indice}')
                print(f'Nome: {contato["nome"]} {favorito}')
                print(f'Telefone: {contato["telefone"]}')
                print(f'Email: {contato["email"]}')
                print('\n----------------')

    elif opcao == '3':

        indice = int(input('Digite o ID do contato que deseja editar: '))
        contatos[indice]["nome"] = input("Novo nome: ")
        contatos[indice]["telefone"] = input("Novo telefone: ")
        contatos[indice]["email"] = input("Novo email: ")

        print('\nContato editado com sucesso!')

    elif opcao =='4':

        indice = int(input('Digite o ID do contato que deseja favoritar: '))
        contatos[indice]['favorito'] = not contatos[indice]['favorito']
        print('\nFavorito atualizado!')

    elif opcao == '5':

        print('\n==== FAVORITOS ====')

        for indice, contato in enumerate(contatos):
            if contato['favorito'] == True:
                print(f'\nID: {indice}')
                print(f'Nome: {contato["nome"]} ★')
                print(f'Telefone: {contato["telefone"]}')
                print(f'Email: {contato["email"]}')

    elif opcao == '6':

        indice = int(input('Digite o ID do contato que deseja apagar: '))
        del contatos[indice]
        print('\nContato apagado com sucesso!')


    elif opcao == '7':

        print('Saindo da agenda...')
        time.sleep(1)
        break
