---
title: "205 – OperationInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7385d34ac2ed0357e964e992a88f96a6a89b1a26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="205---operationinvoked"></a><span data-ttu-id="aaaaf-102">205 – OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="aaaaf-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="aaaaf-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="aaaaf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aaaaf-104">ID</span><span class="sxs-lookup"><span data-stu-id="aaaaf-104">ID</span></span>|<span data-ttu-id="aaaaf-105">205</span><span class="sxs-lookup"><span data-stu-id="aaaaf-105">205</span></span>|  
|<span data-ttu-id="aaaaf-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="aaaaf-106">Keywords</span></span>|<span data-ttu-id="aaaaf-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aaaaf-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="aaaaf-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="aaaaf-108">Level</span></span>|<span data-ttu-id="aaaaf-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="aaaaf-109">Information</span></span>|  
|<span data-ttu-id="aaaaf-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="aaaaf-110">Channel</span></span>|<span data-ttu-id="aaaaf-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="aaaaf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aaaaf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="aaaaf-112">Description</span></span>  
 <span data-ttu-id="aaaaf-113">Tato událost je vygenerované těsně před výchozí Model služby `OperationInvoker` zahájí volání metody.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aaaaf-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="aaaaf-114">Message</span></span>  
 <span data-ttu-id="aaaaf-115">OperationInvoker volá metodu '%1'.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="aaaaf-116">Informace o subjektu volajícím: '%2'.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aaaaf-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="aaaaf-117">Details</span></span>  
  
|<span data-ttu-id="aaaaf-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="aaaaf-118">Data Item Name</span></span>|<span data-ttu-id="aaaaf-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="aaaaf-119">Data Item Type</span></span>|<span data-ttu-id="aaaaf-120">Popis</span><span class="sxs-lookup"><span data-stu-id="aaaaf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aaaaf-121">Název metody</span><span class="sxs-lookup"><span data-stu-id="aaaaf-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="aaaaf-122">CLR název metody, který byl vyvolán `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="aaaaf-123">Informace o volajícím</span><span class="sxs-lookup"><span data-stu-id="aaaaf-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="aaaaf-124">IP adresa a port číslo klienta ve formátu 'IPAddress:PortNumber'.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="aaaaf-125">Tyto dvě hodnoty se načítají z vlastnosti 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' zprávy v rámci operace.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="aaaaf-126">Všimněte si, že se u vazeb mimo TCP tuto hodnotu `null`.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="aaaaf-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="aaaaf-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="aaaaf-128">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="aaaaf-129">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="aaaaf-130">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="aaaaf-131">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="aaaaf-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="aaaaf-132">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="aaaaf-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
