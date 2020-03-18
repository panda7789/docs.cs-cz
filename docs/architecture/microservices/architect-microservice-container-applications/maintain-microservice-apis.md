---
title: Vytváření, vývoj a správa verzí rozhraní API a kontraktů mikroslužeb
description: Vytvořte mikroservice API a smlouvy s ohledem na vývoj a správu verzí, protože potřebuje změnit.
ms.date: 09/20/2018
ms.openlocfilehash: 1972d02d8bf7935c71bfd383707ae19ea2baded9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295457"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Vytváření, vývoj a správa verzí rozhraní API a kontraktů mikroslužeb

Rozhraní API mikroslužeb je smlouva mezi službou a jejími klienty. Budete moci vyvíjet mikroslužbu nezávisle pouze v případě, že neporušíte jeho smlouvu rozhraní API, což je důvod, proč je smlouva tak důležitá. Pokud změníte smlouvu, bude to mít vliv na vaše klientské aplikace nebo bránu rozhraní API.

Povaha definice rozhraní API závisí na tom, který protokol používáte. Například pokud používáte zasílání zpráv (například [AMQP](https://www.amqp.org/)), rozhraní API se skládá z typů zpráv. Pokud používáte služby HTTP a RESTful, rozhraní API se skládá z adres URL a formátů JSON požadavků a odpovědí.

I když jste přemýšlivý ohledně počáteční smlouvy, rozhraní API služby bude muset v průběhu času změnit. Když k tomu dojde – a zejména pokud vaše rozhraní API je veřejné rozhraní API spotřebované více klientských aplikací – obvykle nelze vynutit všechny klienty k upgradu na novou smlouvu rozhraní API. Obvykle je třeba postupně nasadit nové verze služby tak, aby staré i nové verze smlouvy o poskytování služeb běží současně. Proto je důležité mít strategii pro správu verzí služby.

Pokud jsou změny rozhraní API malé, například pokud do rozhraní API přidáte atributy nebo parametry, klienti, kteří používají starší rozhraní API, by měli přepnout a pracovat s novou verzí služby. Je možné zadat výchozí hodnoty pro všechny chybějící atributy, které jsou požadovány, a klienti mohou být schopni ignorovat všechny další atributy odpovědi.

Někdy však potřebujete provést hlavní a nekompatibilní změny rozhraní API služby. Vzhledem k tomu, že pravděpodobně nebude možné vynutit okamžité upgradování klientských aplikací nebo služeb na novou verzi, musí služba po určitou dobu podporovat starší verze rozhraní API. Pokud používáte mechanismus založený na protokolu HTTP, jako je REST, jedním z přístupů je vložení čísla verze rozhraní API do adresy URL nebo do hlavičky HTTP. Pak se můžete rozhodnout mezi implementací obou verzí služby současně v rámci stejné instance služby nebo nasazením různých instancí, které každá zpracovává verzi rozhraní API. Dobrým přístupem k tomu je [mediator vzor](https://en.wikipedia.org/wiki/Mediator_pattern) (například [Knihovna MediatR](https://github.com/jbogard/MediatR)) oddělit různé verze implementace do nezávislé obslužné rutiny.

A konečně, pokud používáte architekturu REST, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) je nejlepším řešením pro správu verzí vašich služeb a povolení vyvíjející se api.

## <a name="additional-resources"></a>Další zdroje

- **Scott Hanselman. ASP.NET snadné správu verzí webového rozhraní API ASP.NET** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Správa verzí webového rozhraní RESTful** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roye Fieldinga. Správa verzí, hypermédia a REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
>[Předchozí](asynchronous-message-based-communication.md)
>[další](microservices-addressability-service-registry.md)
