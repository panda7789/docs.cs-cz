---
title: Vytváření, vývoj a správa verzí rozhraní API a kontraktů mikroslužeb
description: Vytváření mikroslužeb rozhraní API a kontraktů zvažujete vývoj a správu verzí, protože změní.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: f42de3895f7f9affe09891fd89621fbb414313e9
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612105"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Vytváření, vývoj a správa verzí rozhraní API a kontraktů mikroslužeb

Mikroslužba rozhraní API je kontrakt mezi službou a klienty. Budete moct vyvíjet mikroslužby nezávisle na sobě jenom v případě, že nedojde k narušení jeho kontrakt rozhraní API, který je důvod, proč je proto důležité kontrakt. Pokud změníte kontrakt, bude to mít vliv klientských aplikací nebo brány rozhraní API.

Druh definice rozhraní API závisí na protokol, který používáte. Například pokud používáte zasílání zpráv (například [AMQP](https://www.amqp.org/)), rozhraní API se skládá z typy zpráv. Pokud používáte protokol HTTP a služby typu REST, se skládá z JSON formáty požadavků a odpovědí a adresy URL rozhraní API.

Nicméně i v případě, že je pro vás důkladné o počáteční smlouvy, rozhraní API služby muset v průběhu času měnit. Když se to stane – a zejména v případě, že vaše rozhraní API je veřejné rozhraní API používané více klientských aplikací – obvykle nemůžou vynutit všichni klienti k upgradu na nové smlouvy rozhraní API. Obvykle je nutné přírůstkově nasazovat nové verze služby tak, aby staré a nové verze kontraktu služby jsou spuštěny souběžně. Proto je důležité mít strategii pro vaši službu správy verzí.

Při změn rozhraní API jsou malé, například pokud můžete přidat atributy nebo parametry do vašeho rozhraní API, klienty, kteří používají starší rozhraní API by měla přepnutí a pracovat s novou verzi služby. Je možné zadat výchozí hodnoty pro všechny chybějící atributy, které jsou požadovány, a klienti možná půjde ignorovat jakékoli další odpovědi atributy.

Ale někdy potřebujete provádět změny hlavní a nekompatibilní rozhraní API služby. Vzhledem k tomu, že nebudete moci vynutit klientských aplikací nebo služeb hned upgradovat na novou verzi, musí podporovat službu starší verze rozhraní API pro určitou dobu. Pokud používáte mechanismus založený na protokolu HTTP, jako je REST, jedním z přístupů je vložit číslo verze rozhraní API v adrese URL, nebo do hlavičky protokolu HTTP. Pak se můžete rozhodnout mezi implementace obě verze služby současně v rámci stejné instance služby nebo nasazení různých instancích, každý zpracovat verzi rozhraní API. Je dobrý přístup pro toto [zprostředkovatel vzor](https://en.wikipedia.org/wiki/Mediator_pattern) (například [MediatR knihovny](https://github.com/jbogard/MediatR)) oddělit různé implementace verze do nezávislé obslužné rutiny.

Nakonec, pokud používáte s architekturou REST [Hypermédia](https://www.infoq.com/articles/mark-baker-hypermedia) je nejlepší řešení pro správu verzí, služeb a umožní evolvable rozhraní API.

## <a name="additional-resources"></a>Další zdroje

- **Scott Hanselman. Správa verzí RESTful webového rozhraní API ASP.NET Core snadné** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Správa verzí RESTful webového rozhraní API** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy Fielding. Správa verzí, Hypermédia a REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
>[Předchozí](asynchronous-message-based-communication.md)
>[další](microservices-addressability-service-registry.md)
