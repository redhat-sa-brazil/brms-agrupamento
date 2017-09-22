# BRMS Agrupamento
Agrupa múltiplas Knowledge Bases de vários projetos

## Execução dos Testes

### URL Post
http://localhost:8080/kie-server/services/rest/server/containers/instances/agrupamento

### Teste 1 - Executando as regras do projeto BRMS Monitoramento de Operações Tesouraria
```
<batch-execution lookup="agrupamentoStatelessSession">
<insert out-identifier="o1">
	<com.redhat.tesouraria.Operacao>
		<mesa>CAMBIO</mesa>
		<gestor>CAMBIO</gestor>
	</com.redhat.tesouraria.Operacao>
</insert>
<start-process processId="tesouraria.Fluxo">
</start-process>
<fire-all-rules />
</batch-execution>
```

### Teste 2 - Executando as regras do projeto BRMS Cálculo de Impacto
```
<batch-execution lookup="agrupamentoStatelessSession">
<insert out-identifier="c1">
	<com.redhat.impacto.Calculo>
		<scoreOrigem>4.0</scoreOrigem>
		<scoreDestino>1.0</scoreDestino>
		<segmentoDestino>GRANDES_EMPRESAS</segmentoDestino>
		<ratingDestino>BOM</ratingDestino>
		<setorOrigem>SETOR_PETROLEO</setorOrigem>
		<pagamento>6</pagamento>
		<recebimentos>
			<com.redhat.impacto.Recebimento>
				<origem>A</origem>
				<recebimento>1</recebimento>
			</com.redhat.impacto.Recebimento>
			<com.redhat.impacto.Recebimento>
				<origem>B</origem>
				<recebimento>3</recebimento>
			</com.redhat.impacto.Recebimento>
			<com.redhat.impacto.Recebimento>
				<origem>C</origem>
				<recebimento>6</recebimento>
			</com.redhat.impacto.Recebimento>
		</recebimentos>		
	</com.redhat.impacto.Calculo>
</insert>
<start-process processId="impacto.Fluxo">
</start-process>
<fire-all-rules />
</batch-execution>
```



