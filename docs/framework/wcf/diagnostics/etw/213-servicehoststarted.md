---
title: "213 – ServiceHostStarted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cc12626263e21f5fd7310157dcdafe327e6d17a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="1726d-102">213 – ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="1726d-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="1726d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1726d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1726d-104">ID</span><span class="sxs-lookup"><span data-stu-id="1726d-104">ID</span></span>|<span data-ttu-id="1726d-105">213</span><span class="sxs-lookup"><span data-stu-id="1726d-105">213</span></span>|  
|<span data-ttu-id="1726d-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1726d-106">Keywords</span></span>|<span data-ttu-id="1726d-107">EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceHost</span><span class="sxs-lookup"><span data-stu-id="1726d-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="1726d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="1726d-108">Level</span></span>|<span data-ttu-id="1726d-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="1726d-109">LogAlways</span></span>|  
|<span data-ttu-id="1726d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="1726d-110">Channel</span></span>|<span data-ttu-id="1726d-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="1726d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1726d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1726d-112">Description</span></span>  
 <span data-ttu-id="1726d-113">Tato událost je vygenerované při spuštění hostitele webové hostované služby.</span><span class="sxs-lookup"><span data-stu-id="1726d-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="1726d-114">Obvykle se to stane, když služba je aktivován zprávu.</span><span class="sxs-lookup"><span data-stu-id="1726d-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="1726d-115">Může také dojít, pokud služba je nakonfigurována na automatické spuštění.</span><span class="sxs-lookup"><span data-stu-id="1726d-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1726d-116">Zpráva</span><span class="sxs-lookup"><span data-stu-id="1726d-116">Message</span></span>  
 <span data-ttu-id="1726d-117">Hostitel služby spuštění: '%1'.</span><span class="sxs-lookup"><span data-stu-id="1726d-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1726d-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1726d-118">Details</span></span>  
  
|<span data-ttu-id="1726d-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="1726d-119">Data Item Name</span></span>|<span data-ttu-id="1726d-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="1726d-120">Data Item Type</span></span>|<span data-ttu-id="1726d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1726d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1726d-122">Název typu služby</span><span class="sxs-lookup"><span data-stu-id="1726d-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="1726d-123">Položka FullName CLR typu implementace služby.</span><span class="sxs-lookup"><span data-stu-id="1726d-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="1726d-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="1726d-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="1726d-125">Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="1726d-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1726d-126">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="1726d-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1726d-127">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="1726d-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1726d-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="1726d-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1726d-129">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1726d-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
