---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511228"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="e4898-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="e4898-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="e4898-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e4898-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e4898-104">ID</span><span class="sxs-lookup"><span data-stu-id="e4898-104">ID</span></span>|<span data-ttu-id="e4898-105">3552</span><span class="sxs-lookup"><span data-stu-id="e4898-105">3552</span></span>|  
|<span data-ttu-id="e4898-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e4898-106">Keywords</span></span>|<span data-ttu-id="e4898-107">Kvóta, WFServices</span><span class="sxs-lookup"><span data-stu-id="e4898-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="e4898-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e4898-108">Level</span></span>|<span data-ttu-id="e4898-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="e4898-109">Warning</span></span>|  
|<span data-ttu-id="e4898-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e4898-110">Channel</span></span>|<span data-ttu-id="e4898-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="e4898-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e4898-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e4898-112">Description</span></span>  
 <span data-ttu-id="e4898-113">Určuje omezení MaxPendingMessagesPerChannel bylo dosaženo limitu.</span><span class="sxs-lookup"><span data-stu-id="e4898-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e4898-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e4898-114">Message</span></span>  
 <span data-ttu-id="e4898-115">Omezení limit 'MaxPendingMessagesPerChannel' % 1, který byl vybrán.</span><span class="sxs-lookup"><span data-stu-id="e4898-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="e4898-116">Chcete-li tento limit zvýšit, upravte vlastnost MaxPendingMessagesPerChannel na BufferedReceiveServiceBehavior.</span><span class="sxs-lookup"><span data-stu-id="e4898-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e4898-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e4898-117">Details</span></span>  
  
|<span data-ttu-id="e4898-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e4898-118">Data Item Name</span></span>|<span data-ttu-id="e4898-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="e4898-119">Data Item Type</span></span>|<span data-ttu-id="e4898-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e4898-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e4898-121">Limit</span><span class="sxs-lookup"><span data-stu-id="e4898-121">Limit</span></span>|<span data-ttu-id="e4898-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="e4898-122">xs:string</span></span>|<span data-ttu-id="e4898-123">Limit omezovače MaxPendingMessagesPerChannel.</span><span class="sxs-lookup"><span data-stu-id="e4898-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="e4898-124">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="e4898-124">AppDomain</span></span>|<span data-ttu-id="e4898-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="e4898-125">xs:string</span></span>|<span data-ttu-id="e4898-126">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e4898-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
