---
layout: post
title:  "Anaconda libstdc++.so.6: version `GLIBCXX_3.4.20' not found"
date:   2025-03-01 09:48:04 -0300
categories: anaconda error fix
---

Recentemente, ao tentar rodar um ambiente do Anaconda, me deparei com o seguinte erro:

```
libstdc++.so.6: version `GLIBCXX_3.4.20' not found
```

Esse erro ocorre geralmente quando a versão da biblioteca `libstdc++.so.6` no seu sistema não é compatível com o ambiente do Anaconda que você está usando. Esse tipo de problema é comum quando há incompatibilidade entre a versão da biblioteca C++ do seu sistema e a versão esperada pelo Anaconda.

Após muita pesquisa, encontrei uma solução no StackOverflow, que foi a maneira mais rápida e eficiente de corrigir o problema.

### Como resolvi:

A solução proposta foi atualizar o link simbólico da biblioteca `libstdc++.so.6` para a versão correta dentro do ambiente do Anaconda. Para isso, você deve rodar o seguinte comando:

```bash
ln -sf /usr/lib/x86_64-linux-gnu/libstdc++.so.6 ${CONDA_PREFIX}/lib/libstdc++.so.6
```

**Explicação do comando:**
- `ln -sf`: cria um link simbólico forçado, substituindo o arquivo de destino se já existir.
- `/usr/lib/x86_64-linux-gnu/libstdc++.so.6`: é o caminho da versão da biblioteca no sistema.
- `${CONDA_PREFIX}/lib/libstdc++.so.6`: é o caminho onde o Anaconda espera encontrar a biblioteca.

Este comando cria um link simbólico dentro do seu ambiente Anaconda apontando para a versão correta da biblioteca, o que resolve a incompatibilidade.

### Como aplicar a solução:

1. Abra o terminal.
2. Ative o ambiente Anaconda que está apresentando o erro.
3. Execute o comando mencionado acima.
4. Verifique se o problema foi resolvido executando seu código novamente.

### Resultados:

Após rodar o comando, o erro foi corrigido e pude continuar meu trabalho normalmente sem mais problemas relacionados a esse erro.

### Referências:

Se você também se deparou com esse erro, pode conferir o [post completo no StackOverflow](https://stackoverflow.com/questions/48453497/anaconda-libstdc-so-6-version-glibcxx-3-4-20-not-found) para mais detalhes.

Espero que essa solução seja útil para você também! Se tiver qualquer dúvida, sinta-se à vontade para comentar ou entrar em contato!

