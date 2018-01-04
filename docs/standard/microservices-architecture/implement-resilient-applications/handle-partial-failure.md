---
title: "Částečné selhání zpracování"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Částečné selhání zpracování"
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
ms.openlocfilehash: 0b03a5d341dbaadde302692ed0ed236ff3423e63
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="handling-partial-failure"></a>Částečné selhání zpracování

V distribuovaných systémech jako aplikace založené na mikroslužeb existuje všudypřítomné nebezpečí částečné selhání. Pro instanci jediný mikroslužbu nebo kontejner může selhat nebo nemusí být k dispozici po krátkou dobu reagovat, nebo jeden virtuální počítač nebo server může dojít k chybě. Vzhledem k tomu, že služby a klienti jsou samostatné procesy, nemusí být schopné reagovat včas na žádost klienta služby. Služba může být požadavky přetížené a reagování na velmi pomalu nebo nemusí být dostupný po krátkou dobu jednoduše z důvodu problémů se sítí.

Představte si třeba stránce s podrobnostmi o pořadí z eShopOnContainers ukázkovou aplikaci. Pokud je řazení mikroslužbu reagovat při pokusu uživatele o odešlete odbejdnávku, chybný provádění procesu klienta (webová aplikace MVC) – například pokud kód klienta použili synchronní RPC s bez časového limitu – by po neomezenou dobu blokování vláken Čekání na odpověď. Kromě vytváření nepříjemné zkušenosti, každých reagovat čekání používá nebo blokuje vlákno a vláken jsou velmi cenné ve vysoce škálovatelné aplikace. Pokud je počet pozastavených vláken, nakonec běhu aplikace můžete spustit z vláken. V takovém případě může stát aplikace místo globálně reagovat jen částečně reagovat, jak je vidět v obrázek 10-1.

![](./media/image1.png)

**Obrázek 10-1**. Částečné selhání kvůli závislosti, které mít dopad na dostupnost služby přístup z více vláken

V rozsáhlé aplikace na základě mikroslužeb může být rozšířena jakákoli částečné chyba, hlavně v případě, že většina interní mikroslužeb interakce je založen na synchronní volání protokolu HTTP (které považuje za proti vzor). Vezměte v úvahu systému, která bude přijímat miliony příchozí volání za den. Pokud má váš systém chybný návrh, který je založen na dlouhé řetězy synchronní volání protokolu HTTP, tyto příchozí volání může vést v mnoha milionů další odchozí volání (Předpokládejme poměr 1:4) desítek interní mikroslužeb jako synchronní závislosti. Tato situace se zobrazí v 10 obrázek-2, zejména závislostí \#3.

![](./media/image2.png)

**Obrázek 10-2**. Dopad toho, že nesprávné návrh s funkcí dlouho řetězy požadavků HTTP

Občasné selhání je v podstatě zaručit v distribuované a cloud na bázi systému, i v případě, že všechny závislosti, samotné má vynikající dostupnosti. To by měl být faktů, které je třeba vzít v úvahu.

Pokud nemáte navrhnout a implementovat techniky k zajištění odolnosti proti chybám, může být rozšířena i malé výpadky způsobené nástrojem. Jako příklad by kvůli tomu ripple 50 závislosti každý s 99,99 % dostupnost způsobilo několik hodin výpadku každý měsíc. Když závislost mikroslužbu selže při zpracování k velkému počtu požadavků, které selhání můžete rychle saturate všechna vlákna požadavek k dispozici v jednotlivých služeb a havárií celou aplikaci.

![](./media/image3.png)

**Obrázek 10-3**. Částečné selhání doplněné mikroslužeb s dlouhou řetězy synchronní volání protokolu HTTP

Chcete-li minimalizovat tento problém, v části "*asynchronní mikroslužbu integrace vynutit nezávislé na mikroslužbu*" (v kapitole architektura), můžeme vám umožní používat asynchronní komunikaci mezi interní podporovat mikroslužeb. Stručně objasníme více v další části.

Kromě toho je důležité, navrhnout vaše mikroslužeb a klientské aplikace pro zpracování částečné selhání – to znamená, vytvářet odolné mikroslužeb a klientské aplikace.


>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (partial strategies.md selhání)
