---
title: Zvládnutí firemní složitosti v mikroslužbě pomocí vzorů DDD a CQRS
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Pochopte, jak řešit složité obchodní scénáře, které používají vzory DDD a CQRS.
ms.date: 10/08/2018
ms.openlocfilehash: 852073548a66fbe568fc5c2531342db944d5a8b0
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144640"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Zvládnutí firemní složitosti v mikroslužbě pomocí vzorů DDD a CQRS

*Navrhněte doménový model pro jednotlivé mikroslužby nebo s ohraničeným kontextem, který odráží porozumění obchodní doméně.*

Tato část se zaměřuje na pokročilejší mikroslužby, které implementujete, když potřebujete vypořádat se se složitými subsystémy nebo mikroslužbami, které jsou odvozené od znalostí odborníků na domény s neustále se měnícími obchodními pravidly. Vzory architektury použité v této části jsou založené na CQRSch návrhech založených na doménách (DDD) a CQRS (Command and Query Responsibility Segregation) (), jak je znázorněno na obrázku 7-1.

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Diagram porovnání vzorů externích a interních architektur":::
Rozdíl mezi externí architekturou: vzory mikroslužeb, brány API, odolná komunikace, pub/sub atd. a interní architektura: řízené daty/CRUD, DDD vzory, vkládání závislostí, vícenásobné knihovny atd.
:::image-end:::

**Obrázek 7-1**. Externí architektura mikroslužeb oproti vnitřním schématům architektury pro jednotlivé mikroslužby

Většina technik pro mikroslužby řízené daty, jako je například implementace služby ASP.NET Core webového rozhraní API nebo vystavení metadat Swagger pomocí swashbuckle nebo NSwag, se vztahují také na pokročilejší mikroslužby implementované interně pomocí vzorů DDD. Tato část je rozšířením předchozích sekcí, protože většina postupů, které jsme si vyznamenali dříve, platí i pro jakýkoliv druh mikroslužeb.

V této části najdete nejdřív podrobné informace o zjednodušených vzorech CQRS používaných v referenční aplikaci eShopOnContainers. Později získáte přehled technik DDD, které vám umožní najít běžné vzory, které můžete znovu použít ve svých aplikacích.

DDD je velké téma s bohatou sadou prostředků pro učení. Můžete začít s kniha, jako je [návrh založený na doméně](https://domainlanguage.com/ddd/) , pomocí Eric Evans a dalších materiálů od Vaughn Vernon, Jimmy Nilsson, Greg Younga, UDI Dahan, Jimmy Bogard a mnoha dalších expertů na DDD/CQRS. Ale většina z nich se snaží zjistit, jak se v rámci konverzace, tabulování a modelování domén s odborníky v konkrétní obchodní doméně naučíte používat DDD techniky.

#### <a name="additional-resources"></a>Další zdroje

##### <a name="ddd-domain-driven-design"></a>DDD (návrh založený na doméně)

- **Eric Evans. Jazyk domény** \
  <https://domainlanguage.com/>

- **Martin Fowlera. Návrh založený na doméně** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy Bogard. Posílení vaší domény: Úvod** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>DDD knihy

- **Eric Evans. Návrh založený na doméně: řešení složitosti na srdce softwaru** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans. Referenční dokumentace návrhu založeného na doméně: definice a souhrny vzorů** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon. Implementace návrhu založeného na doméně** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon. Návrh založený na doméně byl stále přetrvává.** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson. Použití návrhu a vzorů založených na doméně** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Cesar de la Torre. N-vrstvý Průvodce architekturou orientovaný na doménu s .NET** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram a Floyd Marinescu. Rychlé navrhování založené na doméně** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, záměrné ladění – vzory, principy a postupy návrhu založeného na doméně** \
  <https://www.wiley.com/Patterns%2C+Principles%2C+and+Practices+of+Domain+Driven+Design-p-9781118714706>

##### <a name="ddd-training"></a>DDD školení

- **Julie Lerman a Steve Smith. Základy návrhu založené na doméně** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Předchozí](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md) 
> [Další](apply-simplified-microservice-cqrs-ddd-patterns.md)
