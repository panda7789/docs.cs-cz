---
title: Škálování aplikací nativních pro Cloud
description: Škálování aplikací v cloudu pomocí služby Azure Kubernetes a Azure Functions tak, aby splňovala požadavky uživatelů v úsporném režimu.
ms.date: 04/13/2020
ms.openlocfilehash: 91d925778e9dfcf8a1ec2486fe8961037409f207
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199935"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="acd80-103">Škálování aplikací nativních pro Cloud</span><span class="sxs-lookup"><span data-stu-id="acd80-103">Scaling cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="acd80-104">Jednou z nejčastěji nabídnutá výhod přechodu do hostitelského prostředí v cloudu je škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="acd80-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="acd80-105">Škálovatelnost nebo schopnost aplikace přijímat dodatečné uživatelské zatížení, aniž by došlo k narušení výkonu pro každého uživatele.</span><span class="sxs-lookup"><span data-stu-id="acd80-105">Scalability, or the ability for an application to accept additional user load without compromising performance for each user.</span></span> <span data-ttu-id="acd80-106">Nejčastěji se dosahuje tím, že se aplikace rozbalí do malých částí, které je možné dodávat podle libovolných prostředků, které potřebují.</span><span class="sxs-lookup"><span data-stu-id="acd80-106">It's most often achieved by breaking up an application into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="acd80-107">Dodavatelé cloudu umožňují obrovské škálovatelnost kdykoli a kdekoli na světě.</span><span class="sxs-lookup"><span data-stu-id="acd80-107">Cloud vendors enable massive scalability anytime and anywhere in the world.</span></span>

 <span data-ttu-id="acd80-108">V této kapitole se zabýváme technologiemi, které umožňují škálování cloudových aplikací pro splnění požadavků uživatelů.</span><span class="sxs-lookup"><span data-stu-id="acd80-108">In this chapter, we discuss technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="acd80-109">Patří k nim tyto technologie:</span><span class="sxs-lookup"><span data-stu-id="acd80-109">These technologies include:</span></span>

- <span data-ttu-id="acd80-110">Containers</span><span class="sxs-lookup"><span data-stu-id="acd80-110">Containers</span></span>
- <span data-ttu-id="acd80-111">Orchestrátory</span><span class="sxs-lookup"><span data-stu-id="acd80-111">Orchestrators</span></span>
- <span data-ttu-id="acd80-112">Bezserverová architektura</span><span class="sxs-lookup"><span data-stu-id="acd80-112">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="acd80-113">[Předchozí](centralized-configuration.md)
>[Další](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="acd80-113">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
