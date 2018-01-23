---
title: "Vytváření složených uživatelského rozhraní založené na mikroslužeb, včetně visual tvar uživatelského rozhraní a rozložení generované více mikroslužeb"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Vytváření složených uživatelského rozhraní založené na mikroslužeb, včetně visual tvar uživatelského rozhraní a rozložení generované více mikroslužeb"
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
ms.openlocfilehash: 12b170e9d4c46fbb697f988596af6566d33099a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Vytváření složených uživatelského rozhraní založené na mikroslužeb, včetně visual tvar uživatelského rozhraní a rozložení generované více mikroslužeb

Architektura Mikroslužeb často začíná na straně serveru, zpracování dat a logiku. Pokročilejší přístup je však k návrhu aplikace uživatelského rozhraní založené na také mikroslužeb. To znamená, nutnosti složené uživatelského rozhraní vyprodukované mikroslužeb, místo nutnosti mikroslužeb na serveru a jenom se využívají mikroslužeb monolitický klientskou aplikaci. S tímto přístupem může být mikroslužeb při sestavování kompletní s logiku a vizuální reprezentace.

Obrázek 4-20 ukazuje jednodušší přístup z právě využívání mikroslužeb z monolitický klientské aplikace. Samozřejmě můžete mít služby ASP.NET MVC mezi generovala kód HTML a JavaScript. Na obrázku je zjednodušení, která označuje, že máte jednoho klienta (monolitický) uživatelského rozhraní využívání mikroslužeb, který právě soustředit na logiku a data a ne na tvar uživatelského rozhraní (HTML a JavaScript).

![](./media/image20.png)

**Obrázek 4-20**. Monolitický uživatelského rozhraní aplikace využívání mikroslužeb back-end

Složené uživatelského rozhraní je naopak přesněji vygeneruje a sestává z mikroslužeb sami. Některé mikroslužeb jednotky visual obrazec určitých oblastí uživatelského rozhraní. Klíčovým rozdílem je, že máte součásti uživatelského rozhraní klienta (například třídy TS) na základě šablon a ViewModel data shaping-uživatelského rozhraní pro tyto šablony pochází z každé mikroslužby.

V době spuštění klienta aplikace jednotlivých součástí uživatelského rozhraní klienta (například třídy TypeScript) registruje mikroslužbu infrastrukturu, která je schopný poskytnout ViewModels v daném scénáři. Pokud se změní mikroslužbu tvaru, uživatelské rozhraní se změní také.

Obrázek 4 – 21 se zobrazuje verze tohoto složeného přístupu uživatelského rozhraní. To je jednodušší, protože může mít jiné mikroslužeb, která jsou agregování podrobné části podle různých technik – závisí na tom, zda vytváříte tradiční webový přístup (technologie ASP.NET MVC) nebo SPA (jedné stránky aplikace).

![](./media/image21.png)

**Obrázek 4 – 21**. Příklad uživatelského rozhraní aplikace kompozitních tvaru podle mikroslužeb back-end

Každý z těchto mikroslužeb složení uživatelského rozhraní by podobná malé Brána rozhraní API. Ale v takovém případě každý je zodpovědná za malou oblast uživatelského rozhraní.

Složené koncepci uživatelského rozhraní, které vycházejí z mikroslužeb může být náročné, více nebo méně Ano, v závislosti na tom, jaké technologie uživatelského rozhraní používáte. Například nebude používat stejné postupy pro vytváření tradiční webové aplikace, které používáte pro vytváření SPA nebo pro nativní mobilní aplikace (stejně jako při vývoji aplikace Xamarin, na které může být náročné další pro tento přístup).

[EShopOnContainers](http://aka.ms/MicroservicesArchitecture) ukázková aplikace používá monolitický uživatelského rozhraní přístup z několika důvodů. Nejprve je Úvod do kontejnerů a mikroslužeb. Složené uživatelského rozhraní je složitější, ale také vyžaduje další složitosti při návrhu a vývoj uživatelského rozhraní. Za druhé eShopOnContainers také poskytuje nativní mobilní aplikace založené na Xamarinu, který by ji činilo složitější na straně klienta C\# straně.

Ale doporučujeme vám použít následující odkazy na další informace o složené uživatelského rozhraní založené na mikroslužeb.

## <a name="additional-resources"></a>Další zdroje

-   **Složené uživatelského rozhraní pomocí technologie ASP.NET (na konkrétní dílny)**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga. Monolitický front-endu v architektuře Mikroslužeb**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti. Tajný klíč lepší složení uživatelského rozhraní**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic. Včetně front-endu webové komponenty do Mikroslužeb**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Správa front-endu v architektuře Mikroslužeb**\
    [*http://Allegro.tech/2016/03/Managing-frontend-in-the-microservices-Architecture.HTML*](http://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Předchozí] (microservices-addressability-service-registry.md) [Další] (resilient-high-availability-microservices.md)
