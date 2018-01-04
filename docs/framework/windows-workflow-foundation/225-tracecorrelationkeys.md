---
title: 225 - TraceCorrelationKeys
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a8d9120c4173d90d7bf6b1ff2054117f80ac96a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="daae8-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="daae8-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="daae8-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="daae8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="daae8-104">ID</span><span class="sxs-lookup"><span data-stu-id="daae8-104">ID</span></span>|<span data-ttu-id="daae8-105">225</span><span class="sxs-lookup"><span data-stu-id="daae8-105">225</span></span>|  
|<span data-ttu-id="daae8-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="daae8-106">Keywords</span></span>|<span data-ttu-id="daae8-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="daae8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="daae8-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="daae8-108">Level</span></span>|<span data-ttu-id="daae8-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="daae8-109">Information</span></span>|  
|<span data-ttu-id="daae8-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="daae8-110">Channel</span></span>|<span data-ttu-id="daae8-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="daae8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="daae8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="daae8-112">Description</span></span>  
 <span data-ttu-id="daae8-113">Tato událost je vygenerované při korelace na základě obsahu se používá pro služby pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="daae8-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="daae8-114">Obsahuje korelace klíčů, které se použijí ke korelaci zprávu, která instance.</span><span class="sxs-lookup"><span data-stu-id="daae8-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="daae8-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="daae8-115">Message</span></span>  
 <span data-ttu-id="daae8-116">Vypočítat korelace klíč '%1' v nadřazeném oboru: %3' pomocí hodnoty '%2'.</span><span class="sxs-lookup"><span data-stu-id="daae8-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="daae8-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="daae8-117">Details</span></span>  
  
|<span data-ttu-id="daae8-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="daae8-118">Data Item Name</span></span>|<span data-ttu-id="daae8-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="daae8-119">Data Item Type</span></span>|<span data-ttu-id="daae8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="daae8-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="daae8-121">Klíč instance</span><span class="sxs-lookup"><span data-stu-id="daae8-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="daae8-122">Klíč, který byl vygenerován z hodnot korelace.</span><span class="sxs-lookup"><span data-stu-id="daae8-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="daae8-123">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="daae8-123">Values</span></span>|`xs:string`|<span data-ttu-id="daae8-124">Hodnoty, které byly použity k výpočtu klíčem instance korelace.</span><span class="sxs-lookup"><span data-stu-id="daae8-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="daae8-125">Nadřazeného oboru</span><span class="sxs-lookup"><span data-stu-id="daae8-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="daae8-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="daae8-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="daae8-127">Webové hostované služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="daae8-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="daae8-128">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="daae8-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="daae8-129">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="daae8-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="daae8-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="daae8-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="daae8-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="daae8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
