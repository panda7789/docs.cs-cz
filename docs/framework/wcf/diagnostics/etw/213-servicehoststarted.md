---
title: 213 – ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781820"
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="9cbaa-102">213 – ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="9cbaa-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="9cbaa-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9cbaa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9cbaa-104">ID</span><span class="sxs-lookup"><span data-stu-id="9cbaa-104">ID</span></span>|<span data-ttu-id="9cbaa-105">213</span><span class="sxs-lookup"><span data-stu-id="9cbaa-105">213</span></span>|  
|<span data-ttu-id="9cbaa-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="9cbaa-106">Keywords</span></span>|<span data-ttu-id="9cbaa-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span><span class="sxs-lookup"><span data-stu-id="9cbaa-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="9cbaa-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="9cbaa-108">Level</span></span>|<span data-ttu-id="9cbaa-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="9cbaa-109">LogAlways</span></span>|  
|<span data-ttu-id="9cbaa-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="9cbaa-110">Channel</span></span>|<span data-ttu-id="9cbaa-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="9cbaa-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9cbaa-112">Popis</span><span class="sxs-lookup"><span data-stu-id="9cbaa-112">Description</span></span>  
 <span data-ttu-id="9cbaa-113">Tato událost je vygenerován při spuštění hostitele webové hostované služby.</span><span class="sxs-lookup"><span data-stu-id="9cbaa-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="9cbaa-114">Obvykle se to stane, když je služba aktivovaná zpráva.</span><span class="sxs-lookup"><span data-stu-id="9cbaa-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="9cbaa-115">Může také dojít, pokud služba je nakonfigurována na automatické spuštění.</span><span class="sxs-lookup"><span data-stu-id="9cbaa-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9cbaa-116">Zpráva</span><span class="sxs-lookup"><span data-stu-id="9cbaa-116">Message</span></span>  
 <span data-ttu-id="9cbaa-117">Třída ServiceHost byla spuštěna: '%1'.</span><span class="sxs-lookup"><span data-stu-id="9cbaa-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9cbaa-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="9cbaa-118">Details</span></span>  
  
|<span data-ttu-id="9cbaa-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="9cbaa-119">Data Item Name</span></span>|<span data-ttu-id="9cbaa-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="9cbaa-120">Data Item Type</span></span>|<span data-ttu-id="9cbaa-121">Popis</span><span class="sxs-lookup"><span data-stu-id="9cbaa-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9cbaa-122">Název typu služby</span><span class="sxs-lookup"><span data-stu-id="9cbaa-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="9cbaa-123">Celý název CLR typu implementace služby.</span><span class="sxs-lookup"><span data-stu-id="9cbaa-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="9cbaa-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="9cbaa-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="9cbaa-125">Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="9cbaa-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9cbaa-126">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="9cbaa-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9cbaa-127">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="9cbaa-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9cbaa-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9cbaa-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9cbaa-129">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9cbaa-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
