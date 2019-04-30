---
title: 209 – MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 24184c24b9affdf3a56d7968c02cf5354d690749
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781875"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="0a1be-102">209 – MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="0a1be-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="0a1be-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0a1be-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0a1be-104">ID</span><span class="sxs-lookup"><span data-stu-id="0a1be-104">ID</span></span>|<span data-ttu-id="0a1be-105">209</span><span class="sxs-lookup"><span data-stu-id="0a1be-105">209</span></span>|  
|<span data-ttu-id="0a1be-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="0a1be-106">Keywords</span></span>|<span data-ttu-id="0a1be-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0a1be-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0a1be-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="0a1be-108">Level</span></span>|<span data-ttu-id="0a1be-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="0a1be-109">Information</span></span>|  
|<span data-ttu-id="0a1be-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="0a1be-110">Channel</span></span>|<span data-ttu-id="0a1be-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="0a1be-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0a1be-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0a1be-112">Description</span></span>  
 <span data-ttu-id="0a1be-113">Tato událost je vygenerován po má Model služby `BeforeSend` metodu na zpráva inspector.</span><span class="sxs-lookup"><span data-stu-id="0a1be-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0a1be-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="0a1be-114">Message</span></span>  
 <span data-ttu-id="0a1be-115">Dispečer vyvolal metodu 'BeforeSendRequest"na třídě MessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="0a1be-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0a1be-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="0a1be-116">Details</span></span>  
  
|<span data-ttu-id="0a1be-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="0a1be-117">Data Item Name</span></span>|<span data-ttu-id="0a1be-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="0a1be-118">Data Item Type</span></span>|<span data-ttu-id="0a1be-119">Popis</span><span class="sxs-lookup"><span data-stu-id="0a1be-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0a1be-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="0a1be-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="0a1be-121">Celý název CLR typu vyvolanou `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="0a1be-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="0a1be-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="0a1be-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="0a1be-123">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="0a1be-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0a1be-124">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="0a1be-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0a1be-125">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="0a1be-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0a1be-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0a1be-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0a1be-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0a1be-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
