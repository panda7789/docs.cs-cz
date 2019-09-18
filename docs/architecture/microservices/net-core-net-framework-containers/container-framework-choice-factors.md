---
title: Tabulka rozhodnutí Rozhraní .NET Framework, která se mají použít pro Docker
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Tabulka rozhodnutí, rozhraní .NET Framework, které se má použít pro Docker
ms.date: 09/11/2018
ms.openlocfilehash: 0087d80c2d949daf14e1edd773dd310f47c508a9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039669"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabulka rozhodnutí: Rozhraní .NET Framework, která se mají použít pro Docker

Následující rozhodovací tabulka shrnuje, jestli se má použít .NET Framework nebo .NET Core. Pamatujte na to, že pro kontejnery Linux potřebujete hostitele Docker (virtuální počítače nebo servery) založené na systému Linux a to pro kontejnery Windows, které potřebujete pro hostitele Docker (virtuální počítače nebo servery) založené na Windows serveru.

> [!IMPORTANT]
> Ve vývojových počítačích se spustí jeden hostitel Docker, buď Linux nebo Windows. Související mikroslužby, které chcete spustit a testovat společně v jednom řešení, je potřeba spustit na stejné platformě kontejneru.

| Architektura/typ aplikace | Kontejnery platformy Linux | Kontejnery Windows |
|-------------------------|------------------|--------------------|
| Mikroslužby na kontejnerech | .NET Core | .NET Core |
| Aplikace monolitické | .NET Core | .NET Framework <br/> .NET Core |
| Nejlepší výkon a škálovatelnost ve své třídě | .NET Core | .NET Core |
| Migrace do kontejnerů starší verze aplikace ("hnědá-Field") Windows serveru | -- | .NET Framework |
| Nový vývoj založený na kontejneru (zelená-Field) | .NET Core | .NET Core |
| ASP.NET Core | .NET Core | .NET Core (doporučeno) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, webové rozhraní API 2 a webové formuláře) | -- | .NET Framework |
| Služby Signal | Verze .NET Core 2,1 nebo vyšší | .NET Framework <br/> Verze .NET Core 2,1 nebo vyšší |
| WCF, WF a další starší verze platforem | WCF v .NET Core (jenom Klientská knihovna) | .NET Framework <br/> WCF v .NET Core (jenom Klientská knihovna) |
| Spotřeba služeb Azure | .NET Core <br/> (nakonec všechny služby Azure budou poskytovat klientské sady SDK pro .NET Core) | .NET Framework <br/> .NET Core <br/> (nakonec všechny služby Azure budou poskytovat klientské sady SDK pro .NET Core) |

>[!div class="step-by-step"]
>[Předchozí](net-framework-container-scenarios.md)Další
>[](net-container-os-targets.md)
