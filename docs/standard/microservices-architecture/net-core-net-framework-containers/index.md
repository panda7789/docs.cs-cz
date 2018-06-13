---
title: Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: b483214e7bd039a71ae642aa26e69d63222af8ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580124"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="758db-103">Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery</span><span class="sxs-lookup"><span data-stu-id="758db-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="758db-104">Existují dvě podporované implementace pro vytváření serverové kontejnerizované Docker aplikací pomocí .NET: [rozhraní .NET Framework](https://www.microsoft.com/net/download/framework) a [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="758db-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="758db-105">Sdílejí mnoho součásti rozhraní .NET standardní a kód můžete sdílet mezi dva.</span><span class="sxs-lookup"><span data-stu-id="758db-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="758db-106">Existují však základní rozdíly mezi nimi a implementace, které použijete, bude záviset na co chcete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="758db-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="758db-107">Tato část obsahuje pokyny, když vyberte každou implementaci.</span><span class="sxs-lookup"><span data-stu-id="758db-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="758db-108">[Předchozí] (.. / container-docker-introduction/docker-containers-images-registries.md) [Další] (Obecné guidance.md)</span><span class="sxs-lookup"><span data-stu-id="758db-108">[Previous] (../container-docker-introduction/docker-containers-images-registries.md) [Next] (general-guidance.md)</span></span>
