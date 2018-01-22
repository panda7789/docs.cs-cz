---
title: "Vytvořte odolné služby, které jsou připravené pro cloud. Zapojení přechodných chyb v cloudu"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Vytvořte odolné služby, které jsou připravené pro cloud. Zapojení přechodných chyb v cloudu"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aaf1ef968600a56d91267c6c12efa90d99446dd7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>Vytvářet odolné služby, které jsou připravené pro cloud: zapojení přechodných chyb v cloudu 

Odolnost proti chybám je možnost obnovení v případě selhání a i nadále fungovat. Odolnost proti chybám není o zamezení selhání, ale přijímá fakt, že dojde k selhání a pak reagovat na ně způsobem, který zabraňuje výpadku nebo ztráty dat. Cílem odolnosti je pro návrat aplikace plně funkčního stavu po selhání.

Když minimálně implementuje model na základě softwaru odolnosti, nikoli model založené na hardwaru, je aplikace připravená pro cloud. Cloudové aplikace musí použít částečný chyby, ke kterým dojde jistě. Budete muset navrhnout nebo částečně Refaktorovat vaší aplikace, pokud chcete zajistit odolnost vůči očekávané částečné selhání. Ho by se měly navrhovat zvládnout částečné selhání jako přechodný síťový výpadky a uzly nebo chybám v cloudu virtuálních počítačů. I kontejnery přesouvá na jiný uzel v clusteru služby orchestrator může způsobit občasné krátké chyby v aplikaci.

## <a name="handling-partial-failure"></a>Částečné selhání zpracování

V aplikaci založené na cloudu je všudypřítomné riziko částečné selhání. Například jeden web instance nebo kontejner může selhat nebo může být k dispozici nebo po krátkou dobu reagovat. Nebo může dojít k selhání jednoho virtuálního počítače nebo serveru.

Protože služby a klienti jsou samostatné procesy, nemusí být schopné reagovat včas na žádost klienta služby. Služby mohou být přetížené a reagovat na požadavky velmi pomalu nebo ho jednoduše možná není přístupný po krátkou dobu z důvodu problémů se sítí.

Představte si třeba monolitický aplikace .NET, který přistupuje k databázi v databázi SQL Azure. Pokud databáze Azure SQL nebo na jiné služby třetích stran reagovat pro brief čas (Azure SQL database může přesunout do jiného uzlu nebo server a být reagovat na několik sekund), když se uživatel pokusí o provádět žádné akce, může dojít k selhání aplikace a zobra w výjimku na velmi stejnou chvíli.

Informace o podobném scénáři může dojít v aplikaci, která využívá služeb HTTP. V síti nebo samotnou službu nemusí být k dispozici v cloudu během krátké, přechodné chybě.

Odolné aplikace zobrazený v obrázek 4 – 9 by měla implementovat techniky, jako je "opakování s exponenciálního omezení rychlosti" umožnit aplikaci příležitost pro zpracování přechodných chyb v prostředky. "Okruh moduly dělení" měli použít také v aplikacích. Jistič zastaví aplikace v pokusu o přístup k prostředku, pokud je ve skutečnosti dlouhodobé selhání. Pomocí jistič aplikace zabraňuje vzniku rozptylových odepření služby na sebe sama.

![Částečné selhání zpracovávaných opakování s exponenciálního omezení rychlosti](./media/image9.png)

> **Obrázek 4 – 9.** Částečné selhání zpracovávaných opakování s exponenciálního omezení rychlosti

Tyto postupy můžete použít v HTTP prostředky i v databázi prostředků. Obrázek 4 – 9 aplikace je založena na vrstvě 3 architekturu, proto musíte těchto postupů na úrovni služby (HTTP) a na úrovni vrstvy dat (TCP). V monolitický aplikaci, která používá jenom jedna aplikace vrstvu kromě databáze (žádná další služby nebo mikroslužeb) zpracování přechodných chyb na úrovni připojení databáze může být dost. V tomto scénáři je požadovaná obvykle jenom konkrétní konfigurací připojení k databázi.

Při implementaci odolné komunikaci, která přístup k databázi, v závislosti na verzi rozhraní .NET, které používáte, může být velmi jednoduché (například [s Entity Framework 6 nebo novější](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx), bude stačit konfigurace připojení k databázi). Nebo možná budete muset používat další knihovny jako [přechodné chyby zpracování bloku aplikace](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx) (u starších verzí rozhraní .NET), nebo i implementovat vlastní knihovny.

Při implementaci HTTP opakování a moduly dělení okruh, doporučení pro .NET je používat [Polly](https://github.com/App-vNext/Polly) knihovny, která cílí na rozhraní .NET 4.0, .NET 4.5 a standardní 1.1 rozhraní .NET, včetně podpory .NET Core.

Pokud chcete dozvědět, jak implementovat strategie pro zpracování částečné selhání v cloudu, najdete v následujících odkazů.

### <a name="additional-resources"></a>Další zdroje

-   **Implementace odolné komunikace pro zpracování částečné selhání**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies)

-   **Entity Framework, připojení odolnost proti chybám a zkuste to znovu logiku (verze 6 nebo novější)**

    [https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)

-   **Blok přechodná chyba zpracování aplikace**

<!-- -->

-   [https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)

-   **Knihovna Polly pro odolné komunikaci pomocí protokolu HTTP**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
[Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[další](modernize-your-apps-with-monitoring-and-telemetry.md)
