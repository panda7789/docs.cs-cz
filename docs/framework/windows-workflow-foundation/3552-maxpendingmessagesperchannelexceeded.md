---
title: 3552 – MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945935"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="ad64d-102">3552 – MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="ad64d-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="ad64d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ad64d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad64d-104">ID</span><span class="sxs-lookup"><span data-stu-id="ad64d-104">ID</span></span>|<span data-ttu-id="ad64d-105">3552</span><span class="sxs-lookup"><span data-stu-id="ad64d-105">3552</span></span>|  
|<span data-ttu-id="ad64d-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ad64d-106">Keywords</span></span>|<span data-ttu-id="ad64d-107">Quota, WFServices</span><span class="sxs-lookup"><span data-stu-id="ad64d-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="ad64d-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="ad64d-108">Level</span></span>|<span data-ttu-id="ad64d-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="ad64d-109">Warning</span></span>|  
|<span data-ttu-id="ad64d-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="ad64d-110">Channel</span></span>|<span data-ttu-id="ad64d-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="ad64d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ad64d-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ad64d-112">Description</span></span>  
 <span data-ttu-id="ad64d-113">Určuje omezení bylo dosaženo omezení MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="ad64d-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ad64d-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="ad64d-114">Message</span></span>  
 <span data-ttu-id="ad64d-115">Bylo dosaženo omezení 'MaxPendingMessagesPerChannel' limit '%1'.</span><span class="sxs-lookup"><span data-stu-id="ad64d-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="ad64d-116">Chcete-li tento limit zvýšit, upravte vlastnost MaxPendingMessagesPerChannel objektu bufferedreceiveservicebehavior.</span><span class="sxs-lookup"><span data-stu-id="ad64d-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ad64d-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ad64d-117">Details</span></span>  
  
|<span data-ttu-id="ad64d-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="ad64d-118">Data Item Name</span></span>|<span data-ttu-id="ad64d-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="ad64d-119">Data Item Type</span></span>|<span data-ttu-id="ad64d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="ad64d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ad64d-121">Omezení</span><span class="sxs-lookup"><span data-stu-id="ad64d-121">Limit</span></span>|<span data-ttu-id="ad64d-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad64d-122">xs:string</span></span>|<span data-ttu-id="ad64d-123">Limit omezení MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="ad64d-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="ad64d-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ad64d-124">AppDomain</span></span>|<span data-ttu-id="ad64d-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="ad64d-125">xs:string</span></span>|<span data-ttu-id="ad64d-126">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="ad64d-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
