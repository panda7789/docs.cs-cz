---
title: Zpracování částečného selhání
description: Přečtěte si, jak řádně zpracovat částečné chyby. Mikroslužba nemusí být plně funkční, ale je možné, že je stále možné provést některé užitečné práce.
ms.date: 10/16/2018
ms.openlocfilehash: f00e5349df74b543deb6ac941c751cb130b3837c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733004"
---
# <a name="handle-partial-failure"></a>Zpracovat částečnou chybu

V distribuovaných systémech, jako jsou aplikace založené na mikroslužbách, existuje stále přítomné riziko částečného selhání. Jedna mikroslužba nebo kontejner může například selhat nebo nemusí být k dispozici, aby mohla reagovat po krátkou dobu, nebo může dojít k selhání jednoho virtuálního počítače nebo serveru. Vzhledem k tomu, že klienti a služby jsou samostatné procesy, nemusí být služba schopná reagovat včas na požadavky klienta. Služba může být přetížená a reaguje velmi pomalu na požadavky nebo může být v důsledku problémů se sítí nepřístupná po krátkou dobu.

Můžete například zvážit stránku podrobnosti objednávky z ukázkové aplikace eShopOnContainers. Pokud mikroslužba řazení nereaguje, když se uživatel pokusí odeslat objednávku, špatná implementace klientského procesu (webová aplikace MVC) – například pokud kód klienta používá synchronní službu RPCSS bez časového limitu, by neomezená vlákna byla neomezená. čeká se na odpověď. Kromě vytvoření špatného uživatelského prostředí nereagují při čekání na zpracování nebo blokování vlákna a vlákna jsou v vysoce škálovatelných aplikacích extrémně cenná. Pokud je k dispozici mnoho blokovaných vláken, modul runtime aplikace může být mimo vlákna. V takovém případě může aplikace namísto pouze částečně nereagujících reagovat, a to jak je znázorněno na obrázku 8-1.

![Diagram znázorňující částečné chyby](./media/handle-partial-failure/partial-failures-diagram.png)

**Obrázek 8-1**. Částečné selhání kvůli závislostem, které mají vliv na dostupnost vlákna služby

V rozsáhlých aplikacích založených na mikroslužbách může být jakékoli částečné selhání rozšířeno, zejména pokud je většina interních interakcí mikroslužeb založená na synchronních voláních HTTP (což se považuje za antipattern). Zamyslete se nad systémem, který přijímá miliony příchozích hovorů za den. Pokud má váš systém špatný návrh, který je založený na dlouhých řetězech synchronních volání HTTP, může výsledkem těchto příchozích volání být mnoho dalších milionů odchozích volání (Předpokládejme, že se jedná o poměr 1:4) až desítky interních mikroslužeb jako synchronních závislostí. Tato situace je znázorněna na obrázku 8-2, zejména závislost \#3, která začíná řetězcem, volání #4 závislostí. které volání #5.

![Diagram znázorňující více distribuovaných závislostí.](./media/handle-partial-failure/multiple-distributed-dependencies.png)

**Obrázek 8-2**. Dopad nesprávného návrhu, který nabízí dlouhé řetězce požadavků HTTP

Občasné selhání je zaručené u distribuovaného a cloudového systému, a to i v případě, že každá závislá závislost má skvělou dostupnost. Je to fakt, že je potřeba vzít v úvahu.

Pokud nenavrhnete a neimplementujete techniky pro zajištění odolnosti proti chybám, může být i malé výpadky. Příklad: 50 závislosti každé s 99,99% dostupnosti by vedlo k několika hodinám výpadků v každém měsíci z důvodu tohoto efektu Ripple. V případě selhání závislosti mikroslužeb při zpracování vysokého objemu požadavků může tato chyba rychle navýšit všechna dostupná vlákna žádostí v každé službě a selhání celé aplikace.

![Diagram znázorňující částečné selhání v mikroslužbách.](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

**Obrázek 8-3**. Částečná selhání dodaná mikroslužby s dlouhými řetězy synchronních volání HTTP

Aby se tento problém minimalizoval, v části [asynchronní integrace mikroslužeb vynutila autonomii](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy)mikroslužby. Tato příručka vám pomůže použít asynchronní komunikaci mezi interními mikroslužbami.

Kromě toho je důležité, abyste navrhli své mikroslužby a klientské aplikace pro zpracování částečných selhání – to znamená vytvořit odolné mikroslužby a klientské aplikace.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](partial-failure-strategies.md)
