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
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="0c1e6-104">Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery</span><span class="sxs-lookup"><span data-stu-id="0c1e6-104">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="0c1e6-105">Existují dvě podporované implementace pro vytváření serverové kontejnerizované Docker aplikací pomocí .NET: [rozhraní .NET Framework](https://www.microsoft.com/net/download/framework) a [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="0c1e6-105">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="0c1e6-106">Sdílejí mnoho součásti rozhraní .NET standardní a kód můžete sdílet mezi dva.</span><span class="sxs-lookup"><span data-stu-id="0c1e6-106">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="0c1e6-107">Existují však základní rozdíly mezi nimi a implementace, které použijete, bude záviset na co chcete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="0c1e6-107">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="0c1e6-108">Tato část obsahuje pokyny, když vyberte každou implementaci.</span><span class="sxs-lookup"><span data-stu-id="0c1e6-108">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0c1e6-109">[Předchozí] (.. / container-docker-introduction/docker-containers-images-registries.md) [Další] (Obecné guidance.md)</span><span class="sxs-lookup"><span data-stu-id="0c1e6-109">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
