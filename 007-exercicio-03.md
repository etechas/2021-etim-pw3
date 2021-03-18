# EXERCÍCIO 3


## CODIFICAÇÃO DE CLASSES

1 - Alterar a classe `TipoCozinhaController`, dentro do pacote _controller_, criando um método para buscar um tipo de cozinha por ID através da requisição GET.

2 - Alterar a classe `TipoCozinhaController` codificando um método para atualizar um tipo de cozinha por ID com a requisição PUT.

3 - Alterar a classe `TipoCozinhaController` com um método para excluir um tipo de cozinha por ID via requisição DELETE.

4 - Faça os testes através da ferramenta Postman.

### Resoluções

> **Item 1: Buscar tipo de cozinha por ID**

```java
@GetMapping("/{id}")
public TipoCozinha buscarPorId(@PathVariable Integer id) {
	Optional<TipoCozinha> resultado = dados.stream()
										   .filter(i -> i.getId().equals(id))
									 	   .findFirst();
	return resultado.isEmpty() ? null : resultado.get();
}
```

> **Item 2: Atualizar tipo de cozinha**

```java
@PutMapping("/{id}")
public TipoCozinha atualizar(@PathVariable Integer id, 
							 @RequestBody TipoCozinha body) {
	Optional<TipoCozinha> resultado = dados.stream()
			  							   .filter(i -> i.getId().equals(id))
			  							   .findFirst();
	if (resultado.isEmpty()) {
		return null;
	}
	TipoCozinha atualizado = resultado.get();
	atualizado.setNome(body.getNome());
	return atualizado;
}
```

> **Item 3: Excluir tipo de cozinha**

```java
@DeleteMapping("/{id}")
public void excluir(@PathVariable Integer id) {
	Optional<TipoCozinha> resultado = dados.stream()
			  							   .filter(i -> i.getId().equals(id))
			  							   .findFirst();
	if (resultado.isEmpty()) {
		return;
	}
	
	dados = dados.stream()
				 .filter(i -> !i.getId().equals(id))
				 .collect(Collectors.toList());
	}
```
