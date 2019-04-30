---
title: 207 – FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 9f97e74e7685d57b487f456625826ee9cd8e1760
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781911"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="50c55-102">207 – FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="50c55-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="50c55-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="50c55-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="50c55-104">ID</span><span class="sxs-lookup"><span data-stu-id="50c55-104">ID</span></span>|<span data-ttu-id="50c55-105">207</span><span class="sxs-lookup"><span data-stu-id="50c55-105">207</span></span>|  
|<span data-ttu-id="50c55-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="50c55-106">Keywords</span></span>|<span data-ttu-id="50c55-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="50c55-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="50c55-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="50c55-108">Level</span></span>|<span data-ttu-id="50c55-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="50c55-109">Information</span></span>|  
|<span data-ttu-id="50c55-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="50c55-110">Channel</span></span>|<span data-ttu-id="50c55-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="50c55-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="50c55-112">Popis</span><span class="sxs-lookup"><span data-stu-id="50c55-112">Description</span></span>  
 <span data-ttu-id="50c55-113">Tato událost je vygenerován po `FaultProvider` zavolání.</span><span class="sxs-lookup"><span data-stu-id="50c55-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="50c55-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="50c55-114">Message</span></span>  
 <span data-ttu-id="50c55-115">Dispečer vyvolal třídu FaultProvider typu '%1' se výjimka typu '%2'.</span><span class="sxs-lookup"><span data-stu-id="50c55-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="50c55-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="50c55-116">Details</span></span>  
  
|<span data-ttu-id="50c55-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="50c55-117">Data Item Name</span></span>|<span data-ttu-id="50c55-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="50c55-118">Data Item Type</span></span>|<span data-ttu-id="50c55-119">Popis</span><span class="sxs-lookup"><span data-stu-id="50c55-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="50c55-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="50c55-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="50c55-121">Celý název CLR typu vyvolanou `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="50c55-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="50c55-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="50c55-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="50c55-123">Celý název CLR výjimky, která `FaultProvider` má zpracovat.</span><span class="sxs-lookup"><span data-stu-id="50c55-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="50c55-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="50c55-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="50c55-125">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="50c55-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="50c55-126">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="50c55-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="50c55-127">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="50c55-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="50c55-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="50c55-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="50c55-129">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="50c55-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
