---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781807"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="7d011-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="7d011-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="7d011-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7d011-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d011-104">ID</span><span class="sxs-lookup"><span data-stu-id="7d011-104">ID</span></span>|<span data-ttu-id="7d011-105">216</span><span class="sxs-lookup"><span data-stu-id="7d011-105">216</span></span>|  
|<span data-ttu-id="7d011-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7d011-106">Keywords</span></span>|<span data-ttu-id="7d011-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7d011-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7d011-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="7d011-108">Level</span></span>|<span data-ttu-id="7d011-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="7d011-109">Information</span></span>|  
|<span data-ttu-id="7d011-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="7d011-110">Channel</span></span>|<span data-ttu-id="7d011-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="7d011-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7d011-112">Popis</span><span class="sxs-lookup"><span data-stu-id="7d011-112">Description</span></span>  
 <span data-ttu-id="7d011-113">Při přenosu protokolu TCP odešle zprávu dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="7d011-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="7d011-114">Všimněte si, že na úrovni přenosu více zpráv nelze vyměňovat mezi klienty a služby pro jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="7d011-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="7d011-115">To může být způsobeno chování infrastrukturu, zabezpečení je dobrým příkladem.</span><span class="sxs-lookup"><span data-stu-id="7d011-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="7d011-116">Proto, počet **MessageSentByTransport** události, které jsou emitovány lišit v závislosti na vaší služby vazby a jeho konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7d011-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7d011-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="7d011-117">Message</span></span>  
 <span data-ttu-id="7d011-118">Přenos odeslal zprávu na '%1'.</span><span class="sxs-lookup"><span data-stu-id="7d011-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7d011-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="7d011-119">Details</span></span>  
  
|<span data-ttu-id="7d011-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="7d011-120">Data Item Name</span></span>|<span data-ttu-id="7d011-121">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="7d011-121">Data Item Type</span></span>|<span data-ttu-id="7d011-122">Popis</span><span class="sxs-lookup"><span data-stu-id="7d011-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7d011-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="7d011-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="7d011-124">Adresa, která byla zaslána zpráva požadavku.</span><span class="sxs-lookup"><span data-stu-id="7d011-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="7d011-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="7d011-125">HostReference</span></span>|<span data-ttu-id="7d011-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="7d011-126">xs:string</span></span>|<span data-ttu-id="7d011-127">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="7d011-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7d011-128">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="7d011-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7d011-129">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="7d011-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7d011-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7d011-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7d011-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="7d011-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
