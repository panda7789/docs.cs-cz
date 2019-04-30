---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 98de1d7e8e5e87ec7fbd783092f7fbc212fec65d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781989"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="83ee7-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="83ee7-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="83ee7-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="83ee7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="83ee7-104">ID</span><span class="sxs-lookup"><span data-stu-id="83ee7-104">ID</span></span>|<span data-ttu-id="83ee7-105">202</span><span class="sxs-lookup"><span data-stu-id="83ee7-105">202</span></span>|  
|<span data-ttu-id="83ee7-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="83ee7-106">Keywords</span></span>|<span data-ttu-id="83ee7-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="83ee7-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="83ee7-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="83ee7-108">Level</span></span>|<span data-ttu-id="83ee7-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="83ee7-109">Information</span></span>|  
|<span data-ttu-id="83ee7-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="83ee7-110">Channel</span></span>|<span data-ttu-id="83ee7-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="83ee7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="83ee7-112">Popis</span><span class="sxs-lookup"><span data-stu-id="83ee7-112">Description</span></span>  
 <span data-ttu-id="83ee7-113">Tato událost je vygenerován po má Model služby `BeforeSendRequest` metodu na inspektoru zprávy klienta.</span><span class="sxs-lookup"><span data-stu-id="83ee7-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="83ee7-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="83ee7-114">Message</span></span>  
 <span data-ttu-id="83ee7-115">Dispečer vyvolal metodu 'BeforeSendRequest"na třídě ClientMessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="83ee7-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="83ee7-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="83ee7-116">Details</span></span>  
  
|<span data-ttu-id="83ee7-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="83ee7-117">Data Item Name</span></span>|<span data-ttu-id="83ee7-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="83ee7-118">Data Item Type</span></span>|<span data-ttu-id="83ee7-119">Popis</span><span class="sxs-lookup"><span data-stu-id="83ee7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="83ee7-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="83ee7-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="83ee7-121">Celý název CLR typu vyvolaný inspector.</span><span class="sxs-lookup"><span data-stu-id="83ee7-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="83ee7-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="83ee7-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="83ee7-123">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="83ee7-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="83ee7-124">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="83ee7-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="83ee7-125">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="83ee7-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="83ee7-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="83ee7-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="83ee7-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="83ee7-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
