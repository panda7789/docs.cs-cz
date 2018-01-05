---
title: "204 – ClientParameterInspectorBeforeCallInvoked"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a25315a6008be69aeb534b8bf26c0e813c00c01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="56a23-102">204 – ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="56a23-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="56a23-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="56a23-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56a23-104">ID</span><span class="sxs-lookup"><span data-stu-id="56a23-104">ID</span></span>|<span data-ttu-id="56a23-105">204</span><span class="sxs-lookup"><span data-stu-id="56a23-105">204</span></span>|  
|<span data-ttu-id="56a23-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="56a23-106">Keywords</span></span>|<span data-ttu-id="56a23-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="56a23-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="56a23-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="56a23-108">Level</span></span>|<span data-ttu-id="56a23-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="56a23-109">Information</span></span>|  
|<span data-ttu-id="56a23-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="56a23-110">Channel</span></span>|<span data-ttu-id="56a23-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="56a23-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="56a23-112">Popis</span><span class="sxs-lookup"><span data-stu-id="56a23-112">Description</span></span>  
 <span data-ttu-id="56a23-113">Tato událost je vygenerované po Model služby má vyvolat `BeforeCall` metodu inspector parametr klienta.</span><span class="sxs-lookup"><span data-stu-id="56a23-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="56a23-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="56a23-114">Message</span></span>  
 <span data-ttu-id="56a23-115">Dispečer vyvolat 'BeforeCall' na ClientParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="56a23-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="56a23-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="56a23-116">Details</span></span>  
  
|<span data-ttu-id="56a23-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="56a23-117">Data Item Name</span></span>|<span data-ttu-id="56a23-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="56a23-118">Data Item Type</span></span>|<span data-ttu-id="56a23-119">Popis</span><span class="sxs-lookup"><span data-stu-id="56a23-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="56a23-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="56a23-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="56a23-121">Položka FullName CLR vyvolaná inspector typu.</span><span class="sxs-lookup"><span data-stu-id="56a23-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="56a23-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="56a23-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="56a23-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="56a23-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="56a23-124">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="56a23-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="56a23-125">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="56a23-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="56a23-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="56a23-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="56a23-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="56a23-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
