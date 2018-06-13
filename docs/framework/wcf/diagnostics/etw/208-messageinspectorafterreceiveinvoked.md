---
title: 208 – MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 3499131fcb52f0a0ab6d0e78e165522b7092612f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458895"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="50b14-102">208 – MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="50b14-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="50b14-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="50b14-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="50b14-104">ID</span><span class="sxs-lookup"><span data-stu-id="50b14-104">ID</span></span>|<span data-ttu-id="50b14-105">208</span><span class="sxs-lookup"><span data-stu-id="50b14-105">208</span></span>|  
|<span data-ttu-id="50b14-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="50b14-106">Keywords</span></span>|<span data-ttu-id="50b14-107">Řešení potíží s ServiceModel</span><span class="sxs-lookup"><span data-stu-id="50b14-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="50b14-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="50b14-108">Level</span></span>|<span data-ttu-id="50b14-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="50b14-109">Information</span></span>|  
|<span data-ttu-id="50b14-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="50b14-110">Channel</span></span>|<span data-ttu-id="50b14-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="50b14-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="50b14-112">Popis</span><span class="sxs-lookup"><span data-stu-id="50b14-112">Description</span></span>  
 <span data-ttu-id="50b14-113">Tato událost je vygenerované po Model služby má vyvolat `AfterReceive` metodu na zpráva inspector.</span><span class="sxs-lookup"><span data-stu-id="50b14-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="50b14-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="50b14-114">Message</span></span>  
 <span data-ttu-id="50b14-115">Dispečer vyvolat 'AfterReceiveReply' na MessageInspector typu '%1'.</span><span class="sxs-lookup"><span data-stu-id="50b14-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="50b14-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="50b14-116">Details</span></span>  
  
|<span data-ttu-id="50b14-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="50b14-117">Data Item Name</span></span>|<span data-ttu-id="50b14-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="50b14-118">Data Item Type</span></span>|<span data-ttu-id="50b14-119">Popis</span><span class="sxs-lookup"><span data-stu-id="50b14-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="50b14-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="50b14-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="50b14-121">Položka FullName CLR typu vyvolanou `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="50b14-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="50b14-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="50b14-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="50b14-123">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="50b14-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="50b14-124">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="50b14-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="50b14-125">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="50b14-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="50b14-126">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="50b14-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="50b14-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="50b14-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
