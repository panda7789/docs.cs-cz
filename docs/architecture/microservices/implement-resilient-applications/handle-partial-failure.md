---
title: Zpracování částečného selhání
description: Zjistěte, jak řádně zpracovat částečné chyby. Mikroslužba nemusí být plně funkční, ale stále může být schopen provést některé užitečné práce.
ms.date: 10/16/2018
ms.openlocfilehash: f00e5349df74b543deb6ac941c751cb130b3837c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73733004"
---
# <a name="handle-partial-failure"></a>Zpracování částečné poruchy

V distribuovaných systémech, jako jsou aplikace založené na mikroslužbách, existuje stále přítomné riziko částečného selhání. Například jeden mikroslužbu/kontejner může selhat nebo nemusí být k dispozici reagovat na krátkou dobu, nebo jeden virtuální počítač nebo server může dojít k chybě. Vzhledem k tomu, že klienti a služby jsou samostatné procesy, služba nemusí být schopna včas reagovat na požadavek klienta. Služba může být přetížena a reagovat velmi pomalu na požadavky nebo jednoduše není přístupná na krátkou dobu z důvodu problémů se sítí.

Zvažte například stránku Podrobnosti objednávky z ukázkové aplikace eShopOnContainers. Pokud řazení mikroslužby nereaguje, když se uživatel pokusí odeslat objednávku, chybná implementace klientského procesu (webová aplikace MVC) – například pokud by kód klienta používal synchronní rpc bez časového omezení – by blokoval podprocesy po neomezenou dobu čeká na odpověď. Kromě vytvoření špatné uživatelské prostředí, každé nereagující čekání spotřebovává nebo blokuje vlákno a vlákna jsou velmi cenné ve vysoce škálovatelné aplikace. Pokud existuje mnoho blokovaných vláken, nakonec může dojít k běhu aplikace. V takovém případě aplikace může být globálně nereagující namísto jen částečně neodpovídá, jak je znázorněno na obrázku 8-1.

![Diagram zobrazující částečné chyby.](./media/handle-partial-failure/partial-failures-diagram.png)

**Obrázek 8-1**. Částečné chyby z důvodu závislostí, které mají vliv na dostupnost vlákna služby

Ve velké aplikace založené na mikroslužbách může být zesilována jakákoli částečná chyba, zejména pokud je většina interní interakce mikroslužeb založena na synchronních voláních HTTP (což je považováno za anti-pattern). Zamyslete se nad systémem, který přijímá miliony příchozích hovorů denně. Pokud váš systém má špatný návrh, který je založen na dlouhé řetězce synchronní volání HTTP, tyto příchozí volání může mít za následek mnoho dalších milionů odchozích volání (předpokládejme poměr 1:4) k desítkám interních mikroslužeb jako synchronní závislosti. Tato situace je znázorněna na obrázku \#8-2, zejména závislost 3, která spustí řetěz, volání závislosti #4. které #5 hovory.

![Diagram znázorňující více distribuovaných závislostí.](./media/handle-partial-failure/multiple-distributed-dependencies.png)

**Obrázek 8-2**. Dopad nesprávného návrhu s dlouhými řetězci požadavků HTTP

Občasné selhání je zaručeno v distribuovaném a cloudovém systému, i když každá závislost sama o sobě má vynikající dostupnost. Je to fakt, který musíš zvážit.

Pokud nenavrhujete a neimplementujete techniky k zajištění odolnosti proti chybám, mohou být zesíleny i malé prostoje. Například 50 závislostí s 99,99 % dostupnosti by mělo za následek několik hodin prostojů každý měsíc z důvodu tohoto dominový efekt. Pokud závislost mikroslužeb selže při zpracování velkého objemu požadavků, tato chyba může rychle nasytit všechna dostupná vlákna požadavků v každé službě a selhání celé aplikace.

![Diagram znázorňující částečné selhání zesílené v mikroslužbách.](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

**Obrázek 8-3**. Částečné selhání zesílené mikroslužbami s dlouhými řetězci synchronních volání HTTP

Chcete-li minimalizovat tento problém, v části [Asynchronní integrace mikroslužeb vynucují autonomii mikroslužeb](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy), tato příručka doporučuje používat asynchronní komunikaci napříč interní mikroslužby.

Kromě toho je nezbytné, abyste navrhli mikroslužeb a klientské aplikace pro zpracování částečných selhání – to znamená vytvořit odolné mikroslužby a klientské aplikace.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](partial-failure-strategies.md)
