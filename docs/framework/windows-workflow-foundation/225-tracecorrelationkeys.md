---
title: 225 – TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755659"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="49665-102">225 – TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="49665-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="49665-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="49665-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="49665-104">ID</span><span class="sxs-lookup"><span data-stu-id="49665-104">ID</span></span>|<span data-ttu-id="49665-105">225</span><span class="sxs-lookup"><span data-stu-id="49665-105">225</span></span>|  
|<span data-ttu-id="49665-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="49665-106">Keywords</span></span>|<span data-ttu-id="49665-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="49665-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="49665-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="49665-108">Level</span></span>|<span data-ttu-id="49665-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="49665-109">Information</span></span>|  
|<span data-ttu-id="49665-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="49665-110">Channel</span></span>|<span data-ttu-id="49665-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="49665-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="49665-112">Popis</span><span class="sxs-lookup"><span data-stu-id="49665-112">Description</span></span>  
 <span data-ttu-id="49665-113">Tato událost je vygenerován při korelace na základě obsahu se používá pro služby pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="49665-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="49665-114">Obsahuje klíče korelace, které se použijí pro korelaci zprávy do instance.</span><span class="sxs-lookup"><span data-stu-id="49665-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="49665-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="49665-115">Message</span></span>  
 <span data-ttu-id="49665-116">Vypočítá klíč korelace '%1' pomocí hodnoty '%2' v nadřazeném oboru '%3'.</span><span class="sxs-lookup"><span data-stu-id="49665-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="49665-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="49665-117">Details</span></span>  
  
|<span data-ttu-id="49665-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="49665-118">Data Item Name</span></span>|<span data-ttu-id="49665-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="49665-119">Data Item Type</span></span>|<span data-ttu-id="49665-120">Popis</span><span class="sxs-lookup"><span data-stu-id="49665-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="49665-121">Klíč instance</span><span class="sxs-lookup"><span data-stu-id="49665-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="49665-122">Klíč, který byl vytvořen hodnoty korelace.</span><span class="sxs-lookup"><span data-stu-id="49665-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="49665-123">Hodnoty</span><span class="sxs-lookup"><span data-stu-id="49665-123">Values</span></span>|`xs:string`|<span data-ttu-id="49665-124">Hodnoty, které byly použity k výpočtu korelace klíč instance.</span><span class="sxs-lookup"><span data-stu-id="49665-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="49665-125">Nadřazený obor</span><span class="sxs-lookup"><span data-stu-id="49665-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="49665-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="49665-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="49665-127">Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="49665-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="49665-128">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="49665-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="49665-129">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="49665-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="49665-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="49665-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="49665-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="49665-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
