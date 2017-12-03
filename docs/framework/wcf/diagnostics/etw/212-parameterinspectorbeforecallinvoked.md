---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64dcdb3a928d2ec05cd7dac557b6db10cb4a6511
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="85924-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="85924-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="85924-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="85924-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="85924-104">ID</span><span class="sxs-lookup"><span data-stu-id="85924-104">ID</span></span>|<span data-ttu-id="85924-105">212</span><span class="sxs-lookup"><span data-stu-id="85924-105">212</span></span>|  
|<span data-ttu-id="85924-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="85924-106">Keywords</span></span>|<span data-ttu-id="85924-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="85924-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="85924-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="85924-108">Level</span></span>|<span data-ttu-id="85924-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="85924-109">Information</span></span>|  
|<span data-ttu-id="85924-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="85924-110">Channel</span></span>|<span data-ttu-id="85924-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="85924-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="85924-112">Popis</span><span class="sxs-lookup"><span data-stu-id="85924-112">Description</span></span>  
 <span data-ttu-id="85924-113">Tato událost je vygenerované po Model služby má vyvolat `BeforeCall` metodu `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="85924-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="85924-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="85924-114">Message</span></span>  
 <span data-ttu-id="85924-115">Dispečer vyvolat 'BeforeCall' na ParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="85924-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="85924-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="85924-116">Details</span></span>  
  
|<span data-ttu-id="85924-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="85924-117">Data Item Name</span></span>|<span data-ttu-id="85924-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="85924-118">Data Item Type</span></span>|<span data-ttu-id="85924-119">Popis</span><span class="sxs-lookup"><span data-stu-id="85924-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="85924-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="85924-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="85924-121">Položka FullName CLR vyvolaná inspector typu.</span><span class="sxs-lookup"><span data-stu-id="85924-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="85924-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="85924-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="85924-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="85924-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="85924-124">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="85924-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="85924-125">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="85924-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="85924-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="85924-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="85924-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="85924-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
