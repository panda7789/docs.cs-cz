---
title: 208 – MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 3499131fcb52f0a0ab6d0e78e165522b7092612f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781898"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="53cab-102">208 – MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="53cab-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="53cab-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="53cab-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="53cab-104">ID</span><span class="sxs-lookup"><span data-stu-id="53cab-104">ID</span></span>|<span data-ttu-id="53cab-105">208</span><span class="sxs-lookup"><span data-stu-id="53cab-105">208</span></span>|  
|<span data-ttu-id="53cab-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="53cab-106">Keywords</span></span>|<span data-ttu-id="53cab-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="53cab-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="53cab-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="53cab-108">Level</span></span>|<span data-ttu-id="53cab-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="53cab-109">Information</span></span>|  
|<span data-ttu-id="53cab-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="53cab-110">Channel</span></span>|<span data-ttu-id="53cab-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="53cab-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="53cab-112">Popis</span><span class="sxs-lookup"><span data-stu-id="53cab-112">Description</span></span>  
 <span data-ttu-id="53cab-113">Tato událost je vygenerován po má Model služby `AfterReceive` metodu na zpráva inspector.</span><span class="sxs-lookup"><span data-stu-id="53cab-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="53cab-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="53cab-114">Message</span></span>  
 <span data-ttu-id="53cab-115">Dispečer vyvolal metodu 'AfterReceiveReply"na třídě MessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="53cab-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="53cab-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="53cab-116">Details</span></span>  
  
|<span data-ttu-id="53cab-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="53cab-117">Data Item Name</span></span>|<span data-ttu-id="53cab-118">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="53cab-118">Data Item Type</span></span>|<span data-ttu-id="53cab-119">Popis</span><span class="sxs-lookup"><span data-stu-id="53cab-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="53cab-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="53cab-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="53cab-121">Celý název CLR typu vyvolanou `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="53cab-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="53cab-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="53cab-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="53cab-123">Toto pole pro hostované webové služby, jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="53cab-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="53cab-124">Jeho formát je definován jako "virtuální cesta aplikace název webu&#124;virtuální cesta služby&#124;ServiceName".</span><span class="sxs-lookup"><span data-stu-id="53cab-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="53cab-125">Příklad: "Výchozí webový server/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService".</span><span class="sxs-lookup"><span data-stu-id="53cab-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="53cab-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="53cab-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="53cab-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="53cab-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
