---
title: "214 – OperationCompleted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6ef1eb398a0146e619cbcb85fe2761306aba4fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="214---operationcompleted"></a><span data-ttu-id="14e36-102">214 – OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="14e36-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="14e36-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="14e36-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14e36-104">ID</span><span class="sxs-lookup"><span data-stu-id="14e36-104">ID</span></span>|<span data-ttu-id="14e36-105">214</span><span class="sxs-lookup"><span data-stu-id="14e36-105">214</span></span>|  
|<span data-ttu-id="14e36-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="14e36-106">Keywords</span></span>|<span data-ttu-id="14e36-107">HealthMonitoring, EndToEndMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="14e36-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="14e36-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="14e36-108">Level</span></span>|<span data-ttu-id="14e36-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="14e36-109">Information</span></span>|  
|<span data-ttu-id="14e36-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="14e36-110">Channel</span></span>|<span data-ttu-id="14e36-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="14e36-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14e36-112">Popis</span><span class="sxs-lookup"><span data-stu-id="14e36-112">Description</span></span>  
 <span data-ttu-id="14e36-113">Tato událost je vygenerované při výchozí Model služby `OperationInvoker` volání metody byla dokončena bez dané metody došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="14e36-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="14e36-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="14e36-114">Message</span></span>  
 <span data-ttu-id="14e36-115">OperationInvoker dokončit volání metody '%1'.</span><span class="sxs-lookup"><span data-stu-id="14e36-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="14e36-116">Doba trvání volání metoda byla ms '%2'.</span><span class="sxs-lookup"><span data-stu-id="14e36-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="14e36-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="14e36-117">Details</span></span>  
  
|<span data-ttu-id="14e36-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="14e36-118">Data Item Name</span></span>|<span data-ttu-id="14e36-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="14e36-119">Data Item Type</span></span>|<span data-ttu-id="14e36-120">Popis</span><span class="sxs-lookup"><span data-stu-id="14e36-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="14e36-121">Název metody</span><span class="sxs-lookup"><span data-stu-id="14e36-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="14e36-122">CLR název metody, který byl vyvolán `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="14e36-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="14e36-123">Doba trvání</span><span class="sxs-lookup"><span data-stu-id="14e36-123">Duration</span></span>|`xs:long`|<span data-ttu-id="14e36-124">Čas v milisekundách, po které trvalo `OperationInvoker` k vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="14e36-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="14e36-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="14e36-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="14e36-126">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="14e36-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="14e36-127">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="14e36-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="14e36-128">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="14e36-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="14e36-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="14e36-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="14e36-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="14e36-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
