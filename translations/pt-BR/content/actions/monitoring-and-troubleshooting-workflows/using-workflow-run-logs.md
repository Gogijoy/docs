---
title: Usar registros de execução do fluxo de trabalho
intro: 'Você pode visualizar, pesquisar e fazer download dos logs para cada trabalho em uma execução de fluxo de trabalho.'
redirect_from:
  - /actions/managing-workflow-runs/using-workflow-run-logs
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
---

{% data reusables.actions.enterprise-beta %}
{% data reusables.actions.enterprise-github-hosted-runners %}

Na página de execução de fluxo de trabalho, você pode verificar se a execução está em andamento ou foi concluída. Você deve estar conectado a uma conta {% data variables.product.prodname_dotcom %} para visualizar as informações da execução do seu fluxo de trabalho, incluindo os repositórios públicos. Para obter mais informações, consulte "[Permissões de acesso no GitHub](/articles/access-permissions-on-github)".

Se a execução estiver concluída, será possível ver se o resultado teve êxito, se houve falha, se foi cancelado ou se ficou neutro. Em caso de falha, você poderá exibir e pesquisar os logs de criação para diagnosticar a falha e executar o fluxo de trabalho novamente. Você também pode visualizar os minutos da execução do trabalho faturável ou fazer o download dos registros e criar artefatos.

O {% data variables.product.prodname_actions %} usa a API de Verificação para mostrar os status, resultados e logs de um fluxo de trabalho. O {% data variables.product.prodname_dotcom %} cria um novo conjunto de verificações para cada execução de fluxo de trabalho. O conjunto de verificações contêm uma execução de verificação para cada trabalho no fluxo de trabalho, e cada trabalho inclui etapas. As ações do {% data variables.product.prodname_actions %} são executadas como etapas no fluxo de trabalho. Para obter mais informações sobre a API de verificações, consulte "[Verificações](/rest/reference/checks)".

{% data reusables.actions.invalid-workflow-files %}

## Exibir logs para diagnosticar falhas

Se houver falha na execução do fluxo de trabalho, você poderá ver qual etapa causou a falha e revisar os logs de criação da etapa com falha para resolver os problemas. Também é possível ver a duração da execução de cada etapa. Além disso, você pode copiar um permalink para determinada linha no arquivo de log a fim de compartilhar com a sua equipe. {% data reusables.repositories.permissions-statement-read %}

Além das etapas configuradas no arquivo do fluxo de trabalho, {% data variables.product.prodname_dotcom %} acrescenta duas etapas adicionais a cada trabalho para configurar e concluir a execução do trabalho. Estas etapas estão registradas na execução do fluxo de trabalho com os nomes "Configurar trabalho" e "Concluir trabalho".

Para trabalhos executados em executores hospedados no {% data variables.product.prodname_dotcom %}, "Configurar trabalho" registra os detalhes do ambiente virtual do executor e inclui um link para a lista de ferramentas pré-instaladas que estavam presentes na máquina do executor.

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.actions-tab %}
{% data reusables.repositories.navigate-to-workflow-superlinter %}
{% data reusables.repositories.view-run-superlinter %}
{% data reusables.repositories.navigate-to-job-superlinter %}
{% data reusables.repositories.view-failed-job-results-superlinter %}
{% data reusables.repositories.view-specific-line-superlinter %}

## Pesquisar logs

É possível pesquisar os logs de criação em determinadas etapas. Na pesquisa dos logs, somente as etapas expandidas são incluídas nos resultados. {% data reusables.repositories.permissions-statement-read %}

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.actions-tab %}
{% data reusables.repositories.navigate-to-workflow-superlinter %}
{% data reusables.repositories.view-run-superlinter %}
{% data reusables.repositories.navigate-to-job-superlinter %}
1. No canto superior direito da saída do log, na caixa **Search logs** (Pesquisar logs), digite um termo de consulta.
{% ifversion fpt or ghes > 3.0 or ghae or ghec %}
  ![Caixa de pesquisa de logs](/assets/images/help/repository/search-log-box-updated-2.png)
{% else %}
  ![Caixa de pesquisa de logs](/assets/images/help/repository/search-log-box-updated.png)
{% endif %}

