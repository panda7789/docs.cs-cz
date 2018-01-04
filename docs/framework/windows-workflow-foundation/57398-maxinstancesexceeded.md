---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba48f19de1be3cfd2461e159b91fa365e24ee750
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="6a29d-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="6a29d-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="6a29d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6a29d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6a29d-104">ID</span><span class="sxs-lookup"><span data-stu-id="6a29d-104">ID</span></span>|<span data-ttu-id="6a29d-105">57398</span><span class="sxs-lookup"><span data-stu-id="6a29d-105">57398</span></span>|  
|<span data-ttu-id="6a29d-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="6a29d-106">Keywords</span></span>|<span data-ttu-id="6a29d-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="6a29d-107">WFServices</span></span>|  
|<span data-ttu-id="6a29d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="6a29d-108">Level</span></span>|<span data-ttu-id="6a29d-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="6a29d-109">Warning</span></span>|  
|<span data-ttu-id="6a29d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="6a29d-110">Channel</span></span>|<span data-ttu-id="6a29d-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="6a29d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6a29d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6a29d-112">Description</span></span>  
 <span data-ttu-id="6a29d-113">Označuje, že systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="6a29d-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6a29d-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6a29d-114">Message</span></span>  
 <span data-ttu-id="6a29d-115">Systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="6a29d-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="6a29d-116">Limit pro toto omezení byla nastavena na %1.</span><span class="sxs-lookup"><span data-stu-id="6a29d-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="6a29d-117">Hodnota omezení lze změnit úpravou atribut 'maxConcurrentInstances' v omezení ServiceThrottle s hodnotou elementu nebo úpravou vlastnosti 'MaxConcurrentInstances' na chování třídy ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="6a29d-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6a29d-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="6a29d-118">Details</span></span>  
  
|<span data-ttu-id="6a29d-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="6a29d-119">Data Item Name</span></span>|<span data-ttu-id="6a29d-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="6a29d-120">Data Item Type</span></span>|<span data-ttu-id="6a29d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="6a29d-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6a29d-122">Název</span><span class="sxs-lookup"><span data-stu-id="6a29d-122">Name</span></span>|<span data-ttu-id="6a29d-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="6a29d-123">xs:string</span></span>|<span data-ttu-id="6a29d-124">Název položky.</span><span class="sxs-lookup"><span data-stu-id="6a29d-124">The name of the item.</span></span>|  
|<span data-ttu-id="6a29d-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="6a29d-125">AppDomain</span></span>|<span data-ttu-id="6a29d-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="6a29d-126">xs:string</span></span>|<span data-ttu-id="6a29d-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6a29d-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
