---
title: "222 – OperationFailed"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c76b502c9c1a767898b1e857c2e943c26fad5c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="222---operationfailed"></a><span data-ttu-id="70910-102">222 – OperationFailed</span><span class="sxs-lookup"><span data-stu-id="70910-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="70910-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="70910-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="70910-104">ID</span><span class="sxs-lookup"><span data-stu-id="70910-104">ID</span></span>|<span data-ttu-id="70910-105">222</span><span class="sxs-lookup"><span data-stu-id="70910-105">222</span></span>|  
|<span data-ttu-id="70910-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="70910-106">Keywords</span></span>|<span data-ttu-id="70910-107">EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="70910-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="70910-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="70910-108">Level</span></span>|<span data-ttu-id="70910-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="70910-109">Warning</span></span>|  
|<span data-ttu-id="70910-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="70910-110">Channel</span></span>|<span data-ttu-id="70910-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="70910-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="70910-112">Popis</span><span class="sxs-lookup"><span data-stu-id="70910-112">Description</span></span>  
 <span data-ttu-id="70910-113">Tato událost je vygenerované při výchozí Model služby `OperationInvoker` došlo k výjimce při volání její metody.</span><span class="sxs-lookup"><span data-stu-id="70910-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="70910-114">Poznámka: Tento výjimky, které jsou odvozeny od `FaultException` způsobit tuto událost, chcete-li nebyla vygenerované.</span><span class="sxs-lookup"><span data-stu-id="70910-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="70910-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="70910-115">Message</span></span>  
 <span data-ttu-id="70910-116">Metoda "%1, došlo k neošetřené výjimce při vyvolané OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="70910-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="70910-117">Doba trvání volání metoda byla ms '%2'.</span><span class="sxs-lookup"><span data-stu-id="70910-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="70910-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="70910-118">Details</span></span>  
  
|<span data-ttu-id="70910-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="70910-119">Data Item Name</span></span>|<span data-ttu-id="70910-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="70910-120">Data Item Type</span></span>|<span data-ttu-id="70910-121">Popis</span><span class="sxs-lookup"><span data-stu-id="70910-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="70910-122">Název metody</span><span class="sxs-lookup"><span data-stu-id="70910-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="70910-123">CLR název metody, který byl vyvolán `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="70910-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="70910-124">Doba trvání</span><span class="sxs-lookup"><span data-stu-id="70910-124">Duration</span></span>|`xs:long`|<span data-ttu-id="70910-125">Čas v milisekundách, po které trvalo `OperationInvoker` k vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="70910-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="70910-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="70910-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="70910-127">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="70910-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="70910-128">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="70910-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="70910-129">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="70910-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="70910-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="70910-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="70910-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="70910-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
