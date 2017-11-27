---
title: 210 - MessageThrottleExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ca08ea-c11c-4753-946e-98aa820f8711
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2d027f549e86095c732d0e60df3faded44a39fd2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="210---messagethrottleexceeded"></a><span data-ttu-id="5d985-102">210 - MessageThrottleExceeded</span><span class="sxs-lookup"><span data-stu-id="5d985-102">210 - MessageThrottleExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="5d985-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5d985-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d985-104">ID</span><span class="sxs-lookup"><span data-stu-id="5d985-104">ID</span></span>|<span data-ttu-id="5d985-105">210</span><span class="sxs-lookup"><span data-stu-id="5d985-105">210</span></span>|  
|<span data-ttu-id="5d985-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5d985-106">Keywords</span></span>|<span data-ttu-id="5d985-107">EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5d985-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5d985-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5d985-108">Level</span></span>|<span data-ttu-id="5d985-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="5d985-109">Warning</span></span>|  
|<span data-ttu-id="5d985-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5d985-110">Channel</span></span>|<span data-ttu-id="5d985-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="5d985-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5d985-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5d985-112">Description</span></span>  
 <span data-ttu-id="5d985-113">Tato událost je vygenerované, pokud jeden tři hlavní služby se překročila omezení.</span><span class="sxs-lookup"><span data-stu-id="5d985-113">This event is emitted when one of the three main service throttles have been exceeded.</span></span> <span data-ttu-id="5d985-114">Všimněte si, že tato událost je jenom vygenerované při počátečním překročení limitu omezení.</span><span class="sxs-lookup"><span data-stu-id="5d985-114">Note that this event is only emitted when the throttle limit is initially exceeded.</span></span> <span data-ttu-id="5d985-115">Například pokud limit omezovače pro souběžných volání 10, 11 souběžných volání výsledky v `MessageThrottleExceeded` událostí.</span><span class="sxs-lookup"><span data-stu-id="5d985-115">For example, if the throttle limit for concurrent calls is 10, the 11th concurrent call results in a `MessageThrottleExceeded` event.</span></span> <span data-ttu-id="5d985-116">12. volání nevede jinou událost.</span><span class="sxs-lookup"><span data-stu-id="5d985-116">The 12th call does not result in another event.</span></span> <span data-ttu-id="5d985-117">Kromě toho abyste se vyhnuli datového proudu aktivní událostí, aktivity, která bude umístěn kolem limit nevede jinou událost.</span><span class="sxs-lookup"><span data-stu-id="5d985-117">Additionally, to avoid a noisy event stream, activity that hovers around the limit does not result in another event.</span></span> <span data-ttu-id="5d985-118">V tomto příkladu je-li dokončit několik volání pak existují 9 souběžných volání.</span><span class="sxs-lookup"><span data-stu-id="5d985-118">In this example, if a couple of calls complete then there are 9 concurrent calls.</span></span> <span data-ttu-id="5d985-119">Pokud následně dva další volání mohou, aktuální hodnota je znovu 11.</span><span class="sxs-lookup"><span data-stu-id="5d985-119">If subsequently two more calls come in, the current value is again 11.</span></span> <span data-ttu-id="5d985-120">Výsledkem není jinou událost.</span><span class="sxs-lookup"><span data-stu-id="5d985-120">This does not result in another event.</span></span> <span data-ttu-id="5d985-121">Když aktuální hodnota klesne na 70 procent limit omezovače jsou vydávány jinou událost označující, že má zpomalení aktivity.</span><span class="sxs-lookup"><span data-stu-id="5d985-121">When the current value falls to 70 percent of the throttle limit a different event is emitted that indicates that the activity has slowed.</span></span> <span data-ttu-id="5d985-122">Budoucí aktivity, která překračuje limit výsledků v jiném `MessageThrottleExceeded` se vygenerované události.</span><span class="sxs-lookup"><span data-stu-id="5d985-122">Future activity that exceeds the limit results in another `MessageThrottleExceeded` event being emitted.</span></span> <span data-ttu-id="5d985-123">V tomto příkladu, pokud množství souběžných volání spadá do 7 a poté opět dosáhne 11 a druhý `MessageThrottleExceeded` je vygenerované události.</span><span class="sxs-lookup"><span data-stu-id="5d985-123">In this example, if the amount of concurrent calls falls to 7 and then again reaches 11 and another `MessageThrottleExceeded` event is emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5d985-124">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5d985-124">Message</span></span>  
 <span data-ttu-id="5d985-125">Bylo dosaženo limitu omezení '%1' z '%2'.</span><span class="sxs-lookup"><span data-stu-id="5d985-125">The '%1' throttle limit of '%2' was hit.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5d985-126">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5d985-126">Details</span></span>  
  
|<span data-ttu-id="5d985-127">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5d985-127">Data Item Name</span></span>|<span data-ttu-id="5d985-128">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="5d985-128">Data Item Type</span></span>|<span data-ttu-id="5d985-129">Popis</span><span class="sxs-lookup"><span data-stu-id="5d985-129">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5d985-130">Název omezení.</span><span class="sxs-lookup"><span data-stu-id="5d985-130">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="5d985-131">Název omezení, která byla překročena.</span><span class="sxs-lookup"><span data-stu-id="5d985-131">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="5d985-132">Buď `MaxConcurrentCalls`, `MaxConcurrentInstances`, nebo `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="5d985-132">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="5d985-133">Limit</span><span class="sxs-lookup"><span data-stu-id="5d985-133">Limit</span></span>|`xs:long`|<span data-ttu-id="5d985-134">Aktuálně nakonfigurovaný limit omezení.</span><span class="sxs-lookup"><span data-stu-id="5d985-134">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="5d985-135">HostReference</span><span class="sxs-lookup"><span data-stu-id="5d985-135">HostReference</span></span>|`xs:string`|<span data-ttu-id="5d985-136">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="5d985-136">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5d985-137">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="5d985-137">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5d985-138">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="5d985-138">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5d985-139">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5d985-139">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5d985-140">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5d985-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
