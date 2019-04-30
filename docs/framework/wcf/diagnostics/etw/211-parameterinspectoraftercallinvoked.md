---
title: 211 – ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: ada3ced31def2bb821b975e09f50ad83f28d56bf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781859"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="f8981-102">211 – ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="f8981-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="f8981-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f8981-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f8981-104">ID</span><span class="sxs-lookup"><span data-stu-id="f8981-104">ID</span></span>|<span data-ttu-id="f8981-105">211</span><span class="sxs-lookup"><span data-stu-id="f8981-105">211</span></span>|  
|<span data-ttu-id="f8981-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f8981-106">Keywords</span></span>|<span data-ttu-id="f8981-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f8981-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f8981-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="f8981-108">Level</span></span>|<span data-ttu-id="f8981-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="f8981-109">Information</span></span>|  
|<span data-ttu-id="f8981-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="f8981-110">Channel</span></span>|<span data-ttu-id="f8981-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="f8981-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f8981-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f8981-112">Description</span></span>  
 <span data-ttu-id="f8981-113">Tato událost je vygenerován po má Model služby `AfterCall` metoda `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="f8981-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f8981-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f8981-114">Message</span></span>  
 <span data-ttu-id="f8981-115">Dispečer vyvolal metodu 'AfterCall"na třídě ParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="f8981-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f8981-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f8981-116">Details</span></span>  
  
|<span data-ttu-id="f8981-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="f8981-117">Data Item Name</span></span>|<span data-ttu-id="f8981-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="f8981-118">Data Item Type</span></span>|<span data-ttu-id="f8981-119">Popis</span><span class="sxs-lookup"><span data-stu-id="f8981-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f8981-120">Název typu</span><span class="sxs-lookup"><span data-stu-id="f8981-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="f8981-121">Celý název CLR typu vyvolanou `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="f8981-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="f8981-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="f8981-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="f8981-123">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="f8981-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f8981-124">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="f8981-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f8981-125">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="f8981-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f8981-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f8981-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f8981-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f8981-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
