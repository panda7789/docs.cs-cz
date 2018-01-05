---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d737a7334098961cccb73a114be9be5bb71727
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="6b0f8-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="6b0f8-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="6b0f8-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6b0f8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b0f8-104">ID</span><span class="sxs-lookup"><span data-stu-id="6b0f8-104">ID</span></span>|<span data-ttu-id="6b0f8-105">202</span><span class="sxs-lookup"><span data-stu-id="6b0f8-105">202</span></span>|  
|<span data-ttu-id="6b0f8-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6b0f8-106">Keywords</span></span>|<span data-ttu-id="6b0f8-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6b0f8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="6b0f8-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6b0f8-108">Level</span></span>|<span data-ttu-id="6b0f8-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="6b0f8-109">Information</span></span>|  
|<span data-ttu-id="6b0f8-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6b0f8-110">Channel</span></span>|<span data-ttu-id="6b0f8-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="6b0f8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6b0f8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6b0f8-112">Description</span></span>  
 <span data-ttu-id="6b0f8-113">Tato událost je vygenerované po Model služby má vyvolat `BeforeSendRequest` metodu na zpráva inspector klienta.</span><span class="sxs-lookup"><span data-stu-id="6b0f8-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6b0f8-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6b0f8-114">Message</span></span>  
 <span data-ttu-id="6b0f8-115">Dispečer vyvolat 'BeforeSendRequest' na ClientMessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="6b0f8-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6b0f8-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6b0f8-116">Details</span></span>  
  
|<span data-ttu-id="6b0f8-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6b0f8-117">Data Item Name</span></span>|<span data-ttu-id="6b0f8-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="6b0f8-118">Data Item Type</span></span>|<span data-ttu-id="6b0f8-119">Popis</span><span class="sxs-lookup"><span data-stu-id="6b0f8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6b0f8-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="6b0f8-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="6b0f8-121">Položka FullName CLR vyvolaná inspector typu.</span><span class="sxs-lookup"><span data-stu-id="6b0f8-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="6b0f8-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="6b0f8-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="6b0f8-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="6b0f8-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6b0f8-124">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="6b0f8-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6b0f8-125">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="6b0f8-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6b0f8-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6b0f8-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6b0f8-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6b0f8-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
