---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: baf466bf63dcb9335a20eed8b563c222e09c7055
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="a1d0f-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="a1d0f-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="a1d0f-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a1d0f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a1d0f-104">ID</span><span class="sxs-lookup"><span data-stu-id="a1d0f-104">ID</span></span>|<span data-ttu-id="a1d0f-105">202</span><span class="sxs-lookup"><span data-stu-id="a1d0f-105">202</span></span>|  
|<span data-ttu-id="a1d0f-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a1d0f-106">Keywords</span></span>|<span data-ttu-id="a1d0f-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a1d0f-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a1d0f-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a1d0f-108">Level</span></span>|<span data-ttu-id="a1d0f-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="a1d0f-109">Information</span></span>|  
|<span data-ttu-id="a1d0f-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a1d0f-110">Channel</span></span>|<span data-ttu-id="a1d0f-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="a1d0f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a1d0f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a1d0f-112">Description</span></span>  
 <span data-ttu-id="a1d0f-113">Tato událost je vygenerované po Model služby má vyvolat `BeforeSendRequest` metodu na zpráva inspector klienta.</span><span class="sxs-lookup"><span data-stu-id="a1d0f-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a1d0f-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a1d0f-114">Message</span></span>  
 <span data-ttu-id="a1d0f-115">Dispečer vyvolat 'BeforeSendRequest' na ClientMessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="a1d0f-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a1d0f-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a1d0f-116">Details</span></span>  
  
|<span data-ttu-id="a1d0f-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a1d0f-117">Data Item Name</span></span>|<span data-ttu-id="a1d0f-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="a1d0f-118">Data Item Type</span></span>|<span data-ttu-id="a1d0f-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a1d0f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a1d0f-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="a1d0f-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="a1d0f-121">Položka FullName CLR vyvolaná inspector typu.</span><span class="sxs-lookup"><span data-stu-id="a1d0f-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="a1d0f-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="a1d0f-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="a1d0f-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="a1d0f-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a1d0f-124">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="a1d0f-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a1d0f-125">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="a1d0f-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a1d0f-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a1d0f-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a1d0f-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a1d0f-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
