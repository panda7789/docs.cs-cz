---
title: Zpracování částečného selhání
description: Zjistěte, jak pro zpracování částečného selhání bez výpadku. Mikroslužby nemusí být plně funkční, ale stále může být schopen provádět některé užitečné práce.
ms.date: 10/16/2018
ms.openlocfilehash: a667ad2e1456db7b5846023de27d3797dad58731
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640099"
---
# <a name="handle-partial-failure"></a>Zpracování částečného selhání

V distribuovaných systémech, jako je aplikace založená na mikroslužbách je všudypřítomnou riziko částečného selhání. Například jeden mikroslužeb nebo kontejnerů může selhat nebo nemusí být možné reagovat na krátkou dobu, nebo jeden virtuální počítač nebo server může dojít k chybě. Od klientů a služeb jsou samostatné procesy, služba nemusí být schopné reagovat včas na žádost klienta. Služba může být přetížená a odpovídá velmi pomalu do požadavků nebo nemusí být dostupný na krátkou dobu jednoduše z důvodu problémů se sítí.

Představte si třeba stránka Podrobnosti objednávky z aplikaci eShopOnContainers ukázkovou aplikaci. Pokud řazení mikroslužba přestane reagovat při pokusu uživatele o odešlete odbejdnávku, chybnou implementací procesu klientů (webová aplikace MVC) – například, pokud kód klienta chtěli použít synchronní RPC bez časového limitu, bude blokovaná vlákna Čekání na odpověď. Kromě vytvoření nepříjemné zkušenosti, každý reagovat používá nebo blokuje vlákno a vlákna jsou extrémně cennou ve vysoce škálovatelných aplikací. Pokud existují mnoho blokovaná vlákna, nakonec modulu runtime aplikace můžete zjistit nedostatek podprocesů. V takovém případě může přestat aplikace globálně reagovat místo jen částečně reagovat, jak ukazuje obrázek 8-1.

![Diagram znázorňující předchozím odstavci](./media/image1.png)

**Obrázek 8-1**. Částečně neúspěšné z důvodu závislosti, které ovlivňují dostupnost služeb vlákna

V případě velkých aplikací založených na mikroslužbách může být rozšířena jakékoli částečného selhání, zejména v případě, že většina interakce interní mikroslužeb je založen na synchronní volání HTTP (což se považuje za proti vzor). Představte si systém, která bude přijímat miliony příchozí volání za den. Pokud váš systém má chybný návrh, který je založen na dlouhé řetězce synchronní volání HTTP, může vést k mnoha milionů víc odchozích hovorů (Předpokládejme poměr 1:4) k desítkám interní mikroslužeb jako synchronní závislosti těchto příchozí volání. Tato situace se zobrazí v 8 obrázek-2, zejména závislost \#3.

![Nesprávný návrhu pro webové aplikace mikroslužeb, který závisí na řetězci závislosti na jiných mikroslužeb](./media/image2.png)

**Obrázek 8-2**. Dopad s při nesprávné návrhu s dlouhé řetězce požadavků protokolu HTTP

Občasné selhání je zaručeno, že v systému distribuované a založené na cloudu, i v případě, že všechny závislosti, samotný má skvělé dostupnosti. Je fakt, které je potřeba zvážit.

Pokud není navrhovat a implementovat techniky k zajištění odolnosti proti chybám, může být rozšířena i malá výpadky. Jako příklad způsobí 50 závislosti každý s 99,99 % dostupnost několik hodin výpadků každý měsíc z důvodu tohoto efektu Zvlnění. Když závislost mikroslužeb selže při zpracovávání požadavků, které selhání můžete rychle saturate všechna vlákna žádosti k dispozici v jednotlivých služeb a chybách u aplikací celou aplikaci.

![Částečné selhání může být přísně doplněné zřetězené závislosti](./media/image3.png)

**Obrázek 8-3**. Pomocí mikroslužeb s dlouhé řetězce o synchronních voláních HTTP částečného selhání

Chcete-li minimalizovat potíže, v části [asynchronní mikroslužeb integrace vynutit na mikroslužbách autonomie](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy), tento průvodce doporučuje použít asynchronní komunikaci mezi interní mikroslužeb.

Kromě toho je nezbytné, navrhnout vaše mikroslužeb a klientských aplikací pro zpracování částečného selhání – to znamená, vytvářet odolné mikroslužeb a klientské aplikace.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](partial-failure-strategies.md)
