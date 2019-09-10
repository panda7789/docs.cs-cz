---
title: Volba mezi .NET Core a .NET Framework pro kontejnery Docker
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Volba mezi .NET Core a .NET Framework pro kontejnery Docker
ms.date: 09/11/2018
ms.openlocfilehash: b01aaf25f4071e8e4a07905a12ec9dd0d89a738d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849270"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="5a196-103">Volba mezi .NET Core a .NET Framework pro kontejnery Docker</span><span class="sxs-lookup"><span data-stu-id="5a196-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="5a196-104">Existují dvě podporované architektury pro vytváření kontejnerových aplikací Docker na straně serveru pomocí .NET: [.NET Framework a .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="5a196-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="5a196-105">Sdílejí mnoho komponent platformy .NET a můžete sdílet kód mezi dvěma.</span><span class="sxs-lookup"><span data-stu-id="5a196-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="5a196-106">Mezi nimi ale existují zásadní rozdíly a používané rozhraní bude záviset na tom, co chcete provést.</span><span class="sxs-lookup"><span data-stu-id="5a196-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="5a196-107">V této části najdete pokyny, kdy zvolit jednotlivé architektury.</span><span class="sxs-lookup"><span data-stu-id="5a196-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5a196-108">[Předchozí](../container-docker-introduction/docker-containers-images-registries.md)Další
>[](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="5a196-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>
