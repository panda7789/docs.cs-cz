---
title: Vytváření, vývoj a správa verzí rozhraní API a kontraktů mikroslužeb
description: Vytvářejte rozhraní API mikroslužeb a kontrakty, které zvažuje vývoj a správu verzí, protože se vyžaduje změna.
ms.date: 09/20/2018
ms.openlocfilehash: 1972d02d8bf7935c71bfd383707ae19ea2baded9
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295457"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Vytváření, vývoj a správa verzí rozhraní API a kontraktů mikroslužeb

Rozhraní API mikroslužeb je smlouva mezi službou a jejími klienty. Mikroslužbu budete moct vyvíjet nezávisle jenom v případě, že jste nepřerušili její kontrakt rozhraní API. to je důvod, proč je smlouva důležitá. Pokud změníte smlouvu, bude to mít vliv na vaše klientské aplikace nebo na bránu rozhraní API.

Povaha definice rozhraní API závisí na tom, který protokol používáte. Například pokud používáte zasílání zpráv (například [AMQP](https://www.amqp.org/)), rozhraní API se skládá z typů zpráv. Pokud používáte služby HTTP a RESTful, rozhraní API se skládá z adres URL a formátů JSON požadavků a odpovědí.

Nicméně i v případě, že jste důkladnéi o vaší počáteční smlouvě, rozhraní API služby se bude muset v průběhu času změnit. Když k tomu dojde – a zejména v případě, že vaše rozhraní API je veřejné rozhraní API spotřebované více klientskými aplikacemi – obvykle nemůžete vynutit, aby všichni klienti upgradovali na váš nový kontrakt rozhraní API. Obvykle je třeba postupně nasazovat nové verze služby tak, aby se současně používaly staré i nové verze kontraktu služby. Proto je důležité mít strategii pro správu verzí služby.

Pokud jsou změny rozhraní API malé, například pokud do svého rozhraní API přidáte atributy nebo parametry, klienti, kteří používají starší rozhraní API, by se měli přepínat a pracovat s novou verzí služby. Může být možné zadat výchozí hodnoty pro všechny chybějící atributy, které jsou požadovány, a klienti mohou ignorovat další atributy odpovědi.

Někdy ale budete muset v rozhraní API služby udělat významné a nekompatibilní změny. Vzhledem k tomu, že pravděpodobně nebudete moci vynutit, aby klientské aplikace nebo služby byly okamžitě upgradovány na novou verzi, služba musí po určitou dobu podporovat starší verze rozhraní API. Pokud používáte mechanizmy založené na protokolu HTTP, například REST, je jedním z přístupů vložení čísla verze rozhraní API do adresy URL nebo do hlavičky protokolu HTTP. Pak se můžete rozhodnout mezi implementací obou verzí služby současně v rámci stejné instance služby nebo nasazením různých instancí, které jednotlivé verze rozhraní API zpracovávají. Dobrým přístupem k tomuto je [vzor](https://en.wikipedia.org/wiki/Mediator_pattern) vedení (například [MediatR Library](https://github.com/jbogard/MediatR)), aby se odlišily různé verze implementace na nezávislé obslužné rutiny.

Nakonec, pokud používáte architekturu REST [, je pro](https://www.infoq.com/articles/mark-baker-hypermedia) vás nejvhodnější řešení pro správu verzí vašich služeb a povoluje se vyvíjejíná rozhraní API.

## <a name="additional-resources"></a>Další zdroje

- **Scott Hanselman Jednodušší ASP.NET Core RESTful webového rozhraní API pro správu** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Správa verzí webového rozhraní API RESTful** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy pole. Správa verzí, multimédií a REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
>[Předchozí](asynchronous-message-based-communication.md)Další
>[](microservices-addressability-service-registry.md)
