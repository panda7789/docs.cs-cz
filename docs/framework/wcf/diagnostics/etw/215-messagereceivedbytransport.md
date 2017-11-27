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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 92880fd01f8f61a06c9b2c7d51ecc4a1671c6c85
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="2fff5-102">215 – MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="2fff5-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="2fff5-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2fff5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2fff5-104">ID</span><span class="sxs-lookup"><span data-stu-id="2fff5-104">ID</span></span>|<span data-ttu-id="2fff5-105">215</span><span class="sxs-lookup"><span data-stu-id="2fff5-105">215</span></span>|  
|<span data-ttu-id="2fff5-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2fff5-106">Keywords</span></span>|<span data-ttu-id="2fff5-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2fff5-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2fff5-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="2fff5-108">Level</span></span>|<span data-ttu-id="2fff5-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="2fff5-109">Information</span></span>|  
|<span data-ttu-id="2fff5-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="2fff5-110">Channel</span></span>|<span data-ttu-id="2fff5-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="2fff5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2fff5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2fff5-112">Description</span></span>  
 <span data-ttu-id="2fff5-113">K této události dojde, když přenos protokolu TCP přijme zprávu o.</span><span class="sxs-lookup"><span data-stu-id="2fff5-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="2fff5-114">Všimněte si, že se na úrovni přenosu, více zpráv nelze vyměňovat mezi klienty a služby pro jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="2fff5-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="2fff5-115">To může být z důvodu chování infrastruktury, je dobrým příkladem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2fff5-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="2fff5-116">Proto počet `MessageReceivedByTransport` události, které jsou vygenerované lišit v závislosti na vaší služby vazby a jeho konfigurace.</span><span class="sxs-lookup"><span data-stu-id="2fff5-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2fff5-117">Tato událost není vygenerované pro jednosměrné přenosy.</span><span class="sxs-lookup"><span data-stu-id="2fff5-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2fff5-118">Zpráva</span><span class="sxs-lookup"><span data-stu-id="2fff5-118">Message</span></span>  
 <span data-ttu-id="2fff5-119">Přenos přijala zprávu z '%1'.</span><span class="sxs-lookup"><span data-stu-id="2fff5-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2fff5-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2fff5-120">Details</span></span>  
  
|<span data-ttu-id="2fff5-121">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="2fff5-121">Data Item Name</span></span>|<span data-ttu-id="2fff5-122">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="2fff5-122">Data Item Type</span></span>|<span data-ttu-id="2fff5-123">Popis</span><span class="sxs-lookup"><span data-stu-id="2fff5-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2fff5-124">Adresu naslouchání</span><span class="sxs-lookup"><span data-stu-id="2fff5-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="2fff5-125">Adresa, která se zobrazila zpráva.</span><span class="sxs-lookup"><span data-stu-id="2fff5-125">The address that received the message.</span></span>|  
|<span data-ttu-id="2fff5-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="2fff5-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="2fff5-127">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="2fff5-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2fff5-128">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="2fff5-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2fff5-129">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="2fff5-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2fff5-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="2fff5-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2fff5-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="2fff5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
