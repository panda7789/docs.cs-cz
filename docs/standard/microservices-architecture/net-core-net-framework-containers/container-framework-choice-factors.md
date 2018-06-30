---
title: Rozhodovací tabulky. Rozhraní .NET Framework pro Docker
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Rozhodovací tabulky, rozhraní .NET Framework pro Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: c45fbb9f26e6cd315e1b623ba2c79d5d038a6919
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105297"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Rozhodovací tabulky: rozhraní .NET Framework pro Docker

Následující možnost shrne ohledně použití rozhraní .NET Framework nebo .NET Core a systému Windows nebo Linux kontejnerů. Nezapomeňte, že pro Linux kontejnery, potřebujete hostitelů Docker založených na Linuxu (virtuální počítače nebo servery) a že pro kontejnery Windows potřebujete Windows Server na základě hostitelů Docker (virtuální počítače nebo servery).

Existuje několik funkcí vaší aplikace, které ovlivnit vaše rozhodnutí. Při rozhodování, měli byste zvážit důležitosti těchto funkcí.

> [!IMPORTANT]
> Vaše počítače vývoj spustí jednoho hostitele Docker, Linux nebo Windows. Související mikroslužeb, který chcete spustit a otestovat společně v jednom řešení bude nutné ke spuštění na stejnou platformu kontejneru.

* Architektura zvoleného aplikace je **Mikroslužeb kontejnerům**.
    - Svou volbu implementace rozhraní .NET by měl být *.NET Core*.
    - Váš výběr platformy kontejner může být buď *Linux kontejnery* nebo *Windows kontejnery*.
* Je zvoleného Architektura aplikace **monolitický aplikace**.
    - Svou volbu implementace rozhraní .NET může být buď *.NET Core* nebo *rozhraní .NET Framework*.
    - Pokud jste vybrali *.NET Core*, váš výběr platformy kontejner může být buď *Linux kontejnery* nebo *Windows kontejnery*.
    - Pokud jste vybrali *rozhraní .NET Framework*, musí být váš výběr platformy kontejneru *Windows kontejnery*.
* Je vaše aplikace **vývoj nových na základě kontejneru ("zelená pole")**.
    - Svou volbu implementace rozhraní .NET by měl být *.NET Core*.
    - Váš výběr platformy kontejner může být buď *Linux kontejnery* nebo *Windows kontejnery*.
* Je vaše aplikace **migrace systému Windows Server starší verze aplikace ("menších pole") do kontejnerů**
    - Vaše volba implementace rozhraní .NET je *rozhraní .NET Framework* podle závislostí architektury.
    - Váš výběr platformy kontejneru musí být *Windows kontejnery* z důvodu závislosti rozhraní .NET Framework.
* Cílem aplikace je **třídy nejlepší výkon a škálovatelnost**.
    - Svou volbu implementace rozhraní .NET by měl být *.NET Core*.
    - Váš výběr platformy kontejner může být buď *Linux kontejnery* nebo *Windows kontejnery*.
* Jste vytvořili aplikaci pomocí **ASP.NET Core**.
    - Svou volbu implementace rozhraní .NET by měl být *.NET Core*.
    - Můžete použít *rozhraní .NET Framework* implementace, pokud máte další závislosti architektury.
    - Pokud jste vybrali *.NET Core*, váš výběr platformy kontejner může být buď *Linux kontejnery* nebo *Windows kontejnery*.
    - Pokud jste vybrali *rozhraní .NET Framework*, musí být váš výběr platformy kontejneru *Windows kontejnery*.
* Jste vytvořili aplikaci pomocí **ASP.NET 4 (MVC 5, webové rozhraní API 2 a webových formulářů)**.
    - Vaše volba implementace rozhraní .NET je *rozhraní .NET Framework* podle závislostí architektury.
    - Váš výběr platformy kontejneru musí být *Windows kontejnery* z důvodu závislosti rozhraní .NET Framework.
* Vaše aplikace používá **služby SignalR**.
    - Svou volbu implementace rozhraní .NET může být *rozhraní .NET Framework*, nebo *.NET Core 2.1 (po vydání) nebo novější*.
    - Váš výběr platformy kontejneru musí být *Windows kontejnery* Pokud jste zvolili implementace SignalR v rozhraní .NET Framework.
    - Váš výběr platformy kontejner může být kontejnery Linux nebo Windows kontejnery, pokud jste zvolili SignalR implementace v rozhraní .NET Core 2.1 nebo novější (po vydání).  
    - Když **služby SignalR** spustit na *.NET Core*, můžete použít *Linux kontejnery nebo Windows kontejnerů*.
* Vaše aplikace používá **WCF, WF a dalších starších verzí rozhraní**.
    - Vaše volba implementace rozhraní .NET je *rozhraní .NET Framework*, nebo *.NET Core (v plán pro budoucí použití)*.
    - Váš výběr platformy kontejneru musí být *Windows kontejnery* z důvodu závislosti rozhraní .NET Framework.
* Vaše aplikace zahrnuje **spotřeba Azure services**.
    - Vaše volba implementace rozhraní .NET je *rozhraní .NET Framework*, nebo *.NET Core (služby nakonec všechny Azure bude poskytovat klientské sady SDK pro .NET Core)*.
    - Váš výběr platformy kontejneru musí být *Windows kontejnery* Pokud používáte rozhraní API klienta rozhraní .NET Framework.
    - Pokud používáte rozhraní API, které jsou k dispozici pro klienta *.NET Core*, můžete také zvolit *Linux kontejnery a kontejnery Windows*.

>[!div class="step-by-step"]
[Předchozí](net-framework-container-scenarios.md)
[další](net-container-os-targets.md)
