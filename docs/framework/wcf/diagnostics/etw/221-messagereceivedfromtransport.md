---
title: 221 – MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781716"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="58517-102">221 – MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="58517-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="58517-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="58517-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58517-104">ID</span><span class="sxs-lookup"><span data-stu-id="58517-104">ID</span></span>|<span data-ttu-id="58517-105">221</span><span class="sxs-lookup"><span data-stu-id="58517-105">221</span></span>|  
|<span data-ttu-id="58517-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="58517-106">Keywords</span></span>|<span data-ttu-id="58517-107">EndToEndMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="58517-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="58517-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="58517-108">Level</span></span>|<span data-ttu-id="58517-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="58517-109">Information</span></span>|  
|<span data-ttu-id="58517-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="58517-110">Channel</span></span>|<span data-ttu-id="58517-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="58517-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="58517-112">Popis</span><span class="sxs-lookup"><span data-stu-id="58517-112">Description</span></span>  
 <span data-ttu-id="58517-113">Tato událost je vygenerován, když modelu služby obdrží zprávu od přenosu.</span><span class="sxs-lookup"><span data-stu-id="58517-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="58517-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="58517-114">Message</span></span>  
 <span data-ttu-id="58517-115">Dispečer obdržel zprávu od přenosu.</span><span class="sxs-lookup"><span data-stu-id="58517-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="58517-116">ID korelace == '%1'.</span><span class="sxs-lookup"><span data-stu-id="58517-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="58517-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="58517-117">Details</span></span>  
  
|<span data-ttu-id="58517-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="58517-118">Data Item Name</span></span>|<span data-ttu-id="58517-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="58517-119">Data Item Type</span></span>|<span data-ttu-id="58517-120">Popis</span><span class="sxs-lookup"><span data-stu-id="58517-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="58517-121">ID korelace</span><span class="sxs-lookup"><span data-stu-id="58517-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="58517-122">Aktivita ID použít ke korelaci `MessageSentToTransport` událostí ze služby ani klienta k jeho odpovídajícím `MessageReceivedFromTransport` na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="58517-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="58517-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="58517-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="58517-124">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="58517-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="58517-125">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="58517-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="58517-126">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="58517-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="58517-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="58517-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="58517-128">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="58517-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
