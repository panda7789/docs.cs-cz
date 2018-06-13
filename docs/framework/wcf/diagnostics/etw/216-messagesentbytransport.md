---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458680"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="e7a4b-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="e7a4b-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="e7a4b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e7a4b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e7a4b-104">ID</span><span class="sxs-lookup"><span data-stu-id="e7a4b-104">ID</span></span>|<span data-ttu-id="e7a4b-105">216</span><span class="sxs-lookup"><span data-stu-id="e7a4b-105">216</span></span>|  
|<span data-ttu-id="e7a4b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e7a4b-106">Keywords</span></span>|<span data-ttu-id="e7a4b-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e7a4b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e7a4b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e7a4b-108">Level</span></span>|<span data-ttu-id="e7a4b-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="e7a4b-109">Information</span></span>|  
|<span data-ttu-id="e7a4b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e7a4b-110">Channel</span></span>|<span data-ttu-id="e7a4b-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e7a4b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e7a4b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e7a4b-112">Description</span></span>  
 <span data-ttu-id="e7a4b-113">K této události dojde, když přenos protokolu TCP odešle zprávu.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="e7a4b-114">Všimněte si, že na úrovni přenosu může být více zpráv vyměňují mezi klienty a služby pro jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="e7a4b-115">Může to být způsobeno chování infrastruktury, je dobrým příkladem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="e7a4b-116">Proto počet **MessageSentByTransport** události, které jsou vygenerované lišit v závislosti na vaší služby vazby a jeho konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e7a4b-117">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e7a4b-117">Message</span></span>  
 <span data-ttu-id="e7a4b-118">Přenos neodeslal zprávu na '%1'.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e7a4b-119">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e7a4b-119">Details</span></span>  
  
|<span data-ttu-id="e7a4b-120">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e7a4b-120">Data Item Name</span></span>|<span data-ttu-id="e7a4b-121">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="e7a4b-121">Data Item Type</span></span>|<span data-ttu-id="e7a4b-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e7a4b-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e7a4b-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="e7a4b-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="e7a4b-124">Adresa, který vám byl zaslán zprávu požadavku.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="e7a4b-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="e7a4b-125">HostReference</span></span>|<span data-ttu-id="e7a4b-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="e7a4b-126">xs:string</span></span>|<span data-ttu-id="e7a4b-127">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e7a4b-128">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e7a4b-129">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e7a4b-130">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="e7a4b-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e7a4b-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e7a4b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
