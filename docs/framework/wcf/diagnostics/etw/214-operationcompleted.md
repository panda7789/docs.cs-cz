---
title: 214 – OperationCompleted
ms.date: 03/30/2017
ms.assetid: a6287eef-023f-4816-813c-1802c82366df
ms.openlocfilehash: da1021b674b555b683f8f745f5a2a0073c9567e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967996"
---
# <a name="214---operationcompleted"></a><span data-ttu-id="efec1-102">214 – OperationCompleted</span><span class="sxs-lookup"><span data-stu-id="efec1-102">214 - OperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="efec1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="efec1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="efec1-104">ID</span><span class="sxs-lookup"><span data-stu-id="efec1-104">ID</span></span>|<span data-ttu-id="efec1-105">214</span><span class="sxs-lookup"><span data-stu-id="efec1-105">214</span></span>|  
|<span data-ttu-id="efec1-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="efec1-106">Keywords</span></span>|<span data-ttu-id="efec1-107">HealthMonitoring EndToEndMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="efec1-107">HealthMonitoring, EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="efec1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="efec1-108">Level</span></span>|<span data-ttu-id="efec1-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="efec1-109">Information</span></span>|  
|<span data-ttu-id="efec1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="efec1-110">Channel</span></span>|<span data-ttu-id="efec1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="efec1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="efec1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="efec1-112">Description</span></span>  
 <span data-ttu-id="efec1-113">Tato událost je vygenerován při výchozím modelu služby `OperationInvoker` volání metody byla dokončena bez metody došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="efec1-113">This event is emitted when the Service Model's default `OperationInvoker` has completed a call to a method without that method throwing an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="efec1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="efec1-114">Message</span></span>  
 <span data-ttu-id="efec1-115">Třída OperationInvoker dokončila volání metody '%1'.</span><span class="sxs-lookup"><span data-stu-id="efec1-115">An OperationInvoker completed the call to the '%1' method.</span></span> <span data-ttu-id="efec1-116">Délka volání metody byla ms '%2'.</span><span class="sxs-lookup"><span data-stu-id="efec1-116">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="efec1-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="efec1-117">Details</span></span>  
  
|<span data-ttu-id="efec1-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="efec1-118">Data Item Name</span></span>|<span data-ttu-id="efec1-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="efec1-119">Data Item Type</span></span>|<span data-ttu-id="efec1-120">Popis</span><span class="sxs-lookup"><span data-stu-id="efec1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="efec1-121">Název metody</span><span class="sxs-lookup"><span data-stu-id="efec1-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="efec1-122">Název CLR metody, která byla vyvolána pomocí `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="efec1-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="efec1-123">Doba trvání</span><span class="sxs-lookup"><span data-stu-id="efec1-123">Duration</span></span>|`xs:long`|<span data-ttu-id="efec1-124">Doba v milisekundách, jakou trvalo `OperationInvoker` k vyvolání metody.</span><span class="sxs-lookup"><span data-stu-id="efec1-124">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="efec1-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="efec1-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="efec1-126">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="efec1-126">For web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="efec1-127">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="efec1-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="efec1-128">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="efec1-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="efec1-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="efec1-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="efec1-130">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="efec1-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
