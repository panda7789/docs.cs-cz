---
title: 223 - OperationFaulted
ms.date: 03/30/2017
ms.assetid: 2f7d89d7-3a6a-40fe-9610-5424eb6bbf61
ms.openlocfilehash: cf4a455d80a1a0ac09e99bad967c1feba3653842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596529"
---
# <a name="223---operationfaulted"></a><span data-ttu-id="f2844-102">223 - OperationFaulted</span><span class="sxs-lookup"><span data-stu-id="f2844-102">223 - OperationFaulted</span></span>
## <a name="properties"></a><span data-ttu-id="f2844-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f2844-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2844-104">ID</span><span class="sxs-lookup"><span data-stu-id="f2844-104">ID</span></span>|<span data-ttu-id="f2844-105">223</span><span class="sxs-lookup"><span data-stu-id="f2844-105">223</span></span>|  
|<span data-ttu-id="f2844-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f2844-106">Keywords</span></span>|<span data-ttu-id="f2844-107">EndToEndMonitoring HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f2844-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f2844-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="f2844-108">Level</span></span>|<span data-ttu-id="f2844-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="f2844-109">Warning</span></span>|  
|<span data-ttu-id="f2844-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="f2844-110">Channel</span></span>|<span data-ttu-id="f2844-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f2844-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f2844-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f2844-112">Description</span></span>  
 <span data-ttu-id="f2844-113">Tato událost je vygenerován při výchozím modelu služby `OperationInvoker` došlo k výjimce odvozený od `FaultException` při vyvolání jeho metody.</span><span class="sxs-lookup"><span data-stu-id="f2844-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception deriving from `FaultException` while invoking its method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f2844-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f2844-114">Message</span></span>  
 <span data-ttu-id="f2844-115">Metoda '%1' generovala výjimku FaultException při vyvolání třídou OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="f2844-115">The '%1' method threw a FaultException when invoked by the OperationInvoker.</span></span> <span data-ttu-id="f2844-116">Délka volání metody byla ms '%2'.</span><span class="sxs-lookup"><span data-stu-id="f2844-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f2844-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f2844-117">Details</span></span>  
  
|<span data-ttu-id="f2844-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="f2844-118">Data Item Name</span></span>|<span data-ttu-id="f2844-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="f2844-119">Data Item Type</span></span>|<span data-ttu-id="f2844-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f2844-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f2844-121">methodName</span><span class="sxs-lookup"><span data-stu-id="f2844-121">MethodName</span></span>|`xs:string`|<span data-ttu-id="f2844-122">Název CLR metody, která byla vyvolána pomocí `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="f2844-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="f2844-123">Doba trvání</span><span class="sxs-lookup"><span data-stu-id="f2844-123">Duration</span></span>|`xs:long`|<span data-ttu-id="f2844-124">Doba v milisekundách, jakou trvalo `OperationInvoker` k vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="f2844-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="f2844-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="f2844-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="f2844-126">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="f2844-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f2844-127">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="f2844-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f2844-128">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="f2844-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f2844-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f2844-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f2844-130">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f2844-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
