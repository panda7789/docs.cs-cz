---
title: Volba mezi rozhraním .NET Core a rozhraníM .NET Framework pro kontejnery Dockeru
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Volba mezi rozhraním .NET Core a rozhraníM .NET Framework pro kontejnery Dockeru
ms.date: 09/11/2018
ms.openlocfilehash: b01aaf25f4071e8e4a07905a12ec9dd0d89a738d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70849270"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="ce027-103">Volba mezi rozhraním .NET Core a rozhraníM .NET Framework pro kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="ce027-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="ce027-104">Existují dva podporované architektury pro vytváření kontejnerizovaných aplikací Dockeru na straně serveru s rozhraním .NET: [Rozhraní .NET Framework a .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="ce027-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="ce027-105">Sdílejí mnoho komponent platformy .NET a můžete sdílet kód mezi dvěma.</span><span class="sxs-lookup"><span data-stu-id="ce027-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="ce027-106">Existují však zásadní rozdíly mezi nimi a rámec, který používáte, bude záviset na tom, co chcete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="ce027-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="ce027-107">Tato část obsahuje pokyny, kdy zvolit jednotlivé rámce.</span><span class="sxs-lookup"><span data-stu-id="ce027-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ce027-108">[Předchozí](../container-docker-introduction/docker-containers-images-registries.md)
>[další](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="ce027-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
