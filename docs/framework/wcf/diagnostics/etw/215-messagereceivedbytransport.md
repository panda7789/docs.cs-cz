---
title: 215 – MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781833"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="e685a-102">215 – MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="e685a-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="e685a-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e685a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e685a-104">ID</span><span class="sxs-lookup"><span data-stu-id="e685a-104">ID</span></span>|<span data-ttu-id="e685a-105">215</span><span class="sxs-lookup"><span data-stu-id="e685a-105">215</span></span>|  
|<span data-ttu-id="e685a-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e685a-106">Keywords</span></span>|<span data-ttu-id="e685a-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e685a-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e685a-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e685a-108">Level</span></span>|<span data-ttu-id="e685a-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="e685a-109">Information</span></span>|  
|<span data-ttu-id="e685a-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e685a-110">Channel</span></span>|<span data-ttu-id="e685a-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e685a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e685a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e685a-112">Description</span></span>  
 <span data-ttu-id="e685a-113">Při přenosu protokolu TCP přijme zprávu dojde k této události.</span><span class="sxs-lookup"><span data-stu-id="e685a-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="e685a-114">Všimněte si, že na úrovni přenosu, více zpráv nelze vyměňovat mezi klienty a služby pro jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="e685a-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="e685a-115">To může být způsobeno chování infrastrukturu, zabezpečení je dobrým příkladem.</span><span class="sxs-lookup"><span data-stu-id="e685a-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="e685a-116">Proto, počet `MessageReceivedByTransport` události, které jsou emitovány lišit v závislosti na vaší služby vazby a jeho konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e685a-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e685a-117">Tato událost není aktivováno pro jednosměrnou přenosy.</span><span class="sxs-lookup"><span data-stu-id="e685a-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e685a-118">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e685a-118">Message</span></span>  
 <span data-ttu-id="e685a-119">Přenos obdržel zprávu od '%1'.</span><span class="sxs-lookup"><span data-stu-id="e685a-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e685a-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e685a-120">Details</span></span>  
  
|<span data-ttu-id="e685a-121">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e685a-121">Data Item Name</span></span>|<span data-ttu-id="e685a-122">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="e685a-122">Data Item Type</span></span>|<span data-ttu-id="e685a-123">Popis</span><span class="sxs-lookup"><span data-stu-id="e685a-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e685a-124">Adresa naslouchání</span><span class="sxs-lookup"><span data-stu-id="e685a-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="e685a-125">Adresa, která se zobrazila zpráva.</span><span class="sxs-lookup"><span data-stu-id="e685a-125">The address that received the message.</span></span>|  
|<span data-ttu-id="e685a-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="e685a-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="e685a-127">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="e685a-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e685a-128">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="e685a-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e685a-129">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="e685a-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e685a-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e685a-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e685a-131">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e685a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
