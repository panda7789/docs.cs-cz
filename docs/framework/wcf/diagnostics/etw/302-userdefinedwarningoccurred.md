---
title: 302 – UserDefinedWarningOccurred
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae455c9eec2335fcf6eb5473932bd8d9e5d2db95
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="1deb7-102">302 – UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="1deb7-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="1deb7-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1deb7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1deb7-104">ID</span><span class="sxs-lookup"><span data-stu-id="1deb7-104">ID</span></span>|<span data-ttu-id="1deb7-105">302</span><span class="sxs-lookup"><span data-stu-id="1deb7-105">302</span></span>|  
|<span data-ttu-id="1deb7-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1deb7-106">Keywords</span></span>|<span data-ttu-id="1deb7-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="1deb7-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="1deb7-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="1deb7-108">Level</span></span>|<span data-ttu-id="1deb7-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="1deb7-109">Warning</span></span>|  
|<span data-ttu-id="1deb7-110">Channel</span><span class="sxs-lookup"><span data-stu-id="1deb7-110">Channel</span></span>|<span data-ttu-id="1deb7-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1deb7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1deb7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1deb7-112">Description</span></span>  
 <span data-ttu-id="1deb7-113">Tato událost je vygenerované z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="1deb7-113">This event is emitted from user code.</span></span> <span data-ttu-id="1deb7-114">Vývojáři mohou emitování Tato událost při výskytu události definované vlastní upozornění ve své služby.</span><span class="sxs-lookup"><span data-stu-id="1deb7-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="1deb7-115">To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1deb7-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="1deb7-116">Kromě toho je WCF vzorku, který zabalí toto rozhraní API a ukazuje, jak správně emitování této události.</span><span class="sxs-lookup"><span data-stu-id="1deb7-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1deb7-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="1deb7-117">Message</span></span>  
 <span data-ttu-id="1deb7-118">Název: %1, Reference: %2, datové části: % 3</span><span class="sxs-lookup"><span data-stu-id="1deb7-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="1deb7-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1deb7-119">Details</span></span>  
  
|<span data-ttu-id="1deb7-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="1deb7-120">Data Item Name</span></span>|<span data-ttu-id="1deb7-121">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="1deb7-121">Data Item Type</span></span>|<span data-ttu-id="1deb7-122">Popis</span><span class="sxs-lookup"><span data-stu-id="1deb7-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1deb7-123">Název</span><span class="sxs-lookup"><span data-stu-id="1deb7-123">Name</span></span>|`xs:string`|<span data-ttu-id="1deb7-124">Název uživatelem definované události.</span><span class="sxs-lookup"><span data-stu-id="1deb7-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="1deb7-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="1deb7-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="1deb7-126">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="1deb7-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1deb7-127">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="1deb7-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1deb7-128">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="1deb7-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1deb7-129">datová část</span><span class="sxs-lookup"><span data-stu-id="1deb7-129">Payload</span></span>|`xs:string`|<span data-ttu-id="1deb7-130">Uživatelem definované datové části události.</span><span class="sxs-lookup"><span data-stu-id="1deb7-130">The user-defined payload of the event.</span></span>|
