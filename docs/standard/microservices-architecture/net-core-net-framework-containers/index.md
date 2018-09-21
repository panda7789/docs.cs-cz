---
title: Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 9abff2614e4022408a069be25440196111db19ab
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46489874"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="e645a-103">Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="e645a-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="e645a-104">Existují dvě podporované architektury pro vytváření na straně serveru kontejnerizovaných aplikací Dockeru s .NET: [rozhraní .NET Framework a .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="e645a-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="e645a-105">Mají mnoho součástí platformy .NET a kód můžete sdílet mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="e645a-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="e645a-106">Existují však základní rozdíly mezi nimi a rozhraní, které použijete, bude záviset na co chcete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="e645a-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="e645a-107">Tato část obsahuje pokyny, kdy zvolit každého rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e645a-107">This section provides guidance on when to choose each framework.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e645a-108">[Předchozí](../container-docker-introduction/docker-containers-images-registries.md)
[další](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="e645a-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
