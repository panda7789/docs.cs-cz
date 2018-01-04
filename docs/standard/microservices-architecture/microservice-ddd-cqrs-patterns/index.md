---
title: "Boji se složitost firmy v Mikroslužbu s DDD a CQRS vzorky"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Boji se složitost firmy v Mikroslužbu s DDD a CQRS vzorky"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 45f29a8d19e49685f864b7ca83e466ceb1f73a62
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Boji se složitost firmy v Mikroslužbu s DDD a CQRS vzorky

*Návrh modelu domény pro každou mikroslužbu nebo ohraničenou kontext, který se vztahuje k pochopení obchodní domény.*

Tato část se zaměřuje na pokročilejší mikroslužeb, který implementujete, když potřebujete řešení komplexních subsystémy nebo mikroslužeb odvozené od znalosti odborníků domény s proměnlivých obchodní pravidla. Architektura vzory použít v této části jsou založené na základě domény návrhu (DDD) a přístupy k příkazu a dotaz odpovědnost oddělení (CQRS), jak ukazuje následující obrázek 9-1.

![](./media/image1.png)

**Obrázek 9-1**. Architektura externí mikroslužbu versus vzory interní architekturu pro každý mikroslužbu

Většina techniky pro data řízené mikroslužeb, jako je například implementaci služby webového rozhraní API ASP.NET Core nebo jak vystavit metadata Swagger s Swashbuckle, je však také pro pokročilejší mikroslužeb implementuje interně pomocí DDD vzory. Tato část je rozšířením předchozích sekcí, protože většina postupy popsané dříve platí také zde nebo pro jakýkoli druh mikroslužby.

Tato část obsahuje podrobnosti nejprve zjednodušené CQRS vzory použitou v eShopOnContainers odkaz na aplikaci. Později zobrazí se přehled DDD techniky, které vám umožní najít běžných vzorů, které můžete opakovaně použít ve svých aplikacích.

DDD je velké téma s bohatou sadu prostředků pro učení. Můžete spustit pomocí books jako [Domain-Driven návrhu](https://domainlanguage.com/ddd/) zařízení Erica Evans a další materiály z Vaughn Vernon, Jimmy Nilsson, Gregu Young, Udi Dahan, Jimmy Bogard a mnoho dalších DDD nebo CQRS odborníky. Ale většina vše, co je potřeba k vyzkoušení se dozvíte, jak použít techniky DDD z konverzace, whiteboarding a modelování relace s odborníky ve vaší doméně konkrétní obchodní domény.

#### <a name="additional-resources"></a>Další zdroje

##### <a name="ddd-domain-driven-design"></a>DDD (návrh řízené domény)

-   **Zařízení Evans Erica. Jazyk domény**
    [*http://domainlanguage.com/*](http://domainlanguage.com/)

-   **Martin Fowler. Domény řízené návrhu**
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)

-   **Jimmy Bogard. Posílení doménu: Základy**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a>DDD knihy

-   **Zařízení Evans Erica. Řízené domény návrhu: Boji se složitostí při vysílat softwaru**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Zařízení Evans Erica. Odkaz na základě domény návrhu: Definice a souhrny vzor**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

-   **Vaughn Vernon. Implementace návrhu řízené domény**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Vaughn Vernon. Domény řízené návrhu destilovaná**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

-   **Jimmy Nilsson. Použití řízené domény návrhu a vzory**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

-   **Cesaru členka Torre. Průvodce vrstvený N architektura orientovaná na doméně s .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

-   **Opisek Avram a Floyd Marinescu. Domény řízené návrhu rychle**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

DDD školení

-   **Julie Lerman a Steve Smith. Základy návrhu řízené domény**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)


>[!div class="step-by-step"]
[Předchozí] (.. / multi-container-microservice-net-applications/background-tasks-with-ihostedservice.md) [Další] (apply-simplified-microservice-cqrs-ddd-patterns.md)
