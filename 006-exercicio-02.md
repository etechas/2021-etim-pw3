# EXERCÍCIO 2


## CODIFICAÇÃO DE CLASSES

1 - Crie a classe `TipoCozinha` dentro do pacote _model_ e com os campos **id** e **nome**. 

2 - Crie a classe `TipoCozinhaController` dentro do pacote _controller_. É necessário indicar que a classe é um controller e receberá as requisições HTTP, anotando-a com `@RestController`.

3 - As requisições HTTP absorvidas por essa classe serão feitas no recurso `tipos-cozinha`. Assim, anote a classe, também, com a anotação `@RequestMapping`.

4 - Declare uma lista de TipoCozinha como atributo para armazenar os dados em memória.

5 - Crie um método para listar todos os tipos de cozinha através da requisição GET.

6 - Crie um método para adicionar um tipo de cozinha na lista através da requisição POST.

7 - Faça os testes através da ferramenta Postman.

### Resoluções

> **Item 1: TipoCozinha**

```java
@Getter
@Setter
public class TipoCozinha {

	private Integer id;
	private String nome;
	
}
```

> **Item 2 e item 3: TipoCozinhaController**

```java
@RestController
@RequestMapping("tipos-cozinha")
public class TipoCozinhaController {

}
```

> **Item 4: Lista de tipos de cozinha**

```java

private List<TipoCozinha> dados = new ArrayList<TipoCozinha>();

```

> **Item 5: Listar todos os tipos de cozinha**

```java
@GetMapping
public List<TipoCozinha> listar() {
	return dados;
}
```
> **Item 6: Adicionar na lista**

```java
@PostMapping
public TipoCozinha inserir(@RequestBody TipoCozinha body) {
	body.setId(dados.size() + 1);
	dados.add(body);
	return body;
}
```