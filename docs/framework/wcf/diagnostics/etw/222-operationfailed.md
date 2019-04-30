---
title: 222 – OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781638"
---
# <a name="222---operationfailed"></a><span data-ttu-id="6bade-102">222 – OperationFailed</span><span class="sxs-lookup"><span data-stu-id="6bade-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="6bade-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6bade-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6bade-104">ID</span><span class="sxs-lookup"><span data-stu-id="6bade-104">ID</span></span>|<span data-ttu-id="6bade-105">222</span><span class="sxs-lookup"><span data-stu-id="6bade-105">222</span></span>|  
|<span data-ttu-id="6bade-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6bade-106">Keywords</span></span>|<span data-ttu-id="6bade-107">EndToEndMonitoring HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6bade-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="6bade-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6bade-108">Level</span></span>|<span data-ttu-id="6bade-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="6bade-109">Warning</span></span>|  
|<span data-ttu-id="6bade-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6bade-110">Channel</span></span>|<span data-ttu-id="6bade-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6bade-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6bade-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6bade-112">Description</span></span>  
 <span data-ttu-id="6bade-113">Tato událost je vygenerován při výchozím modelu služby `OperationInvoker` došlo k výjimce při vyvolání jeho metody.</span><span class="sxs-lookup"><span data-stu-id="6bade-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="6bade-114">Poznámka: Tento výjimky, které jsou odvozeny z `FaultException` způsobit, že tato událost nebude vygenerován.</span><span class="sxs-lookup"><span data-stu-id="6bade-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6bade-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6bade-115">Message</span></span>  
 <span data-ttu-id="6bade-116">Metoda '%1' došlo k neošetřené výjimce při vyvolání třídou OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="6bade-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="6bade-117">Délka volání metody byla ms '%2'.</span><span class="sxs-lookup"><span data-stu-id="6bade-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6bade-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6bade-118">Details</span></span>  
  
|<span data-ttu-id="6bade-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6bade-119">Data Item Name</span></span>|<span data-ttu-id="6bade-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="6bade-120">Data Item Type</span></span>|<span data-ttu-id="6bade-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6bade-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6bade-122">Název metody</span><span class="sxs-lookup"><span data-stu-id="6bade-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="6bade-123">Název CLR metody, která byla vyvolána pomocí `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="6bade-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="6bade-124">Doba trvání</span><span class="sxs-lookup"><span data-stu-id="6bade-124">Duration</span></span>|`xs:long`|<span data-ttu-id="6bade-125">Doba v milisekundách, jakou trvalo `OperationInvoker` k vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="6bade-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="6bade-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="6bade-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="6bade-127">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="6bade-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6bade-128">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="6bade-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6bade-129">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="6bade-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6bade-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6bade-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6bade-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6bade-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
