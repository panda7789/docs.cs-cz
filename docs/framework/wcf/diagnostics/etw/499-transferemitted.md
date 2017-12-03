---
title: 499 - TransferEmitted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a0bbe31095a59be4b091de6974ae0173753e240
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="17faf-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="17faf-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="17faf-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="17faf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="17faf-104">ID</span><span class="sxs-lookup"><span data-stu-id="17faf-104">ID</span></span>|<span data-ttu-id="17faf-105">499</span><span class="sxs-lookup"><span data-stu-id="17faf-105">499</span></span>|  
|<span data-ttu-id="17faf-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="17faf-106">Keywords</span></span>|<span data-ttu-id="17faf-107">Řešení potíží, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="17faf-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="17faf-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="17faf-108">Level</span></span>|<span data-ttu-id="17faf-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="17faf-109">LogAlways</span></span>|  
|<span data-ttu-id="17faf-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="17faf-110">Channel</span></span>|<span data-ttu-id="17faf-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="17faf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="17faf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="17faf-112">Description</span></span>  
 <span data-ttu-id="17faf-113">Tato událost je vygenerované při výskytu události přenosu.</span><span class="sxs-lookup"><span data-stu-id="17faf-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="17faf-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="17faf-114">Message</span></span>  
 <span data-ttu-id="17faf-115">Vygenerované událost přenosu.</span><span class="sxs-lookup"><span data-stu-id="17faf-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="17faf-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="17faf-116">Details</span></span>  
  
|<span data-ttu-id="17faf-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="17faf-117">Data Item Name</span></span>|<span data-ttu-id="17faf-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="17faf-118">Data Item Type</span></span>|<span data-ttu-id="17faf-119">Popis</span><span class="sxs-lookup"><span data-stu-id="17faf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="17faf-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="17faf-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="17faf-121">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="17faf-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="17faf-122">Formát je definovaný jako "virtuální cesta aplikace název webu & #124; Virtuální cesta služby & #124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="17faf-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="17faf-123">Příklad: "Default Web Site/CalculatorApplication & #124;/CalculatorService.svc & #124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="17faf-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="17faf-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="17faf-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="17faf-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="17faf-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
