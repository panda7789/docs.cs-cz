---
title: 216 - MessageSentByTransport
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad2b32b8d1386f6cc0754070cba2b1a556219b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="55455-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="55455-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="55455-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="55455-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55455-104">ID</span><span class="sxs-lookup"><span data-stu-id="55455-104">ID</span></span>|<span data-ttu-id="55455-105">216</span><span class="sxs-lookup"><span data-stu-id="55455-105">216</span></span>|  
|<span data-ttu-id="55455-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="55455-106">Keywords</span></span>|<span data-ttu-id="55455-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="55455-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="55455-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="55455-108">Level</span></span>|<span data-ttu-id="55455-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="55455-109">Information</span></span>|  
|<span data-ttu-id="55455-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="55455-110">Channel</span></span>|<span data-ttu-id="55455-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="55455-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="55455-112">Popis</span><span class="sxs-lookup"><span data-stu-id="55455-112">Description</span></span>  
 <span data-ttu-id="55455-113">K této události dojde, když přenos protokolu TCP odešle zprávu.</span><span class="sxs-lookup"><span data-stu-id="55455-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="55455-114">Všimněte si, že na úrovni přenosu může být více zpráv vyměňují mezi klienty a služby pro jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="55455-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="55455-115">Může to být způsobeno chování infrastruktury, je dobrým příkladem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="55455-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="55455-116">Proto počet **MessageSentByTransport** události, které jsou vygenerované lišit v závislosti na vaší služby vazby a jeho konfigurace.</span><span class="sxs-lookup"><span data-stu-id="55455-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="55455-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="55455-117">Message</span></span>  
 <span data-ttu-id="55455-118">Přenos neodeslal zprávu na '%1'.</span><span class="sxs-lookup"><span data-stu-id="55455-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="55455-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="55455-119">Details</span></span>  
  
|<span data-ttu-id="55455-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="55455-120">Data Item Name</span></span>|<span data-ttu-id="55455-121">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="55455-121">Data Item Type</span></span>|<span data-ttu-id="55455-122">Popis</span><span class="sxs-lookup"><span data-stu-id="55455-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="55455-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="55455-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="55455-124">Adresa, který vám byl zaslán zprávu požadavku.</span><span class="sxs-lookup"><span data-stu-id="55455-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="55455-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="55455-125">HostReference</span></span>|<span data-ttu-id="55455-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="55455-126">xs:string</span></span>|<span data-ttu-id="55455-127">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="55455-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="55455-128">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="55455-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="55455-129">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="55455-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="55455-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="55455-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="55455-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="55455-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
