---
title: "211 – ParameterInspectorAfterCallInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78424b8057518f5d9f201ead33b2784ffeeb7e58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="961e3-102">211 – ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="961e3-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="961e3-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="961e3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="961e3-104">ID</span><span class="sxs-lookup"><span data-stu-id="961e3-104">ID</span></span>|<span data-ttu-id="961e3-105">211</span><span class="sxs-lookup"><span data-stu-id="961e3-105">211</span></span>|  
|<span data-ttu-id="961e3-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="961e3-106">Keywords</span></span>|<span data-ttu-id="961e3-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="961e3-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="961e3-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="961e3-108">Level</span></span>|<span data-ttu-id="961e3-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="961e3-109">Information</span></span>|  
|<span data-ttu-id="961e3-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="961e3-110">Channel</span></span>|<span data-ttu-id="961e3-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="961e3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="961e3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="961e3-112">Description</span></span>  
 <span data-ttu-id="961e3-113">Tato událost je vygenerované po Model služby má vyvolat `AfterCall` metodu `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="961e3-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="961e3-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="961e3-114">Message</span></span>  
 <span data-ttu-id="961e3-115">Dispečer vyvolat 'AfterCall' na ParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="961e3-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="961e3-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="961e3-116">Details</span></span>  
  
|<span data-ttu-id="961e3-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="961e3-117">Data Item Name</span></span>|<span data-ttu-id="961e3-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="961e3-118">Data Item Type</span></span>|<span data-ttu-id="961e3-119">Popis</span><span class="sxs-lookup"><span data-stu-id="961e3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="961e3-120">Název typu</span><span class="sxs-lookup"><span data-stu-id="961e3-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="961e3-121">Položka FullName CLR typu vyvolanou `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="961e3-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="961e3-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="961e3-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="961e3-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="961e3-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="961e3-124">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="961e3-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="961e3-125">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="961e3-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="961e3-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="961e3-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="961e3-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="961e3-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