## Fazer download dos registros

Você pode fazer o download dos arquivos de registro da execução do seu fluxo de trabalho. Você também pode fazer o download dos artefatos de um fluxo de trabalho. Para obter mais informações, consulte "[Dados recorrentes do fluxo de trabalho que usam artefatos](/actions/automating-your-workflow-with-github-actions/persisting-workflow-data-using-artifacts)". {% data reusables.repositories.permissions-statement-read %}

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.actions-tab %}
{% data reusables.repositories.navigate-to-workflow-superlinter %}
{% data reusables.repositories.view-run-superlinter %}
{% data reusables.repositories.navigate-to-job-superlinter %}
1. No canto superior direito, clique em {% ifversion fpt or ghes > 3.0 or ghae or ghec %}{% octicon "gear" aria-label="The gear icon" %}{% else %}{% octicon "kebab-horizontal" aria-label="The horizontal kebab icon" %}{% endif %} e selecione **Fazer download do arquivo de registro**.
  {% ifversion fpt or ghes > 3.0 or ghae or ghec %}
  ![Menu suspenso Download logs (Baixar logs)](/assets/images/help/repository/download-logs-drop-down-updated-2.png)
  {% else %}
  ![Menu suspenso Download logs (Baixar logs)](/assets/images/help/repository/download-logs-drop-down-updated.png)
  {% endif %}

## Excluir registros

Você pode excluir arquivos de registro da execução do seu fluxo de trabalho. {% data reusables.repositories.permissions-statement-write %}

{% data reusables.repositories.navigate-to-repo %}
{% data reusables.repositories.actions-tab %}
{% data reusables.repositories.navigate-to-workflow-superlinter %}
{% data reusables.repositories.view-run-superlinter %}
1. No canto superior direito, clique em {% octicon "kebab-horizontal" aria-label="The horizontal kebab icon" %}.
    {% ifversion fpt or ghes > 3.0 or ghae or ghec %}
    ![Ícone horizontal do kebab](/assets/images/help/repository/workflow-run-kebab-horizontal-icon-updated-2.png)
    {% else %}
    ![Ícone horizontal do kebab](/assets/images/help/repository/workflow-run-kebab-horizontal-icon-updated.png)
    {% endif %}
2. Para excluir os arquivos de registro, clique no botão **Excluir todos os registros** e revise a instrução de confirmação.
  {% ifversion fpt or ghes > 3.0 or ghae or ghec %}
  ![Excluir todos os registros](/assets/images/help/repository/delete-all-logs-updated-2.png)
  {% else %}
  ![Excluir todos os registros](/assets/images/help/repository/delete-all-logs-updated.png)
  {% endif %}
Após excluir os registros, o botão **Excluir todos os registros** será removido para indicar que nenhum arquivo de registro permaneça na execução do fluxo de trabalho.

## Visualizar registros com {% data variables.product.prodname_cli %}

{% data reusables.cli.cli-learn-more %}

Para visualizar o registro para uma tarefa específica, use o subcomando `executar a vista`. Substitua `run-id` pelo ID da execução que você deseja visualizar os registros. {% data variables.product.prodname_cli %} retorna um menu interativo para você escolher um trabalho a partir da execução. Se você não especificar `run-id`, {% data variables.product.prodname_cli %} irá retornar um menu interativo para você escolher uma execução recente e, em seguida, irá retornar outro menu interativo para você escolher um trabalho da execução.

```shell
gh run view <em>run-id</em> --log
```

Você também pode usar o sinalizador `--job` para especificar um ID de trabalho. Substitua `job-id` pelo ID do trabalho para o qual você deseja exibir os registros.

```shell
gh run view --job <em>job-id</em> --log
```

Você pode usar `grep` para pesquisar o registro. Por exemplo, este comando retornará todas as entradas do registro que contêm a palavra `erro`.

```shell
gh run view --job <em>job-id</em> --log | grep error
```

Para filtrar os registros para quaisquer etapas que falharam, use `--log-failed` em vez de `--log`.

```shell
gh run view --job <em>job-id</em> --log-failed
```
