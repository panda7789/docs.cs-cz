---
title: Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: e71739b06275d4ee786d246004930d7b66fbc72b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019604"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="b602c-103">Volba mezi .NET Core a .NET Framework pro kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="b602c-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="b602c-104">Existují dvě podporované architektury pro vytváření na straně serveru kontejnerizovaných aplikací Dockeru s .NET: [rozhraní .NET Framework a .NET Core](https://www.microsoft.com/net/download).</span><span class="sxs-lookup"><span data-stu-id="b602c-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="b602c-105">Mají mnoho součástí platformy .NET a kód můžete sdílet mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="b602c-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="b602c-106">Existují však základní rozdíly mezi nimi a rozhraní, které použijete, bude záviset na co chcete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="b602c-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="b602c-107">Tato část obsahuje pokyny, kdy zvolit každého rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b602c-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b602c-108">[Předchozí](../container-docker-introduction/docker-containers-images-registries.md)
>[další](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="b602c-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>