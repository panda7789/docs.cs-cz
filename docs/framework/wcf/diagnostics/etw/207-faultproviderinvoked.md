---
title: 207 – FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 9f97e74e7685d57b487f456625826ee9cd8e1760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457345"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="66ef7-102">207 – FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="66ef7-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="66ef7-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="66ef7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66ef7-104">ID</span><span class="sxs-lookup"><span data-stu-id="66ef7-104">ID</span></span>|<span data-ttu-id="66ef7-105">207</span><span class="sxs-lookup"><span data-stu-id="66ef7-105">207</span></span>|  
|<span data-ttu-id="66ef7-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="66ef7-106">Keywords</span></span>|<span data-ttu-id="66ef7-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="66ef7-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="66ef7-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="66ef7-108">Level</span></span>|<span data-ttu-id="66ef7-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="66ef7-109">Information</span></span>|  
|<span data-ttu-id="66ef7-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="66ef7-110">Channel</span></span>|<span data-ttu-id="66ef7-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="66ef7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="66ef7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="66ef7-112">Description</span></span>  
 <span data-ttu-id="66ef7-113">Tato událost je vygenerované po `FaultProvider` metoda byla volána.</span><span class="sxs-lookup"><span data-stu-id="66ef7-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="66ef7-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="66ef7-114">Message</span></span>  
 <span data-ttu-id="66ef7-115">Dispečer vyvolat FaultProvider typu "%1, s výjimkou typu '%2'.</span><span class="sxs-lookup"><span data-stu-id="66ef7-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="66ef7-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="66ef7-116">Details</span></span>  
  
|<span data-ttu-id="66ef7-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="66ef7-117">Data Item Name</span></span>|<span data-ttu-id="66ef7-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="66ef7-118">Data Item Type</span></span>|<span data-ttu-id="66ef7-119">Popis</span><span class="sxs-lookup"><span data-stu-id="66ef7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="66ef7-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="66ef7-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="66ef7-121">Položka FullName CLR typu vyvolanou `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="66ef7-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="66ef7-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="66ef7-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="66ef7-123">Položka FullName CLR výjimky, `FaultProvider` má zpracovat.</span><span class="sxs-lookup"><span data-stu-id="66ef7-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="66ef7-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="66ef7-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="66ef7-125">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="66ef7-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="66ef7-126">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="66ef7-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="66ef7-127">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="66ef7-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="66ef7-128">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="66ef7-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="66ef7-129">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="66ef7-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
