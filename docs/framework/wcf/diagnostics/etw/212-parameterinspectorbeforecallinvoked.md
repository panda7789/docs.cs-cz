---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d043bbf4b6484e2d2bcc7840fa08ebc371dca02a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="b7769-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="b7769-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="b7769-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b7769-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7769-104">ID</span><span class="sxs-lookup"><span data-stu-id="b7769-104">ID</span></span>|<span data-ttu-id="b7769-105">212</span><span class="sxs-lookup"><span data-stu-id="b7769-105">212</span></span>|  
|<span data-ttu-id="b7769-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="b7769-106">Keywords</span></span>|<span data-ttu-id="b7769-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b7769-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="b7769-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="b7769-108">Level</span></span>|<span data-ttu-id="b7769-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="b7769-109">Information</span></span>|  
|<span data-ttu-id="b7769-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="b7769-110">Channel</span></span>|<span data-ttu-id="b7769-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="b7769-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7769-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b7769-112">Description</span></span>  
 <span data-ttu-id="b7769-113">Tato událost je vygenerované po Model služby má vyvolat `BeforeCall` metodu `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="b7769-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7769-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b7769-114">Message</span></span>  
 <span data-ttu-id="b7769-115">Dispečer vyvolat 'BeforeCall' na ParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="b7769-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7769-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b7769-116">Details</span></span>  
  
|<span data-ttu-id="b7769-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="b7769-117">Data Item Name</span></span>|<span data-ttu-id="b7769-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="b7769-118">Data Item Type</span></span>|<span data-ttu-id="b7769-119">Popis</span><span class="sxs-lookup"><span data-stu-id="b7769-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7769-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="b7769-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="b7769-121">Položka FullName CLR vyvolaná inspector typu.</span><span class="sxs-lookup"><span data-stu-id="b7769-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="b7769-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="b7769-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="b7769-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="b7769-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="b7769-124">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="b7769-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="b7769-125">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="b7769-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="b7769-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="b7769-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="b7769-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b7769-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
