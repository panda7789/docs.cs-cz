---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ba5e4aa8e1338321838e40db7d976107315ef64
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="5ea50-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="5ea50-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="5ea50-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5ea50-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ea50-104">ID</span><span class="sxs-lookup"><span data-stu-id="5ea50-104">ID</span></span>|<span data-ttu-id="5ea50-105">3552</span><span class="sxs-lookup"><span data-stu-id="5ea50-105">3552</span></span>|  
|<span data-ttu-id="5ea50-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5ea50-106">Keywords</span></span>|<span data-ttu-id="5ea50-107">Kvóta, WFServices</span><span class="sxs-lookup"><span data-stu-id="5ea50-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="5ea50-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5ea50-108">Level</span></span>|<span data-ttu-id="5ea50-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="5ea50-109">Warning</span></span>|  
|<span data-ttu-id="5ea50-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5ea50-110">Channel</span></span>|<span data-ttu-id="5ea50-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="5ea50-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5ea50-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5ea50-112">Description</span></span>  
 <span data-ttu-id="5ea50-113">Určuje omezení MaxPendingMessagesPerChannel bylo dosaženo limitu.</span><span class="sxs-lookup"><span data-stu-id="5ea50-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5ea50-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5ea50-114">Message</span></span>  
 <span data-ttu-id="5ea50-115">Omezení limit 'MaxPendingMessagesPerChannel' % 1, který byl vybrán.</span><span class="sxs-lookup"><span data-stu-id="5ea50-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="5ea50-116">Chcete-li tento limit zvýšit, upravte vlastnost MaxPendingMessagesPerChannel na BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="5ea50-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5ea50-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5ea50-117">Details</span></span>  
  
|<span data-ttu-id="5ea50-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5ea50-118">Data Item Name</span></span>|<span data-ttu-id="5ea50-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="5ea50-119">Data Item Type</span></span>|<span data-ttu-id="5ea50-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5ea50-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5ea50-121">Limit</span><span class="sxs-lookup"><span data-stu-id="5ea50-121">Limit</span></span>|<span data-ttu-id="5ea50-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="5ea50-122">xs:string</span></span>|<span data-ttu-id="5ea50-123">Limit omezovače MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="5ea50-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="5ea50-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5ea50-124">AppDomain</span></span>|<span data-ttu-id="5ea50-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="5ea50-125">xs:string</span></span>|<span data-ttu-id="5ea50-126">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5ea50-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
