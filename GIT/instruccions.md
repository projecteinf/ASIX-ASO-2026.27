# Windows

## Generar parella clau pública/privada 

```bash
ssh-keygen -t rsa -b 4096 -C "el_teu_email@example.com"
``` 
Exemple amb usuari projecteinf (projecteinf@boscdelacoma.cat)

![Generar clau ssh](./Images/Generate%20ssh%20key%20pair.png)

## Iniciar agent ssh

```bash
eval "$(ssh-agent -s)"
```

![Iniciar agent ssh](./Images/Iniciar%20agent%20ssh.png)

## Afegir clau privada a l'agent

```bash
ssh-add ~/.ssh/id_rsa
```

![Associar clau privada a l'usuari](./Images/Associar%20Clau%20privada.png)

# Configuració GitHub - Tots els sistemes

Accedim a l'opció "SSH and GPG keys" del menú "Settings" associat a l'usuari.

![SSH and GPG keys](./Images/SSH%20and%20GPG%20keys.png)

Botó "New SSH key" i copiem la clau pública.

![Associar clau publica a GitHub](./Images/Associar%20clau%20publica%20a%20GitHub.png)

![Clau associada](./Images/Clau%20associada.png)

# Verificació

```bash
ssh -T git@github.com
```

![Verificació](./Images/Verificació.png)
