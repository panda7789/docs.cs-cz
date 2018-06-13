---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 02d4a4ed1e96983e132a1943dd39f9f885e5596a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458803"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="00896-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="00896-102">212 - ParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="00896-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="00896-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="00896-104">ID</span><span class="sxs-lookup"><span data-stu-id="00896-104">ID</span></span>|<span data-ttu-id="00896-105">212</span><span class="sxs-lookup"><span data-stu-id="00896-105">212</span></span>|  
|<span data-ttu-id="00896-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="00896-106">Keywords</span></span>|<span data-ttu-id="00896-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="00896-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="00896-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="00896-108">Level</span></span>|<span data-ttu-id="00896-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="00896-109">Information</span></span>|  
|<span data-ttu-id="00896-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="00896-110">Channel</span></span>|<span data-ttu-id="00896-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="00896-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="00896-112">Popis</span><span class="sxs-lookup"><span data-stu-id="00896-112">Description</span></span>  
 <span data-ttu-id="00896-113">Tato událost je vygenerované po Model služby má vyvolat `BeforeCall` metodu `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="00896-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="00896-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="00896-114">Message</span></span>  
 <span data-ttu-id="00896-115">Dispečer vyvolat 'BeforeCall' na ParameterInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="00896-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="00896-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="00896-116">Details</span></span>  
  
|<span data-ttu-id="00896-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="00896-117">Data Item Name</span></span>|<span data-ttu-id="00896-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="00896-118">Data Item Type</span></span>|<span data-ttu-id="00896-119">Popis</span><span class="sxs-lookup"><span data-stu-id="00896-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="00896-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="00896-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="00896-121">Položka FullName CLR vyvolaná inspector typu.</span><span class="sxs-lookup"><span data-stu-id="00896-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="00896-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="00896-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="00896-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="00896-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="00896-124">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="00896-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="00896-125">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="00896-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="00896-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="00896-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="00896-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="00896-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
