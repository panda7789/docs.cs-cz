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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7417d2e0e850017e65910be32e7449255f0761c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="57398---maxinstancesexceeded"></a><span data-ttu-id="bf812-102">57398 - MaxInstancesExceeded</span><span class="sxs-lookup"><span data-stu-id="bf812-102">57398 - MaxInstancesExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="bf812-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bf812-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bf812-104">ID</span><span class="sxs-lookup"><span data-stu-id="bf812-104">ID</span></span>|<span data-ttu-id="bf812-105">57398</span><span class="sxs-lookup"><span data-stu-id="bf812-105">57398</span></span>|  
|<span data-ttu-id="bf812-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="bf812-106">Keywords</span></span>|<span data-ttu-id="bf812-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="bf812-107">WFServices</span></span>|  
|<span data-ttu-id="bf812-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="bf812-108">Level</span></span>|<span data-ttu-id="bf812-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="bf812-109">Warning</span></span>|  
|<span data-ttu-id="bf812-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="bf812-110">Channel</span></span>|<span data-ttu-id="bf812-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="bf812-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bf812-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bf812-112">Description</span></span>  
 <span data-ttu-id="bf812-113">Označuje, že systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="bf812-113">Indicates the system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bf812-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="bf812-114">Message</span></span>  
 <span data-ttu-id="bf812-115">Systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'.</span><span class="sxs-lookup"><span data-stu-id="bf812-115">The system hit the limit set for throttle 'MaxConcurrentInstances'.</span></span> <span data-ttu-id="bf812-116">Limit pro toto omezení byla nastavena na %1.</span><span class="sxs-lookup"><span data-stu-id="bf812-116">Limit for this throttle was set to %1.</span></span> <span data-ttu-id="bf812-117">Hodnota omezení lze změnit úpravou atribut 'maxConcurrentInstances' v omezení ServiceThrottle s hodnotou elementu nebo úpravou vlastnosti 'MaxConcurrentInstances' na chování třídy ServiceThrottlingBehavior.</span><span class="sxs-lookup"><span data-stu-id="bf812-117">Throttle value can be changed by modifying attribute 'maxConcurrentInstances' in serviceThrottle element or by modifying 'MaxConcurrentInstances' property on behavior ServiceThrottlingBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bf812-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bf812-118">Details</span></span>  
  
|<span data-ttu-id="bf812-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="bf812-119">Data Item Name</span></span>|<span data-ttu-id="bf812-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="bf812-120">Data Item Type</span></span>|<span data-ttu-id="bf812-121">Popis</span><span class="sxs-lookup"><span data-stu-id="bf812-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bf812-122">Název</span><span class="sxs-lookup"><span data-stu-id="bf812-122">Name</span></span>|<span data-ttu-id="bf812-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="bf812-123">xs:string</span></span>|<span data-ttu-id="bf812-124">Název položky.</span><span class="sxs-lookup"><span data-stu-id="bf812-124">The name of the item.</span></span>|  
|<span data-ttu-id="bf812-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="bf812-125">AppDomain</span></span>|<span data-ttu-id="bf812-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="bf812-126">xs:string</span></span>|<span data-ttu-id="bf812-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bf812-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
