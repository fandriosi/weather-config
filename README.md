# weather-config-repo

Repositório de configurações externas para a aplicação `weather` via Spring Cloud Config.

## Estrutura

- `weather.properties`: configurações comuns (todos os ambientes)
- `weather-dev.properties`: sobreposições para desenvolvimento
- `weather-docker.properties`: sobreposições para execução em container
- `weather-prod.properties`: sobreposições para produção

## Convenção de carregamento

A aplicação cliente usa:

- `spring.cloud.config.name=weather`
- profile ativo (`dev`, `docker`, `prod`) para escolher o arquivo adicional.

Exemplos carregados:

- Sem profile: `weather.properties`
- Com `SPRING_PROFILES_ACTIVE=docker`: `weather.properties` + `weather-docker.properties`

## Boas práticas

- Não commitar segredos reais (senhas, tokens, secrets JWT).
- Use placeholders de ambiente (`${VAR}`) para dados sensíveis.
- Faça mudanças via Pull Request para rastreabilidade.
