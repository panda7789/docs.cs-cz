---
title: "224 – MessageThrottleAtSeventyPercent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82bbbfd7-10d2-41fd-805d-2443b0c1b96b
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e2f96aea0df629c24eb9d795a4409cae6a9c9aa9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="224---messagethrottleatseventypercent"></a><span data-ttu-id="d6d83-102">224 – MessageThrottleAtSeventyPercent</span><span class="sxs-lookup"><span data-stu-id="d6d83-102">224 - MessageThrottleAtSeventyPercent</span></span>
## <a name="properties"></a><span data-ttu-id="d6d83-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d6d83-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d6d83-104">ID</span><span class="sxs-lookup"><span data-stu-id="d6d83-104">ID</span></span>|<span data-ttu-id="d6d83-105">224</span><span class="sxs-lookup"><span data-stu-id="d6d83-105">224</span></span>|  
|<span data-ttu-id="d6d83-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d6d83-106">Keywords</span></span>|<span data-ttu-id="d6d83-107">EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d6d83-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d6d83-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="d6d83-108">Level</span></span>|<span data-ttu-id="d6d83-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="d6d83-109">Warning</span></span>|  
|<span data-ttu-id="d6d83-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="d6d83-110">Channel</span></span>|<span data-ttu-id="d6d83-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="d6d83-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d6d83-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d6d83-112">Description</span></span>  
 <span data-ttu-id="d6d83-113">Pokud byla překročena jedním z omezení hlavní služby, `MessageThrottleExceeded` je vygenerované události.</span><span class="sxs-lookup"><span data-stu-id="d6d83-113">When one of the main service throttles has been exceeded, the `MessageThrottleExceeded` event is emitted.</span></span> <span data-ttu-id="d6d83-114">Když zpomalí Špička aktivity a aktuální hodnota omezení je na 70 procent aktuální limit pak tato událost je vygenerované.</span><span class="sxs-lookup"><span data-stu-id="d6d83-114">When the spike of activity slows and the current value of the throttle is at 70 percent of the current limit then this event is emitted.</span></span> <span data-ttu-id="d6d83-115">Všimněte si, že tato událost je jenom vygenerované po zpomalení jako aktivity.</span><span class="sxs-lookup"><span data-stu-id="d6d83-115">Note that this event is only emitted once as the activity is slowing.</span></span> <span data-ttu-id="d6d83-116">Pokud je aktuální hodnota bude umístěn na značce 70 procent, (například 70,69,70,71,70,69), pouze první výskyt 70 procent výsledky v události.</span><span class="sxs-lookup"><span data-stu-id="d6d83-116">If the current value hovers at the 70 percent mark, (for example, 70,69,70,71,70,69), only the first occurrence of 70 percent results in an event.</span></span> <span data-ttu-id="d6d83-117">Po této události je vygenerované, budoucí výskyt překročení omezení je omezit vést `MessageThrottleExceeded` událostí.</span><span class="sxs-lookup"><span data-stu-id="d6d83-117">After this event is emitted, future occurrences of exceeding the throttle's limit result in a `MessageThrottleExceeded` event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d6d83-118">Zpráva</span><span class="sxs-lookup"><span data-stu-id="d6d83-118">Message</span></span>  
 <span data-ttu-id="d6d83-119">Limit omezení "%1" (%2) je na 70 %%.</span><span class="sxs-lookup"><span data-stu-id="d6d83-119">The '%1' throttle limit of '%2' is at 70%%.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d6d83-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d6d83-120">Details</span></span>  
  
|<span data-ttu-id="d6d83-121">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="d6d83-121">Data Item Name</span></span>|<span data-ttu-id="d6d83-122">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="d6d83-122">Data Item Type</span></span>|<span data-ttu-id="d6d83-123">Popis</span><span class="sxs-lookup"><span data-stu-id="d6d83-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d6d83-124">Název omezení.</span><span class="sxs-lookup"><span data-stu-id="d6d83-124">Throttle Name</span></span>|`xs:string`|<span data-ttu-id="d6d83-125">Název omezení, která byla překročena.</span><span class="sxs-lookup"><span data-stu-id="d6d83-125">The name of the throttle that has been exceeded.</span></span> <span data-ttu-id="d6d83-126">Buď `MaxConcurrentCalls`, `MaxConcurrentInstances`, nebo `MaxConcurrentSessions`,</span><span class="sxs-lookup"><span data-stu-id="d6d83-126">Either `MaxConcurrentCalls`, `MaxConcurrentInstances`, or `MaxConcurrentSessions`,</span></span>|  
|<span data-ttu-id="d6d83-127">Limit</span><span class="sxs-lookup"><span data-stu-id="d6d83-127">Limit</span></span>|`xs:long`|<span data-ttu-id="d6d83-128">Aktuálně nakonfigurovaný limit omezení.</span><span class="sxs-lookup"><span data-stu-id="d6d83-128">The currently configured limit of the throttle.</span></span>|  
|<span data-ttu-id="d6d83-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="d6d83-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="d6d83-130">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="d6d83-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d6d83-131">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="d6d83-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d6d83-132">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="d6d83-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d6d83-133">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="d6d83-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d6d83-134">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d6d83-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
