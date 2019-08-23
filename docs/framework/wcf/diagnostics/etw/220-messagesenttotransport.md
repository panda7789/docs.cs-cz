---
title: 220 – MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 9f95edf42e0b1ec19d2019773def282fc279871b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948287"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="2a8b2-102">220 – MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="2a8b2-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="2a8b2-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2a8b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a8b2-104">Id</span><span class="sxs-lookup"><span data-stu-id="2a8b2-104">Id</span></span>|<span data-ttu-id="2a8b2-105">220</span><span class="sxs-lookup"><span data-stu-id="2a8b2-105">220</span></span>|  
|<span data-ttu-id="2a8b2-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="2a8b2-106">Keywords</span></span>|<span data-ttu-id="2a8b2-107">EndToEndMonitoring, řešení potíží, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2a8b2-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2a8b2-108">Level</span><span class="sxs-lookup"><span data-stu-id="2a8b2-108">Level</span></span>|<span data-ttu-id="2a8b2-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="2a8b2-109">Information</span></span>|  
|<span data-ttu-id="2a8b2-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="2a8b2-110">Channel</span></span>|<span data-ttu-id="2a8b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="2a8b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a8b2-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2a8b2-112">Description</span></span>  
 <span data-ttu-id="2a8b2-113">Tato událost je generována, když model služby pošle zprávu na přenos.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a8b2-114">Tato událost nebude vygenerována pro jednosměrná přenos.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a8b2-115">Message</span><span class="sxs-lookup"><span data-stu-id="2a8b2-115">Message</span></span>  
 <span data-ttu-id="2a8b2-116">Dispečer odeslal zprávu přenosu.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="2a8b2-117">ID korelace =% 1.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a8b2-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2a8b2-118">Details</span></span>  
  
|<span data-ttu-id="2a8b2-119">Název datové položky</span><span class="sxs-lookup"><span data-stu-id="2a8b2-119">Data Item Name</span></span>|<span data-ttu-id="2a8b2-120">Typ datové položky</span><span class="sxs-lookup"><span data-stu-id="2a8b2-120">Data Item Type</span></span>|<span data-ttu-id="2a8b2-121">Popis</span><span class="sxs-lookup"><span data-stu-id="2a8b2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a8b2-122">ID korelace</span><span class="sxs-lookup"><span data-stu-id="2a8b2-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="2a8b2-123">ID aktivity, které se používá ke korelaci `MessageSentToTransport` události ze služby nebo klienta s odpovídajícím `MessageReceivedFromTransport` na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="2a8b2-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="2a8b2-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="2a8b2-125">V případě služeb hostovaných na webu toto pole jedinečně identifikuje službu ve webové hierarchii.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2a8b2-126">Jeho formát je definován jako název webové stránky služba virtuální cesta&#124;&#124;ServiceName.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2a8b2-127">Příklad: ' Výchozí web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '.</span><span class="sxs-lookup"><span data-stu-id="2a8b2-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2a8b2-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2a8b2-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2a8b2-129">Řetězec vrácený třídou AppDomain. CurrentDomain. FriendlyName</span><span class="sxs-lookup"><span data-stu-id="2a8b2-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
