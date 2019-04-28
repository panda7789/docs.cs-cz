---
title: 303 – UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61595774"
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="a61f3-102">303 – UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="a61f3-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="a61f3-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a61f3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a61f3-104">ID</span><span class="sxs-lookup"><span data-stu-id="a61f3-104">ID</span></span>|<span data-ttu-id="a61f3-105">303</span><span class="sxs-lookup"><span data-stu-id="a61f3-105">303</span></span>|  
|<span data-ttu-id="a61f3-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a61f3-106">Keywords</span></span>|<span data-ttu-id="a61f3-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="a61f3-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="a61f3-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a61f3-108">Level</span></span>|<span data-ttu-id="a61f3-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="a61f3-109">Information</span></span>|  
|<span data-ttu-id="a61f3-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a61f3-110">Channel</span></span>|<span data-ttu-id="a61f3-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="a61f3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a61f3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a61f3-112">Description</span></span>  
 <span data-ttu-id="a61f3-113">Tato událost je vygenerován z uživatelského kódu.</span><span class="sxs-lookup"><span data-stu-id="a61f3-113">This event is emitted from user code.</span></span> <span data-ttu-id="a61f3-114">Vývojáři mohou vygenerovat tuto událost, pokud dojde k vlastní informační událost ve své službě.</span><span class="sxs-lookup"><span data-stu-id="a61f3-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="a61f3-115">To lze provést pomocí <xref:System.Diagnostics.Eventing> rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="a61f3-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="a61f3-116">Kromě toho je Ukázky WCF, která zabalí toto rozhraní API a ukazuje, jak se správně generovat této události.</span><span class="sxs-lookup"><span data-stu-id="a61f3-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a61f3-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a61f3-117">Message</span></span>  
 <span data-ttu-id="a61f3-118">Název: %1, odkaz: %2, vytížení: %3</span><span class="sxs-lookup"><span data-stu-id="a61f3-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="a61f3-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a61f3-119">Details</span></span>  
  
|<span data-ttu-id="a61f3-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a61f3-120">Data Item Name</span></span>|<span data-ttu-id="a61f3-121">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="a61f3-121">Data Item Type</span></span>|<span data-ttu-id="a61f3-122">Popis</span><span class="sxs-lookup"><span data-stu-id="a61f3-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a61f3-123">Název</span><span class="sxs-lookup"><span data-stu-id="a61f3-123">Name</span></span>|`xs:string`|<span data-ttu-id="a61f3-124">Uživatelem definovaný název události</span><span class="sxs-lookup"><span data-stu-id="a61f3-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="a61f3-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="a61f3-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="a61f3-126">Hostované webové služby Toto pole jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="a61f3-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a61f3-127">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="a61f3-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a61f3-128">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="a61f3-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a61f3-129">datová část</span><span class="sxs-lookup"><span data-stu-id="a61f3-129">Payload</span></span>|`xs:string`|<span data-ttu-id="a61f3-130">Uživatelem definované datové části události.</span><span class="sxs-lookup"><span data-stu-id="a61f3-130">The user-defined payload of the event.</span></span>|
