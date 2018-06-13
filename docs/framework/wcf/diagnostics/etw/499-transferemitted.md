---
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: b1ade828ee6519288165e272e7d9f36fd6aca9ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469505"
---
# <a name="499---transferemitted"></a><span data-ttu-id="06b65-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="06b65-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="06b65-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="06b65-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="06b65-104">ID</span><span class="sxs-lookup"><span data-stu-id="06b65-104">ID</span></span>|<span data-ttu-id="06b65-105">499</span><span class="sxs-lookup"><span data-stu-id="06b65-105">499</span></span>|  
|<span data-ttu-id="06b65-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="06b65-106">Keywords</span></span>|<span data-ttu-id="06b65-107">Řešení potíží, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="06b65-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="06b65-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="06b65-108">Level</span></span>|<span data-ttu-id="06b65-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="06b65-109">LogAlways</span></span>|  
|<span data-ttu-id="06b65-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="06b65-110">Channel</span></span>|<span data-ttu-id="06b65-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="06b65-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="06b65-112">Popis</span><span class="sxs-lookup"><span data-stu-id="06b65-112">Description</span></span>  
 <span data-ttu-id="06b65-113">Tato událost je vygenerované při výskytu události přenosu.</span><span class="sxs-lookup"><span data-stu-id="06b65-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="06b65-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="06b65-114">Message</span></span>  
 <span data-ttu-id="06b65-115">Vygenerované událost přenosu.</span><span class="sxs-lookup"><span data-stu-id="06b65-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="06b65-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="06b65-116">Details</span></span>  
  
|<span data-ttu-id="06b65-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="06b65-117">Data Item Name</span></span>|<span data-ttu-id="06b65-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="06b65-118">Data Item Type</span></span>|<span data-ttu-id="06b65-119">Popis</span><span class="sxs-lookup"><span data-stu-id="06b65-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="06b65-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="06b65-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="06b65-121">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="06b65-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="06b65-122">Formát je definovaný jako "virtuální cesta aplikace název webu&#124;virtuální cestu služby&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="06b65-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="06b65-123">Příklad: "Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="06b65-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="06b65-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="06b65-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="06b65-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="06b65-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
