---
title: Vytvoření složeného uživatelského rozhraní založeného na mikroslužbách, včetně visual uživatelského rozhraní tvaru a rozložení generovaných různými mikroslužbami
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Vytvoření složeného uživatelského rozhraní založeného na mikroslužbách, včetně visual uživatelského rozhraní tvaru a rozložení generovaných různými mikroslužbami
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 79b63c376d25725b2bcb6c16cdb4d06e107d5c07
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45641271"
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Vytvoření složeného uživatelského rozhraní založeného na mikroslužbách, včetně visual uživatelského rozhraní tvaru a rozložení generovaných různými mikroslužbami

Architektura Mikroslužeb často začíná zpracování dat a logiky na straně serveru. Pokročilejší přístup je však Navrhněte svou aplikaci, kterou uživatelského rozhraní založeného na mikroslužbách také. To znamená s složeného uživatelského rozhraní vytvářené mikroslužeb, namísto nutnosti mikroslužeb na serveru a jenom monolitické klientskou aplikaci využívající mikroslužby. Tento přístup může být mikroslužeb, které vytváříte s logiky a vizuální reprezentace.

Obrázek 4-20 ukazuje jednodušší přístup právě využívání mikroslužeb z monolitického klientské aplikace. Samozřejmě může mít službu ASP.NET MVC mezi HTML a JavaScript. Na obrázku je zjednodušení, která označuje, že máte jednoho klienta (monolitické) uživatelského rozhraní využívání mikroslužeb, která soustředit jen na logiku a data a ne na obrazec uživatelského rozhraní (HTML a JavaScript).

![](./media/image20.png)

**Obrázek 4-20**. Monolitické aplikace uživatelského rozhraní využívání back-end mikroslužeb

Složeného uživatelského rozhraní naproti tomu přesně vygeneruje a sestává z mikroslužeb, sami. Některé z mikroslužeb jednotka visual tvar konkrétní oblasti uživatelského rozhraní. Klíčovým rozdílem je, že máte součásti uživatelského rozhraní klienta (například třídy TS) založené na šablonách a ViewModel data strukturovat UI pro tyto šablony pochází z jednotlivých mikroslužeb.

V době spuštění klienta aplikace jednotlivých součástí uživatelského rozhraní klienta (například třídy TypeScript) zaregistruje ve službě infrastruktury mikroslužeb, která je schopný poskytnout modely ViewModels v daném scénáři. Pokud mikroslužbách změní tvar, změní se také uživatelského rozhraní.

Obrázek 4 – 21 ukazuje verzi tohoto složeného uživatelského přístupu. Toto je zjednodušený, protože může mít jiné mikroslužeb, která Dáváme dohromady podrobné části podle různých technik – záleží na tom, jestli vytváříte tradičními webovými přístup (technologie ASP.NET MVC) nebo SPA (jednostránkové aplikace).

![](./media/image21.png)

**Obrázek 4 – 21**. Příklad složeného uživatelského rozhraní aplikace ve tvaru pomocí back-end mikroslužeb

Každá z těchto mikroslužeb kompozici uživatelského rozhraní bude podobný malý Brána rozhraní API. Ale v tomto případě každý je zodpovědná za malý oblasti uživatelského rozhraní.

Komplexní přístup uživatelského rozhraní, který řídíte mikroslužeb může být ještě náročnější nebo méně Ano, v závislosti na tom, jaká technologie uživatelského rozhraní používáte. Pro instanci, nebudete používat stejné techniky pro vytváření tradičních webové aplikace, který používáte pro vytváření SPA nebo pro nativní mobilní aplikace (stejně jako při vývoji aplikace Xamarin, které mohou být ještě náročnější pro tento přístup).

[Aplikaci eShopOnContainers](https://aka.ms/MicroservicesArchitecture) ukázková aplikace používá monolitického přístupu uživatelského rozhraní z několika důvodů. Nejprve je úvodem do mikroslužeb a kontejnerů. Složeného uživatelského rozhraní je složitější, ale také vyžaduje další složitosti po návrh a vývoj uživatelského rozhraní. Za druhé aplikaci eShopOnContainers také poskytuje nativní mobilní aplikace založené na Xamarinu, což by mohlo způsobit nepoužitelnost je složitější na straně klienta C\# straně.

Ale doporučujeme vám použít následující odkazy na další informace o složeného uživatelského rozhraní v závislosti na mikroslužbách.

## <a name="additional-resources"></a>Další zdroje

-   **Složeného uživatelského rozhraní pomocí technologie ASP.NET (zejména na seminář)**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga. Monolitické front-endu v architektuře Mikroslužeb**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti. Tajný kód lépe kompozici uživatelského rozhraní**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic. Včetně Front-End webové součásti do Mikroslužeb**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Správa front-endu v architektuře Mikroslužeb**\
    [*https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html*](https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Předchozí](microservices-addressability-service-registry.md)
[další](resilient-high-availability-microservices.md)
