---
title: Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 9abff2614e4022408a069be25440196111db19ab
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45990918"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="a2b6e-103">Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="a2b6e-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="a2b6e-104">Existují dvě podporované architektury pro vytváření na straně serveru kontejnerizovaných aplikací Dockeru s .NET: [rozhraní .NET Framework a .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="a2b6e-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="a2b6e-105">Mají mnoho součástí platformy .NET a kód můžete sdílet mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="a2b6e-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="a2b6e-106">Existují však základní rozdíly mezi nimi a rozhraní, které použijete, bude záviset na co chcete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="a2b6e-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="a2b6e-107">Tato část obsahuje pokyny, kdy zvolit každého rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a2b6e-107">This section provides guidance on when to choose each framework.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a2b6e-108">[Předchozí](../container-docker-introduction/docker-containers-images-registries.md)
[další](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="a2b6e-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
