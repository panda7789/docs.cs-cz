---
title: "215 – MessageReceivedByTransport"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: acc39fea579a66479de6686cba928915a437f864
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="2f6d9-102">215 – MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="2f6d9-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="2f6d9-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2f6d9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f6d9-104">ID</span><span class="sxs-lookup"><span data-stu-id="2f6d9-104">ID</span></span>|<span data-ttu-id="2f6d9-105">215</span><span class="sxs-lookup"><span data-stu-id="2f6d9-105">215</span></span>|  
|<span data-ttu-id="2f6d9-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2f6d9-106">Keywords</span></span>|<span data-ttu-id="2f6d9-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2f6d9-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2f6d9-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="2f6d9-108">Level</span></span>|<span data-ttu-id="2f6d9-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="2f6d9-109">Information</span></span>|  
|<span data-ttu-id="2f6d9-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="2f6d9-110">Channel</span></span>|<span data-ttu-id="2f6d9-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="2f6d9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2f6d9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2f6d9-112">Description</span></span>  
 <span data-ttu-id="2f6d9-113">K této události dojde, když přenos protokolu TCP přijme zprávu o.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="2f6d9-114">Všimněte si, že se na úrovni přenosu, více zpráv nelze vyměňovat mezi klienty a služby pro jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="2f6d9-115">To může být z důvodu chování infrastruktury, je dobrým příkladem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="2f6d9-116">Proto počet `MessageReceivedByTransport` události, které jsou vygenerované lišit v závislosti na vaší služby vazby a jeho konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f6d9-117">Tato událost není vygenerované pro jednosměrné přenosy.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2f6d9-118">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2f6d9-118">Message</span></span>  
 <span data-ttu-id="2f6d9-119">Přenos přijala zprávu z '%1'.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2f6d9-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2f6d9-120">Details</span></span>  
  
|<span data-ttu-id="2f6d9-121">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="2f6d9-121">Data Item Name</span></span>|<span data-ttu-id="2f6d9-122">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="2f6d9-122">Data Item Type</span></span>|<span data-ttu-id="2f6d9-123">Popis</span><span class="sxs-lookup"><span data-stu-id="2f6d9-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2f6d9-124">Adresu naslouchání</span><span class="sxs-lookup"><span data-stu-id="2f6d9-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="2f6d9-125">Adresa, která se zobrazila zpráva.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-125">The address that received the message.</span></span>|  
|<span data-ttu-id="2f6d9-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="2f6d9-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="2f6d9-127">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2f6d9-128">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2f6d9-129">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2f6d9-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="2f6d9-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2f6d9-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2f6d9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
