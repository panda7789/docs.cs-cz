---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 02d4a4ed1e96983e132a1943dd39f9f885e5596a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781846"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="db762-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="db762-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="db762-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="db762-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="db762-104">ID</span><span class="sxs-lookup"><span data-stu-id="db762-104">ID</span></span>|<span data-ttu-id="db762-105">212</span><span class="sxs-lookup"><span data-stu-id="db762-105">212</span></span>|  
|<span data-ttu-id="db762-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="db762-106">Keywords</span></span>|<span data-ttu-id="db762-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="db762-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="db762-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="db762-108">Level</span></span>|<span data-ttu-id="db762-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="db762-109">Information</span></span>|  
|<span data-ttu-id="db762-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="db762-110">Channel</span></span>|<span data-ttu-id="db762-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="db762-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="db762-112">Popis</span><span class="sxs-lookup"><span data-stu-id="db762-112">Description</span></span>  
 <span data-ttu-id="db762-113">Tato událost je vygenerován po má Model služby `BeforeCall` metoda `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="db762-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="db762-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="db762-114">Message</span></span>  
 <span data-ttu-id="db762-115">Dispečer vyvolal metodu 'BeforeCall"na třídě ParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="db762-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="db762-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="db762-116">Details</span></span>  
  
|<span data-ttu-id="db762-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="db762-117">Data Item Name</span></span>|<span data-ttu-id="db762-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="db762-118">Data Item Type</span></span>|<span data-ttu-id="db762-119">Popis</span><span class="sxs-lookup"><span data-stu-id="db762-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="db762-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="db762-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="db762-121">Celý název CLR typu vyvolaný inspector.</span><span class="sxs-lookup"><span data-stu-id="db762-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="db762-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="db762-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="db762-123">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="db762-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="db762-124">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="db762-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="db762-125">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="db762-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="db762-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="db762-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="db762-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="db762-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
