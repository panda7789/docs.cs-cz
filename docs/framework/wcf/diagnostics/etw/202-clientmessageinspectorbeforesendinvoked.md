---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 98de1d7e8e5e87ec7fbd783092f7fbc212fec65d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459352"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="60984-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="60984-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="60984-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="60984-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="60984-104">ID</span><span class="sxs-lookup"><span data-stu-id="60984-104">ID</span></span>|<span data-ttu-id="60984-105">202</span><span class="sxs-lookup"><span data-stu-id="60984-105">202</span></span>|  
|<span data-ttu-id="60984-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="60984-106">Keywords</span></span>|<span data-ttu-id="60984-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="60984-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="60984-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="60984-108">Level</span></span>|<span data-ttu-id="60984-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="60984-109">Information</span></span>|  
|<span data-ttu-id="60984-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="60984-110">Channel</span></span>|<span data-ttu-id="60984-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="60984-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="60984-112">Popis</span><span class="sxs-lookup"><span data-stu-id="60984-112">Description</span></span>  
 <span data-ttu-id="60984-113">Tato událost je vygenerované po Model služby má vyvolat `BeforeSendRequest` metodu na zpráva inspector klienta.</span><span class="sxs-lookup"><span data-stu-id="60984-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="60984-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="60984-114">Message</span></span>  
 <span data-ttu-id="60984-115">Dispečer vyvolat 'BeforeSendRequest' na ClientMessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="60984-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="60984-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="60984-116">Details</span></span>  
  
|<span data-ttu-id="60984-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="60984-117">Data Item Name</span></span>|<span data-ttu-id="60984-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="60984-118">Data Item Type</span></span>|<span data-ttu-id="60984-119">Popis</span><span class="sxs-lookup"><span data-stu-id="60984-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="60984-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="60984-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="60984-121">Položka FullName CLR vyvolaná inspector typu.</span><span class="sxs-lookup"><span data-stu-id="60984-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="60984-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="60984-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="60984-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="60984-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="60984-124">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="60984-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="60984-125">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="60984-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="60984-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="60984-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="60984-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="60984-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
