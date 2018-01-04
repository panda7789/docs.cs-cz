---
title: "206 – ErrorHandlerInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 43acd7ae7bbfc84e1d1ffb1bf4fa49a3dd3f191a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="bdf1e-102">206 – ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="bdf1e-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="bdf1e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bdf1e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bdf1e-104">ID</span><span class="sxs-lookup"><span data-stu-id="bdf1e-104">ID</span></span>|<span data-ttu-id="bdf1e-105">206</span><span class="sxs-lookup"><span data-stu-id="bdf1e-105">206</span></span>|  
|<span data-ttu-id="bdf1e-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="bdf1e-106">Keywords</span></span>|<span data-ttu-id="bdf1e-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bdf1e-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="bdf1e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="bdf1e-108">Level</span></span>|<span data-ttu-id="bdf1e-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="bdf1e-109">Information</span></span>|  
|<span data-ttu-id="bdf1e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="bdf1e-110">Channel</span></span>|<span data-ttu-id="bdf1e-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="bdf1e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bdf1e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bdf1e-112">Description</span></span>  
 <span data-ttu-id="bdf1e-113">Tato událost je vygenerované po `ErrorHandler` zaznamenala příležitost ke zpracování výjimky, k níž došlo v operaci služby.</span><span class="sxs-lookup"><span data-stu-id="bdf1e-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bdf1e-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="bdf1e-114">Message</span></span>  
 <span data-ttu-id="bdf1e-115">Dispečer vyvolat ZpracováníChyby typu "%1, s výjimkou typu"%3".</span><span class="sxs-lookup"><span data-stu-id="bdf1e-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="bdf1e-116">ErrorHandled == '%2'.</span><span class="sxs-lookup"><span data-stu-id="bdf1e-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bdf1e-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bdf1e-117">Details</span></span>  
  
|<span data-ttu-id="bdf1e-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="bdf1e-118">Data Item Name</span></span>|<span data-ttu-id="bdf1e-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="bdf1e-119">Data Item Type</span></span>|<span data-ttu-id="bdf1e-120">Popis</span><span class="sxs-lookup"><span data-stu-id="bdf1e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bdf1e-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="bdf1e-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="bdf1e-122">Položka FullName CLR typu vyvolanou `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="bdf1e-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="bdf1e-123">Zpracovává</span><span class="sxs-lookup"><span data-stu-id="bdf1e-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="bdf1e-124">`true`Pokud obslužná rutina chyb zpracovávat chyby, jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="bdf1e-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="bdf1e-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="bdf1e-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="bdf1e-126">Položka FullName CLR výjimky, která se právě zpracovává.</span><span class="sxs-lookup"><span data-stu-id="bdf1e-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="bdf1e-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="bdf1e-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="bdf1e-128">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="bdf1e-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="bdf1e-129">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="bdf1e-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="bdf1e-130">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="bdf1e-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="bdf1e-131">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="bdf1e-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="bdf1e-132">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bdf1e-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
