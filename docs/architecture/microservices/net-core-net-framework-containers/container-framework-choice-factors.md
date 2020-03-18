---
title: Rozhodovací tabulka. Rozhraní .NET, které se mají použít pro Docker
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Tabulka rozhodnutí, rozhraní .NET, které se mají použít pro Docker
ms.date: 09/11/2018
ms.openlocfilehash: 8ffe2b7bc0bee976d3a63b274994dbcc8aef0c61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628316"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabulka rozhodnutí: Rozhraní .NET Framework, která se mají použít pro Docker

Následující tabulka rozhodnutí shrnuje, zda se má použít rozhraní .NET Framework nebo .NET Core. Nezapomeňte, že pro linuxové kontejnery potřebujete hostitele Dockeru založeného na Linuxu (virtuální počítače nebo servery) a že pro kontejnery Windows Jsou potřeba hostitelé Dockeru na základě Windows Serveru (virtuální počítače nebo servery).

> [!IMPORTANT]
> Vývojové počítače poběží jeden hostitel Dockeru, linux nebo windows. Související mikroslužby, které chcete spustit a otestovat společně v jednom řešení bude muset běžet na stejné platformě kontejneru.

| Architektura / typ aplikace | Linuxové kontejnery | Kontejnery Windows |
|-------------------------|------------------|--------------------|
| Mikroslužby na kontejnerech | .NET Core | .NET Core |
| Monolitická aplikace | .NET Core | .NET Framework <br/> .NET Core |
| Nejlepší výkon a škálovatelnost ve své třídě | .NET Core | .NET Core |
| Migrace starší aplikace windows serveru ("brown-field") do kontejnerů | -- | .NET Framework |
| Vývoj nových kontejnerů ("zelená pole") | .NET Core | .NET Core |
| Jádro ASP.NET | .NET Core | Jádro .NET (doporučeno) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, webové rozhraní API 2 a webové formuláře) | -- | .NET Framework |
| SignalR služby | Verze .NET Core 2.1 nebo vyšší | .NET Framework <br/> Verze .NET Core 2.1 nebo vyšší |
| WCF, WF a další starší architektury | WCF v jádru .NET (pouze klientská knihovna) | .NET Framework <br/> WCF v jádru .NET (pouze klientská knihovna) |
| Spotřeba služeb Azure | .NET Core <br/> (nakonec většina služeb Azure bude poskytovat klientské sady SDK pro .NET Core) | .NET Framework <br/> .NET Core <br/> (nakonec většina služeb Azure bude poskytovat klientské sady SDK pro .NET Core) |

>[!div class="step-by-step"]
>[Předchozí](net-framework-container-scenarios.md)
>[další](net-container-os-targets.md)
