---
title: "303 – UserDefinedInformationEventOccured"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc04837834277dccc9d21d27e89c84f09f36167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="94f56-102">303 – UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="94f56-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="94f56-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="94f56-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="94f56-104">ID</span><span class="sxs-lookup"><span data-stu-id="94f56-104">ID</span></span>|<span data-ttu-id="94f56-105">303</span><span class="sxs-lookup"><span data-stu-id="94f56-105">303</span></span>|  
|<span data-ttu-id="94f56-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="94f56-106">Keywords</span></span>|<span data-ttu-id="94f56-107">Řešení potíží, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="94f56-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="94f56-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="94f56-108">Level</span></span>|<span data-ttu-id="94f56-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="94f56-109">Information</span></span>|  
|<span data-ttu-id="94f56-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="94f56-110">Channel</span></span>|<span data-ttu-id="94f56-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="94f56-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="94f56-112">Popis</span><span class="sxs-lookup"><span data-stu-id="94f56-112">Description</span></span>  
 <span data-ttu-id="94f56-113">Tato událost je vygenerované z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="94f56-113">This event is emitted from user code.</span></span> <span data-ttu-id="94f56-114">Vývojáři mohou emitování Tato událost při výskytu vlastní informační události ve své služby.</span><span class="sxs-lookup"><span data-stu-id="94f56-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="94f56-115">To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="94f56-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="94f56-116">Kromě toho je WCF vzorku, který zabalí toto rozhraní API a ukazuje, jak správně emitování této události.</span><span class="sxs-lookup"><span data-stu-id="94f56-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="94f56-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="94f56-117">Message</span></span>  
 <span data-ttu-id="94f56-118">Název: %1, Reference: %2, datové části: % 3</span><span class="sxs-lookup"><span data-stu-id="94f56-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="94f56-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="94f56-119">Details</span></span>  
  
|<span data-ttu-id="94f56-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="94f56-120">Data Item Name</span></span>|<span data-ttu-id="94f56-121">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="94f56-121">Data Item Type</span></span>|<span data-ttu-id="94f56-122">Popis</span><span class="sxs-lookup"><span data-stu-id="94f56-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="94f56-123">Název</span><span class="sxs-lookup"><span data-stu-id="94f56-123">Name</span></span>|`xs:string`|<span data-ttu-id="94f56-124">Uživatelem definovaný název události</span><span class="sxs-lookup"><span data-stu-id="94f56-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="94f56-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="94f56-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="94f56-126">Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="94f56-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="94f56-127">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="94f56-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="94f56-128">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="94f56-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="94f56-129">datová část</span><span class="sxs-lookup"><span data-stu-id="94f56-129">Payload</span></span>|`xs:string`|<span data-ttu-id="94f56-130">Uživatelem definované datové části události.</span><span class="sxs-lookup"><span data-stu-id="94f56-130">The user-defined payload of the event.</span></span>|
