# Aplicações Inteligentes com Angular

## Rotas

O roteamento no Angular é um sistema que permite que você crie aplicativos de página única (SPAs).

Arquivo de rotas: `app-routing.module.ts`

- `NgModule`: Provê o decorador para definir um módulo Angular;
- `RouterModule`: Provê as diretivas e serviços para gerenciamento de rotas na aplicação;
- `Routes`: Type que representa um vetor de definições de rotas (objetos path-component);

Ao invés de usar `<a href=""></a>`, utiliza-se `<a [routerLink]=""`.

### Params (/:\*) e QueryParams (?\*=&?\*=)

Para recuperar parâmetros nas rotas, utilizar a classe `ActivatedRoute`. A classe `ActivatedRoute` fornece acesso à rota ativa no momento, incluindo seus parâmetros.

```typescript
const routes: Routes = [
  {
    path: '/produto/:id',
    component: ProdutoComponent
  }
];
```

---

```typescript
import { ActivatedRoute } from '@angular/router';

@Component({
  selector: 'app-produto',
  templateUrl: './produto.component.html',
  styleUrls: ['./produto.component.css']
})
export class ProdutoComponent {

  constructor(private activatedRoute: ActivatedRoute) {}

  ngOnInit() {
    const id = this.activatedRoute.param('id');
    // ...
  }

}
```

ou utilizar:

```typescript
    this.activatedRoute.params.subscribe(
      res => console.log(res)
    )

    this.activatedRoute.queryParams.subscribe(
      res => console.log(res)
    )
```

## Services

> Componente do aplicativo que pode realizar operações longas e não fornece uma interface do usuário.

Em Angular, são objetos typescript singleton (existência de apenas uma instância de uma classe, mantendo um ponto global de acesso ao seu objeto). Possuem métodos que mantêm os dados disponíveis ao longo da vida de um aplicativo.

O foco é separar a parte lógica de um componente para definir comportamentos e renderização, e a lógica de negócios que seja responsável por outras tarefas, como comunicação com o servidor.

### Promises

> Objeto que representa uma eventual conclusão ou falha de uma operação assíncrona (pending/fulfilled/rejected) e seu valor resultante.

- _Promises_ são nativas do ES.
- _Promises_ são adequadas para operações assíncronas únicas, como buscar dados de uma API.
- Uma _Promise_ é sempre assíncrona e pode fornecer um único valor.
- Uma vez que uma _Promise_ é resolvida, ela não pode ser reutilizada.

### Observables

Parte do paradigma reativo, são usados ​​para lidar com fluxos de dados assíncronos. Eles podem emitir vários valores ao longo do tempo e são canceláveis.

- Ideais para lidar com fluxos de dados onde vários valores podem ser emitidos ao longo do tempo.
- Um _Observable_ pode ser tanto síncrono quanto assíncrono, e é um fluxo de valores (de 0 a múltiplos valores).
- _Observables_ fornecem operadores como map, forEach, reduce, semelhantes a um array.
- _Observables_ são _lazy_, ou seja, só começam quando você se inscreve neles.
- _Observables_ têm a vantagem de serem canceláveis.

## Projetos

- [Recriando a Interface da PlayStation Store com Angular](https://github.com/Err0rGCeni/DIOProject_PSStoreAngular)
