---
title: "218 – ClientOperationCompleted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 974fde79d8b24c17928fa4ff38bb9d35d6b5a815
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="6405d-102">218 – ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="6405d-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="6405d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6405d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6405d-104">ID</span><span class="sxs-lookup"><span data-stu-id="6405d-104">ID</span></span>|<span data-ttu-id="6405d-105">218</span><span class="sxs-lookup"><span data-stu-id="6405d-105">218</span></span>|  
|<span data-ttu-id="6405d-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6405d-106">Keywords</span></span>|<span data-ttu-id="6405d-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6405d-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="6405d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6405d-108">Level</span></span>|<span data-ttu-id="6405d-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="6405d-109">Information</span></span>|  
|<span data-ttu-id="6405d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6405d-110">Channel</span></span>|<span data-ttu-id="6405d-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="6405d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6405d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6405d-112">Description</span></span>  
 <span data-ttu-id="6405d-113">Tato událost je vygenerované klienti hned po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="6405d-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="6405d-114">U Jednosměrná operace nastavení je to hned po odeslání zprávy jsou úspěšně.</span><span class="sxs-lookup"><span data-stu-id="6405d-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="6405d-115">Pro operace požadavků a odpovědí jde po obdržení odpovědi.</span><span class="sxs-lookup"><span data-stu-id="6405d-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6405d-116">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6405d-116">Message</span></span>  
 <span data-ttu-id="6405d-117">Klient dokončit provádění akce '%1' přidružené ke smlouvě '%2'.</span><span class="sxs-lookup"><span data-stu-id="6405d-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="6405d-118">Zpráva byla odeslána na '%3'.</span><span class="sxs-lookup"><span data-stu-id="6405d-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6405d-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6405d-119">Details</span></span>  
  
|<span data-ttu-id="6405d-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6405d-120">Data Item Name</span></span>|<span data-ttu-id="6405d-121">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="6405d-121">Data Item Type</span></span>|<span data-ttu-id="6405d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="6405d-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6405d-123">Akce</span><span class="sxs-lookup"><span data-stu-id="6405d-123">Action</span></span>|<span data-ttu-id="6405d-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="6405d-124">xs:string</span></span>|<span data-ttu-id="6405d-125">Hlavička protokolu SOAP akce odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="6405d-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="6405d-126">Název smlouvy</span><span class="sxs-lookup"><span data-stu-id="6405d-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="6405d-127">Název smlouvy.</span><span class="sxs-lookup"><span data-stu-id="6405d-127">The name of the contract.</span></span> <span data-ttu-id="6405d-128">Příklad: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="6405d-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="6405d-129">Cílový</span><span class="sxs-lookup"><span data-stu-id="6405d-129">Destination</span></span>|`xs:string`|<span data-ttu-id="6405d-130">Adresa koncového bodu služby, který vám byl zaslán zprávy.</span><span class="sxs-lookup"><span data-stu-id="6405d-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="6405d-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="6405d-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="6405d-132">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="6405d-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6405d-133">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="6405d-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6405d-134">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="6405d-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6405d-135">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6405d-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6405d-136">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6405d-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
