---
title: 223 - OperationFaulted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0428d90135823761e7b8a12f560786e34e12734
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="309e7-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="309e7-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="309e7-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="309e7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="309e7-104">ID</span><span class="sxs-lookup"><span data-stu-id="309e7-104">ID</span></span>|<span data-ttu-id="309e7-105">223</span><span class="sxs-lookup"><span data-stu-id="309e7-105">223</span></span>|  
|<span data-ttu-id="309e7-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="309e7-106">Keywords</span></span>|<span data-ttu-id="309e7-107">EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="309e7-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="309e7-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="309e7-108">Level</span></span>|<span data-ttu-id="309e7-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="309e7-109">Warning</span></span>|  
|<span data-ttu-id="309e7-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="309e7-110">Channel</span></span>|<span data-ttu-id="309e7-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="309e7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="309e7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="309e7-112">Description</span></span>  
 <span data-ttu-id="309e7-113">Tato událost je vygenerované při výchozí Model služby `OperationInvoker` došlo k výjimce odvozování z `FaultException` při vyvolání příslušnou metodu.</span><span class="sxs-lookup"><span data-stu-id="309e7-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="309e7-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="309e7-114">Message</span></span>  
 <span data-ttu-id="309e7-115">Metoda "%1" způsobila FaultException při vyvolané OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="309e7-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="309e7-116">Doba trvání volání metoda byla ms '%2'.</span><span class="sxs-lookup"><span data-stu-id="309e7-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="309e7-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="309e7-117">Details</span></span>  
  
|<span data-ttu-id="309e7-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="309e7-118">Data Item Name</span></span>|<span data-ttu-id="309e7-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="309e7-119">Data Item Type</span></span>|<span data-ttu-id="309e7-120">Popis</span><span class="sxs-lookup"><span data-stu-id="309e7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="309e7-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="309e7-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="309e7-122">CLR název metody, který byl vyvolán `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="309e7-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="309e7-123">Doba trvání</span><span class="sxs-lookup"><span data-stu-id="309e7-123">Duration</span></span>|`xs:long`|<span data-ttu-id="309e7-124">Čas v milisekundách, po které trvalo `OperationInvoker` k vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="309e7-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="309e7-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="309e7-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="309e7-126">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="309e7-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="309e7-127">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="309e7-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="309e7-128">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="309e7-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="309e7-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="309e7-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="309e7-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="309e7-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
