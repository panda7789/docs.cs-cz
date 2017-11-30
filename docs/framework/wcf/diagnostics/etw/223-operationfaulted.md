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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a04ed11db97d02a90e016ee1825b303375a23412
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="223---operationfaulted"></a><span data-ttu-id="06649-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="06649-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="06649-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="06649-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06649-104">ID</span><span class="sxs-lookup"><span data-stu-id="06649-104">ID</span></span>|<span data-ttu-id="06649-105">223</span><span class="sxs-lookup"><span data-stu-id="06649-105">223</span></span>|  
|<span data-ttu-id="06649-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="06649-106">Keywords</span></span>|<span data-ttu-id="06649-107">EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="06649-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="06649-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="06649-108">Level</span></span>|<span data-ttu-id="06649-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="06649-109">Warning</span></span>|  
|<span data-ttu-id="06649-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="06649-110">Channel</span></span>|<span data-ttu-id="06649-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="06649-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="06649-112">Popis</span><span class="sxs-lookup"><span data-stu-id="06649-112">Description</span></span>  
 <span data-ttu-id="06649-113">Tato událost je vygenerované při výchozí Model služby `OperationInvoker` došlo k výjimce odvozování z `FaultException` při vyvolání příslušnou metodu.</span><span class="sxs-lookup"><span data-stu-id="06649-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="06649-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="06649-114">Message</span></span>  
 <span data-ttu-id="06649-115">Metoda "%1" způsobila FaultException při vyvolané OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="06649-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="06649-116">Doba trvání volání metoda byla ms '%2'.</span><span class="sxs-lookup"><span data-stu-id="06649-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="06649-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="06649-117">Details</span></span>  
  
|<span data-ttu-id="06649-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="06649-118">Data Item Name</span></span>|<span data-ttu-id="06649-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="06649-119">Data Item Type</span></span>|<span data-ttu-id="06649-120">Popis</span><span class="sxs-lookup"><span data-stu-id="06649-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="06649-121">MethodName</span><span class="sxs-lookup"><span data-stu-id="06649-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="06649-122">CLR název metody, který byl vyvolán `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="06649-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="06649-123">Doba trvání</span><span class="sxs-lookup"><span data-stu-id="06649-123">Duration</span></span>|`xs:long`|<span data-ttu-id="06649-124">Čas v milisekundách, po které trvalo `OperationInvoker` k vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="06649-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="06649-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="06649-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="06649-126">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="06649-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="06649-127">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="06649-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="06649-128">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="06649-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="06649-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="06649-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="06649-130">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="06649-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
