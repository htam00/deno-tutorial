# Instalação
```bash
curl -fsSL https://deno.land/x/install/install.sh | sh
```

```bash 
export DENO_INSTALL="/home/home/.deno"
```

```bash
export PATH="$DENO_INSTALL/bin:$PATH"
```

# Criando um servidor
Agora vamos criar um servidor simples para nós iniciar-mos nosso 
estudo com deno.

Vamos criar um arquivo, eu vou chamar de main.ts, mais você é livre pra colocar o nome que desejar, neste tutorial estou usando o linux.
```bash
touch main.ts
```
Agora que já criamos nosso arquivo, vamos para o que interessa,
primeiro vamos importar o link do servidor para dentro do nosso arquivo, porque diferentemente do node que baixava os pacotes pra dentro do nosso projeto, o deno trabalha diferente, você passa o link onde está hospedado o pacote que você deseja usar e apos executar o arquivo ele baixar este arquivo e memoriza em cache para quando você for utilizar novamente em um outro arquivo ele não vai precisar mais baixar, só vai executar arquivo e pronto.
```javascript
import { serve } from "https://deno.land/std@0.55.0/http/server.ts";
```

agora vamos criar um variavel para passar a porta que iremos utilizar, ao executar nosso arquivo.
```javascript
const s = serve({ port: 8000 });
```

Olhe como ficou nosso arquivo, pronto pra ser executado.
Muito simples né, vamos vê se realmente vai executar.
```javascript
import { serve } from "https://deno.land/std@0.55.0/http/server.ts";
const s = serve({ port: 8000 });
console.log("http://localhost:8000");
for await (const ) {
    res.respond({ body: "Hello World\n" });
}
```

Vamos agora executar nosso codigo.
```bash
deno run main.ts
error: Uncaught PermissionDenied: network access to "0.0.0.0:8000", run again with the --allow-net flag
    at unwrapResponse ($deno$/ops/dispatch_json.ts:43:11)
    at Object.sendSync ($deno$/ops/dispatch_json.ts:72:10)
    at Object.listen ($deno$/ops/net.ts:51:10)
    at listen ($deno$/net.ts:152:22)
    at serve (https://deno.land/std@0.55.0/http/server.ts:252:20)
    at file:///home/home/htam/deno_learn/main.ts:3:11
```

Note que ao executarmos, ele apresenta um erro, isso acontece porque não demos permissão para acessar a rede, para que ele possa executar precisamos passar este flag --allow-net pronto, agora vamos executar.
```bash
deno run --allow-net main.ts 
```

