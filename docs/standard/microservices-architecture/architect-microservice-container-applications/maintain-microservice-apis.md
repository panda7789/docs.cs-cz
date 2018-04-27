---
title: Mikroslužbu vytváření, vyvíjejí a správa verzí rozhraní API a kontrakty
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Mikroslužbu vytváření, vyvíjejí a správa verzí rozhraní API a kontrakty
keywords: Docker, Mikroslužeb, ASP.NET, kontejneru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7a80405f0a206cfaa0462392eddfc95878353cd7
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Mikroslužbu vytváření, vyvíjejí a správa verzí rozhraní API a kontrakty

Mikroslužbu rozhraní API je smlouva mezi službou a jeho klienty. Bude možné nezávisle vyvíjí mikroslužbu pouze v případě, že nedojde k narušení jeho rozhraní API kontrakt, který je důvod, proč je tak důležité kontrakt. Pokud změníte kontrakt, ovlivní klientské aplikace nebo vaší bránu rozhraní API.

Povaha definice rozhraní API, závisí na protokol, který používáte. Například pokud používáte zasílání zpráv (jako je [AMQP](https://www.amqp.org/)), rozhraní API se skládá z typů zpráv. Pokud používáte protokol HTTP a služeb RESTful, rozhraní API se skládá z adresy URL a JSON formáty požadavků a odpovědí.

Ale i v případě, že jste žádný jazyk o vaší počáteční kontrakt, rozhraní API služby bude nutné změnit v čase. Pokud k tomu dojde – a zejména v případě, že vaše rozhraní API je veřejné rozhraní API spotřebovávají více klientských aplikací – obvykle nemůže vynutit všichni klienti k upgradu vaší nové smlouvy rozhraní API. Obvykle je nutné přírůstkově nasazení nových verzí služby tak, že starý a nový verzích kontraktu služby běží současně. Proto je důležité mít strategii verze vaší služby.

Když změny rozhraní API jsou malé, jako když přidáte k vašemu rozhraní API atributy nebo parametry, klienty, kteří používají starší rozhraní API by měl přepínače a pracovat s novou verzi služby. Je možné zadat výchozí hodnoty pro všechny chybějící atributy, které jsou požadovány a klienti pravděpodobně moci ignorovat žádné atributy. navíc odpovědi.

Však někdy je nutné provést změny hlavní a kompatibilní rozhraní API služby. Vzhledem k tomu, že není možné vynutit klientské aplikace nebo služby k upgradu ihned na novou verzi, služba musí podporovat starší verze rozhraní API po nějakou dobu. Pokud používáte mechanismus založený na protokolu HTTP, jako je například REST, jeden z přístupů je pro vložení číslo verze rozhraní API v adrese URL nebo do hlavičky protokolu HTTP. Pak si můžete vybrat implementace obě verze služby současně v rámci stejné instance služby nebo nasazování různé instance, že každý zpracovat verzi rozhraní API. Je dobrým přístupem pro tento [zprostředkovatel vzor](https://en.wikipedia.org/wiki/Mediator_pattern) (například [MediatR knihovny](https://github.com/jbogard/MediatR)) oddělit různé implementace verze do nezávislé obslužné rutiny.

Nakonec, pokud používáte architekturu REST, [hypermédií](https://www.infoq.com/articles/mark-baker-hypermedia) je nejlepší řešení pro správu verzí, služeb a umožní evolvable rozhraní API.

## <a name="additional-resources"></a>Další zdroje

-   **Scott Hanselman. Správa verzí RESTful webová rozhraní API ASP.NET Core umožněno**
    <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

-   **Správa verzí RESTful webového rozhraní API**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Royi Fielding. Správa verzí, hypermédií a REST**
    <https://www.infoq.com/articles/roy-fielding-on-versioning>


>[!div class="step-by-step"]
[Předchozí] (asynchronous-message-based-communication.md) [Další] (microservices-addressability-service-registry.md)
