---
title: 201 – ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 96ca318c141d49e2ac5594d5ee101658a2aa8f21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782030"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="24255-102">201 – ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="24255-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="24255-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="24255-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="24255-104">ID</span><span class="sxs-lookup"><span data-stu-id="24255-104">ID</span></span>|<span data-ttu-id="24255-105">201</span><span class="sxs-lookup"><span data-stu-id="24255-105">201</span></span>|  
|<span data-ttu-id="24255-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="24255-106">Keywords</span></span>|<span data-ttu-id="24255-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="24255-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="24255-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="24255-108">Level</span></span>|<span data-ttu-id="24255-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="24255-109">Information</span></span>|  
|<span data-ttu-id="24255-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="24255-110">Channel</span></span>|<span data-ttu-id="24255-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="24255-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="24255-112">Popis</span><span class="sxs-lookup"><span data-stu-id="24255-112">Description</span></span>  
 <span data-ttu-id="24255-113">Tato událost je vygenerován po má Model služby `AfterReceiveReply` metodu na inspektoru zprávy klienta.</span><span class="sxs-lookup"><span data-stu-id="24255-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="24255-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="24255-114">Message</span></span>  
 <span data-ttu-id="24255-115">Dispečer vyvolal metodu 'AfterReceiveReply"na třídě ClientMessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="24255-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="24255-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="24255-116">Details</span></span>  
  
|<span data-ttu-id="24255-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="24255-117">Data Item Name</span></span>|<span data-ttu-id="24255-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="24255-118">Data Item Type</span></span>|<span data-ttu-id="24255-119">Popis</span><span class="sxs-lookup"><span data-stu-id="24255-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="24255-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="24255-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="24255-121">Celý název CLR typu vyvolaný inspector.</span><span class="sxs-lookup"><span data-stu-id="24255-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="24255-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="24255-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="24255-123">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="24255-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="24255-124">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="24255-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="24255-125">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="24255-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="24255-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="24255-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="24255-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="24255-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
