---
title: "201 – ClientMessageInspectorAfterReceiveInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cb6d243177700daa1e653c394e027a6f5428371
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="93b5c-102">201 – ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="93b5c-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="93b5c-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="93b5c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93b5c-104">ID</span><span class="sxs-lookup"><span data-stu-id="93b5c-104">ID</span></span>|<span data-ttu-id="93b5c-105">201</span><span class="sxs-lookup"><span data-stu-id="93b5c-105">201</span></span>|  
|<span data-ttu-id="93b5c-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="93b5c-106">Keywords</span></span>|<span data-ttu-id="93b5c-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="93b5c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="93b5c-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="93b5c-108">Level</span></span>|<span data-ttu-id="93b5c-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="93b5c-109">Information</span></span>|  
|<span data-ttu-id="93b5c-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="93b5c-110">Channel</span></span>|<span data-ttu-id="93b5c-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="93b5c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="93b5c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="93b5c-112">Description</span></span>  
 <span data-ttu-id="93b5c-113">Tato událost je vygenerované po Model služby má vyvolat `AfterReceiveReply` metodu na zpráva inspector klienta.</span><span class="sxs-lookup"><span data-stu-id="93b5c-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="93b5c-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="93b5c-114">Message</span></span>  
 <span data-ttu-id="93b5c-115">Dispečer vyvolat 'AfterReceiveReply' na ClientMessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="93b5c-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="93b5c-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="93b5c-116">Details</span></span>  
  
|<span data-ttu-id="93b5c-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="93b5c-117">Data Item Name</span></span>|<span data-ttu-id="93b5c-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="93b5c-118">Data Item Type</span></span>|<span data-ttu-id="93b5c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="93b5c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="93b5c-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="93b5c-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="93b5c-121">Položka FullName CLR vyvolaná inspector typu.</span><span class="sxs-lookup"><span data-stu-id="93b5c-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="93b5c-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="93b5c-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="93b5c-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="93b5c-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="93b5c-124">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="93b5c-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="93b5c-125">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="93b5c-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="93b5c-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="93b5c-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="93b5c-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="93b5c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
