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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf90e78ed7fbfe500ac52e6629d31bd0aff97bd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="08b9b-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="08b9b-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="08b9b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="08b9b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08b9b-104">ID</span><span class="sxs-lookup"><span data-stu-id="08b9b-104">ID</span></span>|<span data-ttu-id="08b9b-105">3552</span><span class="sxs-lookup"><span data-stu-id="08b9b-105">3552</span></span>|  
|<span data-ttu-id="08b9b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="08b9b-106">Keywords</span></span>|<span data-ttu-id="08b9b-107">Kvóta, WFServices</span><span class="sxs-lookup"><span data-stu-id="08b9b-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="08b9b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="08b9b-108">Level</span></span>|<span data-ttu-id="08b9b-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="08b9b-109">Warning</span></span>|  
|<span data-ttu-id="08b9b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="08b9b-110">Channel</span></span>|<span data-ttu-id="08b9b-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="08b9b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="08b9b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="08b9b-112">Description</span></span>  
 <span data-ttu-id="08b9b-113">Určuje omezení MaxPendingMessagesPerChannel bylo dosaženo limitu.</span><span class="sxs-lookup"><span data-stu-id="08b9b-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="08b9b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="08b9b-114">Message</span></span>  
 <span data-ttu-id="08b9b-115">Omezení limit 'MaxPendingMessagesPerChannel' % 1, který byl vybrán.</span><span class="sxs-lookup"><span data-stu-id="08b9b-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="08b9b-116">Chcete-li tento limit zvýšit, upravte vlastnost MaxPendingMessagesPerChannel na BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="08b9b-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="08b9b-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="08b9b-117">Details</span></span>  
  
|<span data-ttu-id="08b9b-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="08b9b-118">Data Item Name</span></span>|<span data-ttu-id="08b9b-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="08b9b-119">Data Item Type</span></span>|<span data-ttu-id="08b9b-120">Popis</span><span class="sxs-lookup"><span data-stu-id="08b9b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="08b9b-121">Limit</span><span class="sxs-lookup"><span data-stu-id="08b9b-121">Limit</span></span>|<span data-ttu-id="08b9b-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="08b9b-122">xs:string</span></span>|<span data-ttu-id="08b9b-123">Limit omezovače MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="08b9b-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="08b9b-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="08b9b-124">AppDomain</span></span>|<span data-ttu-id="08b9b-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="08b9b-125">xs:string</span></span>|<span data-ttu-id="08b9b-126">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="08b9b-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
