---
title: Sobre as atualizações de segurança do Dependabot
intro: '{% data variables.product.prodname_dependabot %} pode corrigir dependências vulneráveis para você, levantando pull requests com atualizações de segurança.'
shortTitle: Dependabot security updates
redirect_from:
  - /github/managing-security-vulnerabilities/about-github-dependabot-security-updates
  - /github/managing-security-vulnerabilities/about-dependabot-security-updates
  - /code-security/supply-chain-security/about-dependabot-security-updates
  - /code-security/supply-chain-security/managing-vulnerabilities-in-your-projects-dependencies/about-dependabot-security-updates
versions:
  fpt: '*'
  ghec: '*'
  ghes: '> 3.2'
type: overview
topics:
  - Dependabot
  - Security updates
  - Vulnerabilities
  - Repositories
  - Dependencies
  - Pull requests
ms.openlocfilehash: 993fb0c4a810f24c63d0b4063029a7a5801ff85a
ms.sourcegitcommit: 478f2931167988096ae6478a257f492ecaa11794
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2022
ms.locfileid: '147861665'
---
<!--Marketing-LINK: From /features/security/software-supply-chain page "About Dependabot security updates".-->

{% data reusables.dependabot.beta-security-and-version-updates %} {% data reusables.dependabot.enterprise-enable-dependabot %}

## Sobre as {% data variables.product.prodname_dependabot_security_updates %}

{% data variables.product.prodname_dependabot_security_updates %} torna mais fácil para você corrigir dependências vulneráveis no seu repositório. Se você habilitar este recurso, quando um alerta de {% data variables.product.prodname_dependabot %} for criado para uma dependência vulnerável no gráfico de dependências do seu repositório, {% data variables.product.prodname_dependabot %} tenta corrigir isso automaticamente. Para obter mais informações, confira "[Sobre os {% data variables.product.prodname_dependabot_alerts %}](/code-security/supply-chain-security/about-alerts-for-vulnerable-dependencies)" e "[Sobre as {% data variables.product.prodname_dependabot_security_updates %}](/github/managing-security-vulnerabilities/configuring-dependabot-security-updates)".

{% data variables.product.prodname_dotcom %} pode enviar  {% data variables.product.prodname_dependabot_alerts %} para repositórios afetados por uma vulnerabilidade revelada por uma consultoria de segurança de {% data variables.product.prodname_dotcom %} recentemente publicada. {% data reusables.security-advisory.link-browsing-advisory-db %}

{% data variables.product.prodname_dependabot %} verifica se é possível atualizar a dependência vulnerável para uma versão fixa sem comprometer o gráfico de dependências para o repositório. Em seguida, {% data variables.product.prodname_dependabot %} levanta um pull request para atualizar a dependência para a versão mínima que inclui o patch e os links do pull request para o alerta de {% data variables.product.prodname_dependabot %} ou relata um erro no alerta. Para obter mais informações, confira "[Solução de problemas de erros do {% data variables.product.prodname_dependabot %}](/github/managing-security-vulnerabilities/troubleshooting-dependabot-errors)".



{% note %}

**Observação**: o recurso {% data variables.product.prodname_dependabot_security_updates %} está disponível para repositórios em que você habilitou o grafo de dependência e {% data variables.product.prodname_dependabot_alerts %}. Você verá um alerta de {% data variables.product.prodname_dependabot %} para cada dependência vulnerável identificada no seu gráfico de dependências completas. No entanto, atualizações de segurança são acionadas apenas para dependências especificadas em um manifesto ou arquivo de bloqueio. Para obter mais informações, confira "[Sobre o grafo de dependência](/github/visualizing-repository-data-with-graphs/about-the-dependency-graph#dependencies-included)". {% ifversion dependabot-security-updates-unlock-transitive-dependencies %}

Para npm, {% data variables.product.prodname_dependabot %} gerará uma solicitação de pull para atualizar uma dependência definida explicitamente para uma versão segura, mesmo que isso signifique atualizar a dependência ou as dependências pai. Para outros ecossistemas, {% data variables.product.prodname_dependabot %} não poderá atualizar uma dependência indireta ou transitiva se isso também exigir uma atualização na dependência pai. Para obter mais informações, confira "[O dependabot tenta atualizar dependências sem um alerta](/en/code-security/dependabot/working-with-dependabot/troubleshooting-dependabot-errors#dependabot-tries-to-update-dependencies-without-an-alert)."{% endif %} 

{% endnote %}

Você pode habilitar um recurso relacionado, {% data variables.product.prodname_dependabot_version_updates %}, para que {% data variables.product.prodname_dependabot %} abra pull requests para atualizar o manifesto para a última versão da dependência, sempre que detectar uma dependência desatualizada. Para obter mais informações, confira "[Sobre as {% data variables.product.prodname_dependabot %}](/github/administering-a-repository/about-dependabot-version-updates)".

{% data reusables.dependabot.pull-request-security-vs-version-updates %}

## Sobre os pull requests para atualizações de segurança

Cada pull request contém tudo o que você precisa para revisar mesclar, de forma rápida e segura, uma correção proposta em seu projeto. Isto inclui informações sobre a vulnerabilidade como, por exemplo, notas de lançamento, entradas de registros de mudanças e detalhes do commit. Detalhes de quais vulnerabilidades são resolvidas por um pull request de qualquer pessoa que não tem acesso a {% data variables.product.prodname_dependabot_alerts %} para o repositório.

Ao fazer merge de um pull request que contém uma atualização de segurança, o alerta de {% data variables.product.prodname_dependabot %} correspondente é marcado como resolvido no seu repositório. Para obter mais informações sobre as solicitações de pull do {% data variables.product.prodname_dependabot %}, confira "[Como gerenciar as solicitações de pull para atualizações de dependência](/github/administering-a-repository/managing-pull-requests-for-dependency-updates)".

{% data reusables.dependabot.automated-tests-note %}

{% ifversion fpt or ghec %}

## Sobre pontuações de compatibilidade

O {% data variables.product.prodname_dependabot_security_updates %} pode incluir uma pontuação de compatibilidade para que você saiba se atualizar uma dependência poderá causar alterações significativas no seu projeto. Estes são calculados a partir de testes de CI em outros repositórios públicos onde a mesma atualização de segurança foi gerada. Uma pontuação de compatibilidade da atualização é a porcentagem de execuções de CI que foram aprovadas durante a atualização entre versões específicas da dependência.

{% endif %}

## Sobre notificações para atualizações de segurança de {% data variables.product.prodname_dependabot %}

Você pode filtrar suas notificações em {% data variables.product.company_short %} para mostrar as atualizações de segurança de {% data variables.product.prodname_dependabot %}. Para obter mais informações, confira "[Como gerenciar notificações na sua caixa de entrada](/github/managing-subscriptions-and-notifications-on-github/managing-notifications-from-your-inbox#dependabot-custom-filters)".
