---
title: Zvládnutí firemní složitosti v mikroslužbě pomocí vzorů DDD a CQRS
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Naučte se řešit komplexní obchodní scénáře použití vzorů DDD a CQRS
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: f17acd6765de96bf8cec28c4e212733822fa0b73
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611104"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Řešit firemní složitosti v Mikroslužbě pomocí vzorů DDD a CQRS

*Návrh modelem domény pro jednotlivé mikroslužby nebo ohraničená kontextu, který se zobrazuje přehled o obchodní domény.*

Tato část se zaměřuje na pokročilejší mikroslužeb, které lze implementovat budete muset řešit komplexní subsystémy nebo mikroslužeb odvozené ze znalostí odborníky na domény s neustále se měnící obchodní pravidla. Tyto architektury vzory se dají použít v této části jsou založené na návrhu řízeného doménou (DDD) a přístupy k příkazu a model dělení zodpovědnosti dotazů (CQRS), jak je znázorněno na obrázku 7-1.

![Rozdíl mezi externí architektury: mikroslužeb vzory, brány rozhraní API, odolné komunikace, publikování a odběr, atd. a interní architekturu: data driven/CRUD vzorů DDD, vkládání závislostí, více knihoven, atd.](./media/image1.png)

**Obrázek 7 – 1**. Architekturu mikroslužeb externí a interní architekturu vzorů u jednotlivých mikroslužeb

Většina techniky pro mikroslužby, jako je například implementace služby webového rozhraní API ASP.NET Core nebo jak vystavit metadata Swagger s Swashbuckle nebo službou NSwag, na základě dat je však také lze použít na pokročilejší mikroslužeb implementována interně pomocí Vzorů DDD. Tato část je rozšířením v předchozích částech, protože většina údajů je vysvětleno výše platí také zde nebo pro jakýkoli druh mikroslužeb.

V této části nejprve poskytuje podrobné informace o jednodušší vzorů CQRS používaných v aplikaci eShopOnContainers odkaz na aplikaci. Později získáte přehled o DDD techniky, které vám umožní najít běžné vzory, které můžete znovu použít ve svých aplikacích.

DDD je velké téma s širokou škálu materiálů. Můžete začít s knihy stejně jako [Domain-Driven Design](https://domainlanguage.com/ddd/) Eric Evans a další materiály od Vaughn Vernon Jimmy Nilsson, Grega Younga, Udi Dahan, Jimmy Bogard a mnoha dalšími experty DDD a CQRS. Ale většinu z vás všechny nutné pokusí zjistěte, jak použít DDD techniky z konverzace, využití tabulí a modelování semináře s odborníky ve vaší doméně konkrétní obchodní domény.

#### <a name="additional-resources"></a>Další zdroje

##### <a name="ddd-domain-driven-design"></a>DDD (návrhem řízeným doménou)

- **Eric Evans. Jazyk domény** \
  <https://domainlanguage.com/>

- **Martina Fowlera. Domain-Driven Design** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy Bogard. Posílení vaší domény: Základy** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>DDD knihy

- **Eric Evans. Návrhy řízené doménou: Použití složitosti srdce softwaru** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans. Reference pro návrhy řízené doménou. Definice a souhrny vzor** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon. Implementace návrhu řízeného doménou** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon. Destilované návrhem řízeným doménou** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson. Použití návrhu řízeného doménou a vzory** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **De la Torre Cesarovi. Průvodce N vrstvami architektura orientovaná na doméně s využitím .NET** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram a Floyd Marinescu. Řízené doménou návrh rychle** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, Nick ladění – vzory, zásady a postupy při návrhu řízeného doménou** \
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a>DDD školení

- **Julie Lerman a Steve Smith. Základy návrhu řízeného doménou** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Předchozí](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[další](apply-simplified-microservice-cqrs-ddd-patterns.md)
