---
title: 221 – MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458774"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="5adae-102">221 – MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="5adae-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="5adae-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5adae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5adae-104">ID</span><span class="sxs-lookup"><span data-stu-id="5adae-104">ID</span></span>|<span data-ttu-id="5adae-105">221</span><span class="sxs-lookup"><span data-stu-id="5adae-105">221</span></span>|  
|<span data-ttu-id="5adae-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5adae-106">Keywords</span></span>|<span data-ttu-id="5adae-107">EndToEndMonitoring, řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5adae-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5adae-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5adae-108">Level</span></span>|<span data-ttu-id="5adae-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="5adae-109">Information</span></span>|  
|<span data-ttu-id="5adae-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5adae-110">Channel</span></span>|<span data-ttu-id="5adae-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="5adae-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5adae-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5adae-112">Description</span></span>  
 <span data-ttu-id="5adae-113">Tato událost je vygenerované, když Model služby přijme zprávu o z přenosu.</span><span class="sxs-lookup"><span data-stu-id="5adae-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5adae-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5adae-114">Message</span></span>  
 <span data-ttu-id="5adae-115">Dispečer přijala zprávu z přenosu.</span><span class="sxs-lookup"><span data-stu-id="5adae-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="5adae-116">ID korelace == '%1'.</span><span class="sxs-lookup"><span data-stu-id="5adae-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5adae-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5adae-117">Details</span></span>  
  
|<span data-ttu-id="5adae-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5adae-118">Data Item Name</span></span>|<span data-ttu-id="5adae-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="5adae-119">Data Item Type</span></span>|<span data-ttu-id="5adae-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5adae-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5adae-121">ID korelace</span><span class="sxs-lookup"><span data-stu-id="5adae-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="5adae-122">Aktivita ID použít ke korelaci `MessageSentToTransport` událostí ze služby nebo klienta na jeho odpovídající `MessageReceivedFromTransport` na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="5adae-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="5adae-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="5adae-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="5adae-124">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="5adae-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5adae-125">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="5adae-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5adae-126">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="5adae-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5adae-127">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5adae-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5adae-128">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5adae-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
