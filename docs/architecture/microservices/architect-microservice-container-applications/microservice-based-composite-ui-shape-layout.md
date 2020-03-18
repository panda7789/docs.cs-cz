---
title: Vytváření složeného ui na základě mikroslužeb
description: Architektura mikroslužeb není pouze pro back-end. Získejte náhled na jeho použití v přední části.
ms.date: 09/20/2018
ms.openlocfilehash: 1861d3bb6e5d4a0226aa8f3f72a2e0d3e83be56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72275738"
---
# <a name="creating-composite-ui-based-on-microservices"></a>Vytváření složeného ui na základě mikroslužeb

Architektura mikroslužeb často začíná zpracování dat na straně serveru a logiky, ale v mnoha případech ui je stále zpracována jako monolit. Pokročilejší přístup, nazývaný mikro [front-endy](https://martinfowler.com/articles/micro-frontends.html), je však navrhnout vaše aplikace ui na základě mikroslužeb také. To znamená, že s složené ui vyrobené mikroslužeb, namísto mikroslužeb na serveru a pouze monolitické klientské aplikace náročné mikroslužeb. S tímto přístupem mikroslužeb, které vytvoříte může být kompletní s logikou a vizuální reprezentace.

Obrázek 4-20 ukazuje jednodušší přístup právě náročné mikroslužeb z monolitické klientské aplikace. Samozřejmě, můžete mít ASP.NET Služby MVC mezi výrobou HTML a JavaScript. Obrázek je zjednodušení, které zdůrazňuje, že máte jeden (monolitické) klientské ui náročné mikroslužeb, které se zaměřují pouze na logiku a data, a nikoli na obrazec ui (HTML a JavaScript).

![Diagram monolitické aplikace ui připojení k mikroslužbám.](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

**Obrázek 4-20**. Monolitické aplikace ui náročné back-endové mikroslužby

Naproti tomu složené uzpložené umělá vi je přesně generována a skládá mikroslužeb sami. Některé mikroslužeb řídit vizuální tvar konkrétní oblasti ui. Klíčovým rozdílem je, že máte komponenty uživatelského prostředí klienta (například třídy TypeScript) založené na šablonách a model zobrazení ui pro tyto šablony pro tyto šablony pochází z každé mikroslužby.

Při spuštění klientské aplikace se každá komponenta klientského ui (například třídy jazyka TypeScript) zaregistruje pomocí mikroslužby infrastruktury, která je schopna poskytnout ViewModels pro daný scénář. Pokud mikroslužba změní tvar, změní se také ui.

Obrázek 4-21 ukazuje verzi tohoto přístupu složené houževnatého. To je zjednodušeno, protože může mít jiné mikroslužby, které agregují granulované části, které jsou založeny na různých technikách. Záleží na tom, zda vytváříte tradiční webový přístup (ASP.NET MVC) nebo SPA (jednostránková aplikace).

![Diagram složeného ui tvořeného mnoha modely zobrazení.](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

**Obrázek 4-21**. Příklad složené aplikace unesprávné back-endovými mikroslužbami

Každá z těchto mikroslužeb složení ui by být podobné malé brány rozhraní API. Ale v tomto případě je každý z nich zodpovědný za malou oblast ui.

Přístup kombinovaného ui, který je řízen mikroslužeb může být náročnější nebo méně, v závislosti na tom, jaké technologie ui, které používáte. Například nebudete používat stejné techniky pro vytváření tradiční webové aplikace, které používáte pro vytváření SPA nebo pro nativní mobilní aplikace (jako při vývoji aplikací Xamarin, což může být pro tento přístup náročnější).

Ukázková aplikace [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) používá monolitický přístup ui z několika důvodů. Nejprve je úvod do mikroslužeb a kontejnerů. Složené ui je pokročilejší, ale také vyžaduje další složitost při navrhování a vývoji uj. Za druhé, eShopOnContainers také poskytuje nativní mobilní aplikace založená na Xamarin, což by bylo složitější na straně klienta C.\#

Doporučujeme však použít následující odkazy, abyste se dozvěděli další informace o složeném uzpořeného ui na základě mikroslužeb.

## <a name="additional-resources"></a>Další zdroje

- **Micro Frontends (Martin Fowler blog)**  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- **Micro Frontends (Michael Geers stránky)**  
  <https://micro-frontends.org/>
  
- **Kompozitní ui pomocí ASP.NET (Particular's Workshop)**  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- **Ruben Oostinga. Monolitický frontend v architektuře mikroslužeb**  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- **Mauro Servienti. Tajemství lepší složení ui**  
  <https://particular.net/blog/secret-of-better-ui-composition>

- **Viktor Farcic. Zahrnutí webových komponent front-endu do mikroslužeb**  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- **Správa front-endu v architektuře mikroslužeb**  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
>[Předchozí](microservices-addressability-service-registry.md)
>[další](resilient-high-availability-microservices.md)
