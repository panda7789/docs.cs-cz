---
title: 222 – OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460732"
---
# <a name="222---operationfailed"></a><span data-ttu-id="dcd4a-102">222 – OperationFailed</span><span class="sxs-lookup"><span data-stu-id="dcd4a-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="dcd4a-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dcd4a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dcd4a-104">ID</span><span class="sxs-lookup"><span data-stu-id="dcd4a-104">ID</span></span>|<span data-ttu-id="dcd4a-105">222</span><span class="sxs-lookup"><span data-stu-id="dcd4a-105">222</span></span>|  
|<span data-ttu-id="dcd4a-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="dcd4a-106">Keywords</span></span>|<span data-ttu-id="dcd4a-107">EndToEndMonitoring, HealthMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dcd4a-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="dcd4a-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="dcd4a-108">Level</span></span>|<span data-ttu-id="dcd4a-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="dcd4a-109">Warning</span></span>|  
|<span data-ttu-id="dcd4a-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="dcd4a-110">Channel</span></span>|<span data-ttu-id="dcd4a-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="dcd4a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dcd4a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd4a-112">Description</span></span>  
 <span data-ttu-id="dcd4a-113">Tato událost je vygenerované při výchozí Model služby `OperationInvoker` došlo k výjimce při volání její metody.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="dcd4a-114">Poznámka: Tento výjimky, které jsou odvozeny od `FaultException` způsobit tuto událost, chcete-li nebyla vygenerované.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dcd4a-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="dcd4a-115">Message</span></span>  
 <span data-ttu-id="dcd4a-116">Metoda "%1, došlo k neošetřené výjimce při vyvolané OperationInvoker.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="dcd4a-117">Doba trvání volání metoda byla ms '%2'.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dcd4a-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="dcd4a-118">Details</span></span>  
  
|<span data-ttu-id="dcd4a-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="dcd4a-119">Data Item Name</span></span>|<span data-ttu-id="dcd4a-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="dcd4a-120">Data Item Type</span></span>|<span data-ttu-id="dcd4a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="dcd4a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dcd4a-122">Název metody</span><span class="sxs-lookup"><span data-stu-id="dcd4a-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="dcd4a-123">CLR název metody, který byl vyvolán `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="dcd4a-124">Doba trvání</span><span class="sxs-lookup"><span data-stu-id="dcd4a-124">Duration</span></span>|`xs:long`|<span data-ttu-id="dcd4a-125">Čas v milisekundách, po které trvalo `OperationInvoker` k vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="dcd4a-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="dcd4a-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="dcd4a-127">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="dcd4a-128">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="dcd4a-129">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="dcd4a-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="dcd4a-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="dcd4a-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="dcd4a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
