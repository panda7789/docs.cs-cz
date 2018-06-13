---
title: 211 – ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: ada3ced31def2bb821b975e09f50ad83f28d56bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459714"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="effe6-102">211 – ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="effe6-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="effe6-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="effe6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="effe6-104">ID</span><span class="sxs-lookup"><span data-stu-id="effe6-104">ID</span></span>|<span data-ttu-id="effe6-105">211</span><span class="sxs-lookup"><span data-stu-id="effe6-105">211</span></span>|  
|<span data-ttu-id="effe6-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="effe6-106">Keywords</span></span>|<span data-ttu-id="effe6-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="effe6-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="effe6-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="effe6-108">Level</span></span>|<span data-ttu-id="effe6-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="effe6-109">Information</span></span>|  
|<span data-ttu-id="effe6-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="effe6-110">Channel</span></span>|<span data-ttu-id="effe6-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="effe6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="effe6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="effe6-112">Description</span></span>  
 <span data-ttu-id="effe6-113">Tato událost je vygenerované po Model služby má vyvolat `AfterCall` metodu `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="effe6-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="effe6-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="effe6-114">Message</span></span>  
 <span data-ttu-id="effe6-115">Dispečer vyvolat 'AfterCall' na ParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="effe6-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="effe6-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="effe6-116">Details</span></span>  
  
|<span data-ttu-id="effe6-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="effe6-117">Data Item Name</span></span>|<span data-ttu-id="effe6-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="effe6-118">Data Item Type</span></span>|<span data-ttu-id="effe6-119">Popis</span><span class="sxs-lookup"><span data-stu-id="effe6-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="effe6-120">Název typu</span><span class="sxs-lookup"><span data-stu-id="effe6-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="effe6-121">Položka FullName CLR typu vyvolanou `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="effe6-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="effe6-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="effe6-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="effe6-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="effe6-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="effe6-124">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="effe6-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="effe6-125">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="effe6-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="effe6-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="effe6-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="effe6-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="effe6-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
