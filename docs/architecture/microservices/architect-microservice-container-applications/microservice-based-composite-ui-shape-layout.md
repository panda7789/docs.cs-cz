---
title: Vytvoření složeného uživatelského rozhraní založeného na mikroslužbách
description: Architektura mikroslužeb není jenom pro back-end. Získejte náhled při jeho použití v front-endu.
ms.date: 09/20/2018
ms.openlocfilehash: 1861d3bb6e5d4a0226aa8f3f72a2e0d3e83be56f
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275738"
---
# <a name="creating-composite-ui-based-on-microservices"></a>Vytvoření složeného uživatelského rozhraní založeného na mikroslužbách

Architektura mikroslužeb často začíná zpracováním dat a logiky na straně serveru, ale v mnoha případech se uživatelské rozhraní pořád zpracovává jako monolitu. Pokročilejší přístup označovaný jako [mikro-endy](https://martinfowler.com/articles/micro-frontends.html)je však navrhovat uživatelské rozhraní aplikace založené i na mikroslužbách. To znamená, že mají složené uživatelské rozhraní vytvořené mikroslužbami, místo abyste měli mikroslužby na serveru a jenom klientská aplikace monolitické využívající mikroslužby. S tímto přístupem můžete mikroslužby, které sestavíte, dokončit jak pomocí logiky, tak i vizuální reprezentace.

Obrázek 4-20 ukazuje jednodušší přístup pouze k náročným mikroslužbám z klientské aplikace monolitické. Samozřejmě můžete mít ASP.NET službu MVC mezi vytvářením kódu HTML a JavaScriptu. Obrázek je zjednodušený, který zdůrazňuje, že máte jedno (monolitické) klientské uživatelské rozhraní náročné na mikroslužby, které se zaměřují jenom na logiku a data, a ne na tvar uživatelského rozhraní (HTML a JavaScript).

![Diagram aplikace uživatelského rozhraní monolitické, která se připojuje k mikroslužbám](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

**Obrázek 4-20**. Aplikace uživatelského rozhraní monolitické využívající back-end mikroslužby

Naproti tomu složené uživatelské rozhraní je přesně vygenerováno a tvořeno samotnými mikroslužbami. Některé mikroslužby na jednotce vizuální tvar určitých oblastí uživatelského rozhraní. Hlavním rozdílem je, že máte komponenty uživatelského rozhraní klienta (například třídy TypeScript) založené na šablonách a Data-Shaping-UI ViewModel pro tyto šablony pocházejí z každé mikroslužby.

V počátečním čase klientské aplikace se každá z komponent klientského uživatelského rozhraní (například třídy TypeScript) registruje s mikroslužbou infrastruktury schopnou poskytovat ViewModels pro daný scénář. Pokud mikroslužba změní tvar, uživatelské rozhraní se také změní.

Obrázek 4-21 ukazuje verzi tohoto složeného přístupu k uživatelskému rozhraní. To je zjednodušené, protože možná máte jiné mikroslužby, které agreguje podrobné části, které jsou založené na různých technikách. Záleží na tom, jestli vytváříte tradiční webový přístup (ASP.NET MVC), nebo na ZABEZPEČENou aplikaci (jednostránkové).

![Diagram složeného uživatelského rozhraní, který sestavil mnoho modelů zobrazení.](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

**Obrázek 4-21**. Příklad složené aplikace uživatelského rozhraní ve tvaru back-endové mikroslužby

Každé z těchto mikroslužeb kompozice uživatelského rozhraní se podobá malé bráně API. Ale v tomto případě je každý z nich zodpovědný za malou oblast uživatelského rozhraní.

Přístup k složenému uživatelskému rozhraní, který ovládá mikroslužby, může být náročnější nebo méně, a to v závislosti na tom, jaké technologie uživatelského rozhraní používáte. Nebudete například používat stejné techniky pro vytváření tradičních webových aplikací, které používáte pro vytváření zabezpečeného hesla nebo pro nativní mobilní aplikace (jako při vývoji aplikací pro Xamarin, které mohou být pro tento přístup náročnější).

Ukázková aplikace [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) používá přístup k uživatelskému rozhraní monolitické z několika důvodů. Nejprve se jedná o Úvod do mikroslužeb a kontejnerů. Složené uživatelské rozhraní je pokročilejší, ale také při navrhování a vývoji uživatelského rozhraní vyžaduje další složitost. Druhý eShopOnContainers také poskytuje nativní mobilní aplikaci založenou na Xamarin, která by byla složitější na straně klienta C\#.

Doporučujeme vám ale použít následující odkazy na Další informace o složeném uživatelském rozhraní založeném na mikroslužbách.

## <a name="additional-resources"></a>Další materiály a zdroje informací

- **Mikroslužby na front-endy (blog Novák Fowlera)**  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- **Micro front-endu (Michael Geers Web)**  
  <https://micro-frontends.org/>
  
- **Složené uživatelské rozhraní využívající ASP.NET (konkrétně Workshop)**  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- **Ruben Oostinga. Monolitické front-endové architektury mikroslužeb**  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- **Mauro Servienti. Tajný kód lepšího složení uživatelského rozhraní**  
  <https://particular.net/blog/secret-of-better-ui-composition>

- **Viktor Farcic. Zahrnutí front-endové webových součástí do mikroslužeb**  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- **Správa front-endu v architektuře mikroslužeb**  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
>[Předchozí](microservices-addressability-service-registry.md)
>[Další](resilient-high-availability-microservices.md)
