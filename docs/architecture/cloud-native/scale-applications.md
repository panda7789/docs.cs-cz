---
title: Škálování aplikací nativních pro Cloud
description: Škálování aplikací v cloudu pomocí služby Azure Kubernetes a Azure Functions tak, aby splňovala požadavky uživatelů v úsporném režimu.
ms.date: 09/23/2019
ms.openlocfilehash: 5f4aac5804c5498c331787083c943a6ea1b69748
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184825"
---
# <a name="scaling-cloud-native-applications"></a><span data-ttu-id="8debd-103">Škálování aplikací nativních pro Cloud</span><span class="sxs-lookup"><span data-stu-id="8debd-103">Scaling cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="8debd-104">Jednou z nejčastěji nabídnutá výhod přechodu do hostitelského prostředí v cloudu je škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="8debd-104">One of the most-often touted advantages of moving to a cloud hosting environment is scalability.</span></span> <span data-ttu-id="8debd-105">V rámci škálovatelnosti nebo schopnosti aplikace přijmout další uživatelské zatížení bez nepatřičného snížení výkonu pro každého uživatele se často dosahuje tím, že se aplikace rozbalí do malých částí, které mohou být dány libovolnými prostředky, které potřebují.</span><span class="sxs-lookup"><span data-stu-id="8debd-105">Scalability, or the ability for an application to accept additional user load without unduly degrading performance for each user, is most often achieved by breaking up applications into small pieces that can each be given whatever resources they require.</span></span> <span data-ttu-id="8debd-106">V této kapitole zavádíme technologie, které umožňují škálování cloudových aplikací pro splnění požadavků uživatelů.</span><span class="sxs-lookup"><span data-stu-id="8debd-106">In this chapter, we introduce the technologies that enable cloud-native applications to scale to meet user demand.</span></span> <span data-ttu-id="8debd-107">Mezi tyto technologie patří:</span><span class="sxs-lookup"><span data-stu-id="8debd-107">These technologies include:</span></span>

- <span data-ttu-id="8debd-108">Kontejnery</span><span class="sxs-lookup"><span data-stu-id="8debd-108">Containers</span></span>
- <span data-ttu-id="8debd-109">Orchestrátorů</span><span class="sxs-lookup"><span data-stu-id="8debd-109">Orchestrators</span></span>
- <span data-ttu-id="8debd-110">Výpočetní prostředí bez serveru</span><span class="sxs-lookup"><span data-stu-id="8debd-110">Serverless computing</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8debd-111">[Předchozí](centralized-configuration.md)
>[Další](leverage-containers-orchestrators.md)</span><span class="sxs-lookup"><span data-stu-id="8debd-111">[Previous](centralized-configuration.md)
[Next](leverage-containers-orchestrators.md)</span></span>
