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
ms.openlocfilehash: 4ff48217b1430002e1590ec3fdb1707d65075ffe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="7503f-102">206 – ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="7503f-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="7503f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7503f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7503f-104">ID</span><span class="sxs-lookup"><span data-stu-id="7503f-104">ID</span></span>|<span data-ttu-id="7503f-105">206</span><span class="sxs-lookup"><span data-stu-id="7503f-105">206</span></span>|  
|<span data-ttu-id="7503f-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7503f-106">Keywords</span></span>|<span data-ttu-id="7503f-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7503f-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7503f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="7503f-108">Level</span></span>|<span data-ttu-id="7503f-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="7503f-109">Information</span></span>|  
|<span data-ttu-id="7503f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="7503f-110">Channel</span></span>|<span data-ttu-id="7503f-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="7503f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7503f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7503f-112">Description</span></span>  
 <span data-ttu-id="7503f-113">Tato událost je vygenerované po `ErrorHandler` zaznamenala příležitost ke zpracování výjimky, k níž došlo v operaci služby.</span><span class="sxs-lookup"><span data-stu-id="7503f-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7503f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="7503f-114">Message</span></span>  
 <span data-ttu-id="7503f-115">Dispečer vyvolat ZpracováníChyby typu "%1, s výjimkou typu"%3".</span><span class="sxs-lookup"><span data-stu-id="7503f-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="7503f-116">ErrorHandled == '%2'.</span><span class="sxs-lookup"><span data-stu-id="7503f-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7503f-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7503f-117">Details</span></span>  
  
|<span data-ttu-id="7503f-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="7503f-118">Data Item Name</span></span>|<span data-ttu-id="7503f-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="7503f-119">Data Item Type</span></span>|<span data-ttu-id="7503f-120">Popis</span><span class="sxs-lookup"><span data-stu-id="7503f-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7503f-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="7503f-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="7503f-122">Položka FullName CLR typu vyvolanou `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="7503f-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="7503f-123">Zpracovává</span><span class="sxs-lookup"><span data-stu-id="7503f-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="7503f-124">`true`Pokud obslužná rutina chyb zpracovávat chyby, jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="7503f-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="7503f-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="7503f-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="7503f-126">Položka FullName CLR výjimky, která se právě zpracovává.</span><span class="sxs-lookup"><span data-stu-id="7503f-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="7503f-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="7503f-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="7503f-128">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="7503f-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7503f-129">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="7503f-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7503f-130">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="7503f-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7503f-131">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="7503f-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7503f-132">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7503f-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
