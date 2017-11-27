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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bc291469721915f399fe5acfa3200716939fee4c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="3cb2a-102">303 – UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="3cb2a-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="3cb2a-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3cb2a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3cb2a-104">ID</span><span class="sxs-lookup"><span data-stu-id="3cb2a-104">ID</span></span>|<span data-ttu-id="3cb2a-105">303</span><span class="sxs-lookup"><span data-stu-id="3cb2a-105">303</span></span>|  
|<span data-ttu-id="3cb2a-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3cb2a-106">Keywords</span></span>|<span data-ttu-id="3cb2a-107">Řešení potíží, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="3cb2a-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="3cb2a-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="3cb2a-108">Level</span></span>|<span data-ttu-id="3cb2a-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="3cb2a-109">Information</span></span>|  
|<span data-ttu-id="3cb2a-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="3cb2a-110">Channel</span></span>|<span data-ttu-id="3cb2a-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="3cb2a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3cb2a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3cb2a-112">Description</span></span>  
 <span data-ttu-id="3cb2a-113">Tato událost je vygenerované z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="3cb2a-113">This event is emitted from user code.</span></span> <span data-ttu-id="3cb2a-114">Vývojáři mohou emitování Tato událost při výskytu vlastní informační události ve své služby.</span><span class="sxs-lookup"><span data-stu-id="3cb2a-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="3cb2a-115">To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3cb2a-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="3cb2a-116">Kromě toho je WCF vzorku, který zabalí toto rozhraní API a ukazuje, jak správně emitování této události.</span><span class="sxs-lookup"><span data-stu-id="3cb2a-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3cb2a-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3cb2a-117">Message</span></span>  
 <span data-ttu-id="3cb2a-118">Název: %1, Reference: %2, datové části: % 3</span><span class="sxs-lookup"><span data-stu-id="3cb2a-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="3cb2a-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3cb2a-119">Details</span></span>  
  
|<span data-ttu-id="3cb2a-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="3cb2a-120">Data Item Name</span></span>|<span data-ttu-id="3cb2a-121">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="3cb2a-121">Data Item Type</span></span>|<span data-ttu-id="3cb2a-122">Popis</span><span class="sxs-lookup"><span data-stu-id="3cb2a-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3cb2a-123">Název</span><span class="sxs-lookup"><span data-stu-id="3cb2a-123">Name</span></span>|`xs:string`|<span data-ttu-id="3cb2a-124">Uživatelem definovaný název události</span><span class="sxs-lookup"><span data-stu-id="3cb2a-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="3cb2a-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="3cb2a-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="3cb2a-126">Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="3cb2a-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3cb2a-127">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="3cb2a-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3cb2a-128">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="3cb2a-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3cb2a-129">datová část</span><span class="sxs-lookup"><span data-stu-id="3cb2a-129">Payload</span></span>|`xs:string`|<span data-ttu-id="3cb2a-130">Uživatelem definované datové části události.</span><span class="sxs-lookup"><span data-stu-id="3cb2a-130">The user-defined payload of the event.</span></span>|
