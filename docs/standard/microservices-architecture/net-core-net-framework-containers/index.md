---
title: Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru
ms.date: 09/11/2018
ms.openlocfilehash: 771d23cf4610e5778f0a144386754ce10d6ae144
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639022"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="55eb9-103">Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="55eb9-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="55eb9-104">Existují dvě podporované architektury pro vytváření na straně serveru kontejnerizovaných aplikací Dockeru s .NET: [rozhraní .NET Framework a .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="55eb9-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="55eb9-105">Mají mnoho součástí platformy .NET a kód můžete sdílet mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="55eb9-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="55eb9-106">Existují však základní rozdíly mezi nimi a rozhraní, které použijete, bude záviset na co chcete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="55eb9-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="55eb9-107">Tato část obsahuje pokyny, kdy zvolit každého rozhraní.</span><span class="sxs-lookup"><span data-stu-id="55eb9-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="55eb9-108">[Předchozí](../container-docker-introduction/docker-containers-images-registries.md)
>[další](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="55eb9-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
