---
title: Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 0f6689468eda1dd1b12c24927e650b2b01381274
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104439"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="6df1e-103">Volba mezi .NET Core a rozhraní .NET Framework pro Docker kontejnery</span><span class="sxs-lookup"><span data-stu-id="6df1e-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="6df1e-104">Existují dvě podporované implementace pro vytváření serverové kontejnerizované Docker aplikací pomocí .NET: [rozhraní .NET Framework](https://www.microsoft.com/net/download/framework) a [.NET Core](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="6df1e-104">There are two supported implementations for building server-side containerized Docker applications with .NET: [.NET Framework](https://www.microsoft.com/net/download/framework) and [.NET Core](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="6df1e-105">Sdílejí mnoho součásti rozhraní .NET standardní a kód můžete sdílet mezi dva.</span><span class="sxs-lookup"><span data-stu-id="6df1e-105">They share many .NET Standard components, and you can share code across the two.</span></span> <span data-ttu-id="6df1e-106">Existují však základní rozdíly mezi nimi a implementace, které použijete, bude záviset na co chcete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="6df1e-106">However, there are fundamental differences between them, and which implementation you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="6df1e-107">Tato část obsahuje pokyny, když vyberte každou implementaci.</span><span class="sxs-lookup"><span data-stu-id="6df1e-107">This section provides guidance on when to choose each implementation.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="6df1e-108">[Předchozí](../container-docker-introduction/docker-containers-images-registries.md)
[další](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="6df1e-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
