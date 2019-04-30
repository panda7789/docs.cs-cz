---
title: 220 – MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 92ec664aead15470fbed576bf157d64d984ddebf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781742"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="8220e-102">220 – MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="8220e-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="8220e-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8220e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8220e-104">ID</span><span class="sxs-lookup"><span data-stu-id="8220e-104">Id</span></span>|<span data-ttu-id="8220e-105">220</span><span class="sxs-lookup"><span data-stu-id="8220e-105">220</span></span>|  
|<span data-ttu-id="8220e-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8220e-106">Keywords</span></span>|<span data-ttu-id="8220e-107">EndToEndMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8220e-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8220e-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8220e-108">Level</span></span>|<span data-ttu-id="8220e-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="8220e-109">Information</span></span>|  
|<span data-ttu-id="8220e-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8220e-110">Channel</span></span>|<span data-ttu-id="8220e-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="8220e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8220e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8220e-112">Description</span></span>  
 <span data-ttu-id="8220e-113">Tato událost je vygenerován Model služby odešle zprávu přenosu.</span><span class="sxs-lookup"><span data-stu-id="8220e-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8220e-114">Tato událost nebude se emitovat pro jednosměrnou přenosy.</span><span class="sxs-lookup"><span data-stu-id="8220e-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8220e-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8220e-115">Message</span></span>  
 <span data-ttu-id="8220e-116">Dispečer odeslal zprávu přenosu.</span><span class="sxs-lookup"><span data-stu-id="8220e-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="8220e-117">ID korelace == '%1'.</span><span class="sxs-lookup"><span data-stu-id="8220e-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8220e-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8220e-118">Details</span></span>  
  
|<span data-ttu-id="8220e-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8220e-119">Data Item Name</span></span>|<span data-ttu-id="8220e-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="8220e-120">Data Item Type</span></span>|<span data-ttu-id="8220e-121">Popis</span><span class="sxs-lookup"><span data-stu-id="8220e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8220e-122">ID korelace</span><span class="sxs-lookup"><span data-stu-id="8220e-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="8220e-123">Aktivita ID použít ke korelaci `MessageSentToTransport` událostí ze služby ani klienta k jeho odpovídajícím `MessageReceivedFromTransport` na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="8220e-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="8220e-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="8220e-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="8220e-125">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="8220e-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8220e-126">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="8220e-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8220e-127">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="8220e-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8220e-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8220e-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8220e-129">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8220e-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
