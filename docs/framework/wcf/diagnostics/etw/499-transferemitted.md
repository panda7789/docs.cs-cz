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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e786691ef3a6ee2a860461562c9de0f627fc907
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="91a12-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="91a12-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="91a12-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="91a12-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91a12-104">ID</span><span class="sxs-lookup"><span data-stu-id="91a12-104">ID</span></span>|<span data-ttu-id="91a12-105">499</span><span class="sxs-lookup"><span data-stu-id="91a12-105">499</span></span>|  
|<span data-ttu-id="91a12-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="91a12-106">Keywords</span></span>|<span data-ttu-id="91a12-107">Řešení potíží, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="91a12-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="91a12-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="91a12-108">Level</span></span>|<span data-ttu-id="91a12-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="91a12-109">LogAlways</span></span>|  
|<span data-ttu-id="91a12-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="91a12-110">Channel</span></span>|<span data-ttu-id="91a12-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="91a12-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="91a12-112">Popis</span><span class="sxs-lookup"><span data-stu-id="91a12-112">Description</span></span>  
 <span data-ttu-id="91a12-113">Tato událost je vygenerované při výskytu události přenosu.</span><span class="sxs-lookup"><span data-stu-id="91a12-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="91a12-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="91a12-114">Message</span></span>  
 <span data-ttu-id="91a12-115">Vygenerované událost přenosu.</span><span class="sxs-lookup"><span data-stu-id="91a12-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="91a12-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="91a12-116">Details</span></span>  
  
|<span data-ttu-id="91a12-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="91a12-117">Data Item Name</span></span>|<span data-ttu-id="91a12-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="91a12-118">Data Item Type</span></span>|<span data-ttu-id="91a12-119">Popis</span><span class="sxs-lookup"><span data-stu-id="91a12-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="91a12-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="91a12-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="91a12-121">Pro hostované webové služby v tomto poli jednoznačně identifikuje v hierarchii webové služby.</span><span class="sxs-lookup"><span data-stu-id="91a12-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="91a12-122">Formát je definovaný jako "virtuální cesta aplikace název webu &#124; Virtuální cesta služby &#124; ServiceName}.</span><span class="sxs-lookup"><span data-stu-id="91a12-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="91a12-123">Příklad: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="91a12-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="91a12-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="91a12-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="91a12-125">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="91a12-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
