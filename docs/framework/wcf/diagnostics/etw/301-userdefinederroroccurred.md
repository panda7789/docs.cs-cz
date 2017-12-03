---
title: "301 – UserDefinedErrorOccurred"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56cfe60c221062e3ad7ae1b8cbdc9b135e6fa2e8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="339af-102">301 – UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="339af-102">301 - UserDefinedErrorOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="339af-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="339af-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="339af-104">ID</span><span class="sxs-lookup"><span data-stu-id="339af-104">ID</span></span>|<span data-ttu-id="339af-105">301</span><span class="sxs-lookup"><span data-stu-id="339af-105">301</span></span>|  
|<span data-ttu-id="339af-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="339af-106">Keywords</span></span>|<span data-ttu-id="339af-107">Řešení potíží, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="339af-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="339af-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="339af-108">Level</span></span>|<span data-ttu-id="339af-109">Chyba</span><span class="sxs-lookup"><span data-stu-id="339af-109">Error</span></span>|  
|<span data-ttu-id="339af-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="339af-110">Channel</span></span>|<span data-ttu-id="339af-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="339af-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="339af-112">Popis</span><span class="sxs-lookup"><span data-stu-id="339af-112">Description</span></span>  
 <span data-ttu-id="339af-113">Tato událost je vygenerované z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="339af-113">This event is emitted from user code.</span></span> <span data-ttu-id="339af-114">Vývojáři mohou emitování tuto událost, pokud dojde k chybě s vlastní ve své služby.</span><span class="sxs-lookup"><span data-stu-id="339af-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="339af-115">To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="339af-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="339af-116">Kromě toho je WCF vzorku, který zabalí toto rozhraní API a ukazuje, jak správně emitování této události.</span><span class="sxs-lookup"><span data-stu-id="339af-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="339af-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="339af-117">Message</span></span>  
 <span data-ttu-id="339af-118">Název: %1, Reference: %2, datové části: % 3</span><span class="sxs-lookup"><span data-stu-id="339af-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="339af-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="339af-119">Details</span></span>  
  
|<span data-ttu-id="339af-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="339af-120">Data Item Name</span></span>|<span data-ttu-id="339af-121">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="339af-121">Data Item Type</span></span>|<span data-ttu-id="339af-122">Popis</span><span class="sxs-lookup"><span data-stu-id="339af-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="339af-123">Název</span><span class="sxs-lookup"><span data-stu-id="339af-123">Name</span></span>|`xs:string`|<span data-ttu-id="339af-124">Název uživatelem definované události.</span><span class="sxs-lookup"><span data-stu-id="339af-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="339af-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="339af-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="339af-126">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="339af-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="339af-127">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="339af-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="339af-128">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="339af-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="339af-129">datová část</span><span class="sxs-lookup"><span data-stu-id="339af-129">Payload</span></span>|`xs:string`|<span data-ttu-id="339af-130">Uživatelem definované datové části události.</span><span class="sxs-lookup"><span data-stu-id="339af-130">The user-defined payload of the event.</span></span>|
