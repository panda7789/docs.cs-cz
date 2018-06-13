---
title: 203 – ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: 57192b44a0c3babc77fcca13ad4a1433b85bfdd7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458618"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="1e8e1-102">203 – ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="1e8e1-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="1e8e1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1e8e1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1e8e1-104">ID</span><span class="sxs-lookup"><span data-stu-id="1e8e1-104">ID</span></span>|<span data-ttu-id="1e8e1-105">203</span><span class="sxs-lookup"><span data-stu-id="1e8e1-105">203</span></span>|  
|<span data-ttu-id="1e8e1-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1e8e1-106">Keywords</span></span>|<span data-ttu-id="1e8e1-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1e8e1-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1e8e1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="1e8e1-108">Level</span></span>|<span data-ttu-id="1e8e1-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="1e8e1-109">Information</span></span>|  
|<span data-ttu-id="1e8e1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="1e8e1-110">Channel</span></span>|<span data-ttu-id="1e8e1-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="1e8e1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1e8e1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1e8e1-112">Description</span></span>  
 <span data-ttu-id="1e8e1-113">Tato událost je vygenerované po Model služby má vyvolat `AfterCall` metodu inspector parametr klienta.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1e8e1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="1e8e1-114">Message</span></span>  
 <span data-ttu-id="1e8e1-115">Dispečer vyvolat 'AfterCall' na ClientParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1e8e1-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1e8e1-116">Details</span></span>  
  
|<span data-ttu-id="1e8e1-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="1e8e1-117">Data Item Name</span></span>|<span data-ttu-id="1e8e1-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="1e8e1-118">Data Item Type</span></span>|<span data-ttu-id="1e8e1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1e8e1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1e8e1-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="1e8e1-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="1e8e1-121">Položka FullName CLR vyvolaná inspector typu.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="1e8e1-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="1e8e1-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="1e8e1-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1e8e1-124">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1e8e1-125">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1e8e1-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="1e8e1-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1e8e1-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1e8e1-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
