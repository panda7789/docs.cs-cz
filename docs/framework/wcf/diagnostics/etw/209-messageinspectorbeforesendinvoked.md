---
title: "209 – MessageInspectorBeforeSendInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9083a6dc9849fcd177b1e6a38ca7bb72e7799dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="9a388-102">209 – MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="9a388-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="9a388-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a388-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a388-104">ID</span><span class="sxs-lookup"><span data-stu-id="9a388-104">ID</span></span>|<span data-ttu-id="9a388-105">209</span><span class="sxs-lookup"><span data-stu-id="9a388-105">209</span></span>|  
|<span data-ttu-id="9a388-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9a388-106">Keywords</span></span>|<span data-ttu-id="9a388-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a388-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9a388-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9a388-108">Level</span></span>|<span data-ttu-id="9a388-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="9a388-109">Information</span></span>|  
|<span data-ttu-id="9a388-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9a388-110">Channel</span></span>|<span data-ttu-id="9a388-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="9a388-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a388-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9a388-112">Description</span></span>  
 <span data-ttu-id="9a388-113">Tato událost je vygenerované po Model služby má vyvolat `BeforeSend` metodu na zpráva inspector.</span><span class="sxs-lookup"><span data-stu-id="9a388-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a388-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9a388-114">Message</span></span>  
 <span data-ttu-id="9a388-115">Dispečer vyvolat 'BeforeSendRequest' na MessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="9a388-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a388-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9a388-116">Details</span></span>  
  
|<span data-ttu-id="9a388-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9a388-117">Data Item Name</span></span>|<span data-ttu-id="9a388-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="9a388-118">Data Item Type</span></span>|<span data-ttu-id="9a388-119">Popis</span><span class="sxs-lookup"><span data-stu-id="9a388-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a388-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="9a388-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="9a388-121">Položka FullName CLR typu vyvolanou `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="9a388-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="9a388-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="9a388-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="9a388-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="9a388-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9a388-124">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="9a388-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9a388-125">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="9a388-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9a388-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="9a388-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9a388-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9a388-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
