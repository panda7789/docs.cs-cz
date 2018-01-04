---
title: "207 – FaultProviderInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9035739f8625a07e8bf2b9bce2fe109880676405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="ab7ab-102">207 – FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="ab7ab-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="ab7ab-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ab7ab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab7ab-104">ID</span><span class="sxs-lookup"><span data-stu-id="ab7ab-104">ID</span></span>|<span data-ttu-id="ab7ab-105">207</span><span class="sxs-lookup"><span data-stu-id="ab7ab-105">207</span></span>|  
|<span data-ttu-id="ab7ab-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ab7ab-106">Keywords</span></span>|<span data-ttu-id="ab7ab-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ab7ab-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ab7ab-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ab7ab-108">Level</span></span>|<span data-ttu-id="ab7ab-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="ab7ab-109">Information</span></span>|  
|<span data-ttu-id="ab7ab-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ab7ab-110">Channel</span></span>|<span data-ttu-id="ab7ab-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="ab7ab-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ab7ab-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ab7ab-112">Description</span></span>  
 <span data-ttu-id="ab7ab-113">Tato událost je vygenerované po `FaultProvider` metoda byla volána.</span><span class="sxs-lookup"><span data-stu-id="ab7ab-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ab7ab-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ab7ab-114">Message</span></span>  
 <span data-ttu-id="ab7ab-115">Dispečer vyvolat FaultProvider typu "%1, s výjimkou typu '%2'.</span><span class="sxs-lookup"><span data-stu-id="ab7ab-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ab7ab-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ab7ab-116">Details</span></span>  
  
|<span data-ttu-id="ab7ab-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ab7ab-117">Data Item Name</span></span>|<span data-ttu-id="ab7ab-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="ab7ab-118">Data Item Type</span></span>|<span data-ttu-id="ab7ab-119">Popis</span><span class="sxs-lookup"><span data-stu-id="ab7ab-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ab7ab-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="ab7ab-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="ab7ab-121">Položka FullName CLR typu vyvolanou `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="ab7ab-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="ab7ab-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="ab7ab-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="ab7ab-123">Položka FullName CLR výjimky, `FaultProvider` má zpracovat.</span><span class="sxs-lookup"><span data-stu-id="ab7ab-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="ab7ab-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="ab7ab-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="ab7ab-125">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="ab7ab-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ab7ab-126">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="ab7ab-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ab7ab-127">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="ab7ab-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ab7ab-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="ab7ab-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ab7ab-129">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ab7ab-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
