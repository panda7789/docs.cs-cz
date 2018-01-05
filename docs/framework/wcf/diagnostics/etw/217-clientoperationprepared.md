---
title: "217 – ClientOperationPrepared"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e1b4e3aab6a6a7f94bfb3783c9e32f83557db19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="f2ca0-102">217 – ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="f2ca0-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="f2ca0-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f2ca0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2ca0-104">ID</span><span class="sxs-lookup"><span data-stu-id="f2ca0-104">ID</span></span>|<span data-ttu-id="f2ca0-105">217</span><span class="sxs-lookup"><span data-stu-id="f2ca0-105">217</span></span>|  
|<span data-ttu-id="f2ca0-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f2ca0-106">Keywords</span></span>|<span data-ttu-id="f2ca0-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f2ca0-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f2ca0-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="f2ca0-108">Level</span></span>|<span data-ttu-id="f2ca0-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="f2ca0-109">Information</span></span>|  
|<span data-ttu-id="f2ca0-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="f2ca0-110">Channel</span></span>|<span data-ttu-id="f2ca0-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="f2ca0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f2ca0-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f2ca0-112">Description</span></span>  
 <span data-ttu-id="f2ca0-113">Tato událost je vygenerované klienty těsně před operace je odešle do služby.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f2ca0-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f2ca0-114">Message</span></span>  
 <span data-ttu-id="f2ca0-115">Klient je provádění akce '%1' přidružené ke smlouvě '%2'.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="f2ca0-116">Zpráva bude odeslána na "%3".</span><span class="sxs-lookup"><span data-stu-id="f2ca0-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f2ca0-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f2ca0-117">Details</span></span>  
  
|<span data-ttu-id="f2ca0-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="f2ca0-118">Data Item Name</span></span>|<span data-ttu-id="f2ca0-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="f2ca0-119">Data Item Type</span></span>|<span data-ttu-id="f2ca0-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f2ca0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f2ca0-121">Akce</span><span class="sxs-lookup"><span data-stu-id="f2ca0-121">Action</span></span>|`xs:string`|<span data-ttu-id="f2ca0-122">Hlavička protokolu SOAP akce odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="f2ca0-123">Název smlouvy</span><span class="sxs-lookup"><span data-stu-id="f2ca0-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="f2ca0-124">Název smlouvy.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-124">The name of the contract.</span></span> <span data-ttu-id="f2ca0-125">Příklad: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="f2ca0-126">Cílový</span><span class="sxs-lookup"><span data-stu-id="f2ca0-126">Destination</span></span>|`xs:string`|<span data-ttu-id="f2ca0-127">Adresa koncového bodu služby, který je zpráva odeslána.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="f2ca0-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="f2ca0-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="f2ca0-129">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f2ca0-130">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f2ca0-131">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f2ca0-132">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="f2ca0-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f2ca0-133">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f2ca0-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
