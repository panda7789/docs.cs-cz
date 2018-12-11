---
title: Zpracování částečného selhání
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Zpracování částečného selhání
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 94239fc30292760b2bb28849f8c6ab72c7ceb33d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144725"
---
# <a name="handling-partial-failure"></a>Zpracování částečného selhání

V distribuovaných systémech, jako je aplikace založená na mikroslužbách je všudypřítomnou riziko částečného selhání. Například jeden mikroslužeb nebo kontejnerů může selhat nebo nemusí být možné reagovat na krátkou dobu, nebo jeden virtuální počítač nebo server může dojít k chybě. Od klientů a služeb jsou samostatné procesy, služba nemusí být schopné reagovat včas na žádost klienta. Služba může být přetížená a odpovídá velmi pomalu do požadavků nebo nemusí být dostupný na krátkou dobu jednoduše z důvodu problémů se sítí.

Představte si třeba stránka Podrobnosti objednávky z aplikaci eShopOnContainers ukázkovou aplikaci. Pokud řazení mikroslužba přestane reagovat při pokusu uživatele o odešlete odbejdnávku, chybnou implementací procesu klientů (webová aplikace MVC) – například, pokud kód klienta chtěli použít synchronní RPC bez časového limitu, bude blokovaná vlákna Čekání na odpověď. Kromě vytvoření nepříjemné zkušenosti, každý reagovat používá nebo blokuje vlákno a vlákna jsou extrémně cennou ve vysoce škálovatelných aplikací. Pokud existují mnoho blokovaná vlákna, nakonec modulu runtime aplikace můžete zjistit nedostatek podprocesů. V takovém případě může přestat aplikace globálně reagovat místo jen částečně reagovat, jak je vidět v obrázek 10-1.

![](./media/image1.png)

**Obrázek 10-1**. Částečně neúspěšné z důvodu závislosti, které ovlivňují dostupnost služeb vlákna

V případě velkých aplikací založených na mikroslužbách může být rozšířena jakékoli částečného selhání, zejména v případě, že většina interakce interní mikroslužeb je založen na synchronní volání HTTP (což se považuje za proti vzor). Představte si systém, která bude přijímat miliony příchozí volání za den. Pokud váš systém má chybný návrh, který je založen na dlouhé řetězce synchronní volání HTTP, tato příchozí volání může způsobit další miliony odchozích volání (Předpokládejme poměr 1:4) k desítkám interní mikroslužeb jako synchronní závislosti. Tato situace se zobrazí v 10 obrázek-2, zejména závislost \#3.

![](./media/image2.png)

**Obrázek 10-2**. Dopad s při nesprávné návrhu s dlouhé řetězce požadavků protokolu HTTP

Občasné selhání je zaručeno, že v systému distribuované a založené na cloudu, i v případě, že všechny závislosti, samotný má skvělé dostupnosti. Je fakt, které je potřeba zvážit.

Pokud není navrhovat a implementovat techniky k zajištění odolnosti proti chybám, může být rozšířena i malá výpadky. Jako příklad způsobí 50 závislosti každý s 99,99 % dostupnost několik hodin výpadků každý měsíc z důvodu tohoto efektu Zvlnění. Když závislost mikroslužeb selže při zpracovávání požadavků, které selhání můžete rychle saturate všechna vlákna žádosti k dispozici v jednotlivých služeb a chybách u aplikací celou aplikaci.

![](./media/image3.png)

**Obrázek 10-3**. Pomocí mikroslužeb s dlouhé řetězce o synchronních voláních HTTP částečného selhání

Chcete-li minimalizovat potíže, v části "*asynchronní mikroslužeb integrace vynutit na mikroslužbách autonomie*" (v kapitole architektury), tyto pokyny doporučuje použít asynchronní komunikaci napříč interní mikroslužeb. 

Kromě toho je nezbytné, navrhnout vaše mikroslužeb a klientských aplikací pro zpracování částečného selhání – to znamená, vytvářet odolné mikroslužeb a klientské aplikace.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](partial-failure-strategies.md)