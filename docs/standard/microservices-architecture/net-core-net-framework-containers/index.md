---
title: Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery
keywords: Docker, Mikroslužeb, ASP.NET, kontejneru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 60d21de06262a14f9be6a1a5ce80edf15ddf1b59
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a>Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery

Existují dvě podporované implementace pro vytváření serverové kontejnerizované Docker aplikací pomocí .NET: [rozhraní .NET Framework](https://www.microsoft.com/net/download/framework) a [.NET Core](https://www.microsoft.com/net/download/core). Sdílejí mnoho součásti rozhraní .NET standardní a kód můžete sdílet mezi dva. Existují však základní rozdíly mezi nimi a implementace, které použijete, bude záviset na co chcete dosáhnout. Tato část obsahuje pokyny, když vyberte každou implementaci.


>[!div class="step-by-step"]
[Předchozí] (.. / container-docker-introduction/docker-containers-images-registries.md) [Další] (Obecné guidance.md)
