---
title: 203 – ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: 57192b44a0c3babc77fcca13ad4a1433b85bfdd7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781937"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="b31a3-102">203 – ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="b31a3-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="b31a3-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b31a3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b31a3-104">ID</span><span class="sxs-lookup"><span data-stu-id="b31a3-104">ID</span></span>|<span data-ttu-id="b31a3-105">203</span><span class="sxs-lookup"><span data-stu-id="b31a3-105">203</span></span>|  
|<span data-ttu-id="b31a3-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b31a3-106">Keywords</span></span>|<span data-ttu-id="b31a3-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b31a3-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b31a3-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b31a3-108">Level</span></span>|<span data-ttu-id="b31a3-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="b31a3-109">Information</span></span>|  
|<span data-ttu-id="b31a3-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b31a3-110">Channel</span></span>|<span data-ttu-id="b31a3-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="b31a3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b31a3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b31a3-112">Description</span></span>  
 <span data-ttu-id="b31a3-113">Tato událost je vygenerován po má Model služby `AfterCall` metodu na inspektoru parametru klienta.</span><span class="sxs-lookup"><span data-stu-id="b31a3-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b31a3-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b31a3-114">Message</span></span>  
 <span data-ttu-id="b31a3-115">Dispečer vyvolal metodu 'AfterCall"na třídě ClientParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="b31a3-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b31a3-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b31a3-116">Details</span></span>  
  
|<span data-ttu-id="b31a3-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b31a3-117">Data Item Name</span></span>|<span data-ttu-id="b31a3-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="b31a3-118">Data Item Type</span></span>|<span data-ttu-id="b31a3-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b31a3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b31a3-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="b31a3-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="b31a3-121">Celý název CLR typu vyvolaný inspector.</span><span class="sxs-lookup"><span data-stu-id="b31a3-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="b31a3-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="b31a3-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="b31a3-123">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="b31a3-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b31a3-124">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="b31a3-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b31a3-125">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="b31a3-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b31a3-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b31a3-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b31a3-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b31a3-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
