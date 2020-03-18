---
title: Zvládnutí firemní složitosti v mikroslužbě pomocí vzorů DDD a CQRS
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pochopit, jak řešit složité obchodní scénáře použití DDD a CQRS vzory
ms.date: 10/08/2018
ms.openlocfilehash: 88b105b68307c8587f877bb9ddf370e143d8539b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73739827"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Řešení obchodní složitosti v mikroslužbě se vzory DDD a CQRS

*Navrhněte model domény pro každou mikroslužbu nebo ohraničený kontext, který odráží pochopení obchodní domény.*

Tato část se zaměřuje na pokročilejší mikroslužeb, které implementujete, když potřebujete řešit složité subsystémy nebo mikroslužeb odvozené ze znalostí doménových odborníků s neustále se měnícími obchodními pravidly. Vzory architektury použité v této části jsou založeny na přístupech návrhu řízeného doménou (DDD) a segregátem odpovědnosti příkazů a dotazů (CQRS), jak je znázorněno na obrázku 7-1.

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Diagram porovnání externí a vnitřní vzory architektury.":::
Rozdíl mezi externí architekturou: vzory mikroslužeb, brány rozhraní API, odolná komunikace, pub/sub atd.
:::image-end:::

**Obrázek 7-1**. Externí architektura mikroslužeb versus vzory interní architektury pro každou mikroslužbu

Většina technik pro mikroslužby řízené daty, například jak implementovat službu ASP.NET core web api nebo jak vystavit metadata Swagger s Swashbuckle nebo NSwag, jsou také použitelné pro pokročilejší mikroslužby implementované interně s Vzory DDD. Tato část je rozšíření předchozí části, protože většina postupů vysvětlených dříve platí také zde nebo pro jakýkoli druh mikroslužeb.

Tato část nejprve obsahuje podrobnosti o zjednodušené CQRS vzory používané v eShopOnContainers referenční aplikace. Později získáte přehled o technikách DDD, které vám umožní najít běžné vzory, které můžete znovu použít ve svých aplikacích.

DDD je velké téma s bohatou sadou zdrojů pro učení. Můžete začít s knihami, jako [je doména-Driven Design](https://domainlanguage.com/ddd/) Eric Evans a další materiály od Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, a mnoho dalších Odborníků DDD / CQRS. Ale ze všeho nejvíc se musíte pokusit naučit, jak aplikovat Techniky DDD z rozhovorů, whiteboarding, a doména modelování zasedání s odborníky ve vaší konkrétní obchodní oblasti.

#### <a name="additional-resources"></a>Další zdroje

##### <a name="ddd-domain-driven-design"></a>DDD (návrh řízený doménou)

- **Eric Evans. Jazyk domény** \
  <https://domainlanguage.com/>

- **Martin Fowler. Návrh řízený doménou** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmyho Bogarda. Posílení vaší domény: základní nátěr** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>DDD knihy

- **Eric Evans. Návrh řízený doménou: Řešení složitosti v srdci softwaru** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans. Odkaz na návrh založený na doméně: Definice a souhrny vzorů** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon, to je můj zástupce. Implementace návrhu řízeného doménou** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon, to je můj zástupce. Destilovaný návrh řízený doménou** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson. Použití návrhu a vzorů řízených doménou** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Cesar de la Torre. N-vrstvené architektura orientované na doménu s rozhraním .NET** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram a Floyd Marinescu. Návrh řízený doménou rychle** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, Nick Tune - vzory, principy a postupy návrhu řízeného doménou** \
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a>Školení DDD

- **Julie Lermanová a Steve Smith. Základy návrhu řízeného doménou** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Předchozí](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[další](apply-simplified-microservice-cqrs-ddd-patterns.md)
