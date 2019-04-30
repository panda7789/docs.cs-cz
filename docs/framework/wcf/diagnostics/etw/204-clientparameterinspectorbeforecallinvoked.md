---
title: 204 – ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: eb060cfa79b75452deae67705126a24b7ca9ffef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782034"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="0e005-102">204 – ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="0e005-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="0e005-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0e005-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e005-104">ID</span><span class="sxs-lookup"><span data-stu-id="0e005-104">ID</span></span>|<span data-ttu-id="0e005-105">204</span><span class="sxs-lookup"><span data-stu-id="0e005-105">204</span></span>|  
|<span data-ttu-id="0e005-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0e005-106">Keywords</span></span>|<span data-ttu-id="0e005-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0e005-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0e005-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="0e005-108">Level</span></span>|<span data-ttu-id="0e005-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="0e005-109">Information</span></span>|  
|<span data-ttu-id="0e005-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="0e005-110">Channel</span></span>|<span data-ttu-id="0e005-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="0e005-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0e005-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0e005-112">Description</span></span>  
 <span data-ttu-id="0e005-113">Tato událost je vygenerován po má Model služby `BeforeCall` metodu na inspektoru parametru klienta.</span><span class="sxs-lookup"><span data-stu-id="0e005-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0e005-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0e005-114">Message</span></span>  
 <span data-ttu-id="0e005-115">Dispečer vyvolal metodu 'BeforeCall"na třídě ClientParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="0e005-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0e005-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0e005-116">Details</span></span>  
  
|<span data-ttu-id="0e005-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="0e005-117">Data Item Name</span></span>|<span data-ttu-id="0e005-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="0e005-118">Data Item Type</span></span>|<span data-ttu-id="0e005-119">Popis</span><span class="sxs-lookup"><span data-stu-id="0e005-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0e005-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="0e005-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="0e005-121">Celý název CLR typu vyvolaný inspector.</span><span class="sxs-lookup"><span data-stu-id="0e005-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="0e005-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="0e005-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="0e005-123">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="0e005-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0e005-124">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="0e005-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0e005-125">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="0e005-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0e005-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0e005-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0e005-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0e005-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
