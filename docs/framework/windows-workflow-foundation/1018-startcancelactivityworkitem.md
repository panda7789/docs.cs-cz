---
title: 1018 - StartCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b64ea860e9881ed31aa0d8e78dec55f329cc6fad
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="00fc9-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="00fc9-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="00fc9-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="00fc9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="00fc9-104">ID</span><span class="sxs-lookup"><span data-stu-id="00fc9-104">ID</span></span>|<span data-ttu-id="00fc9-105">1018</span><span class="sxs-lookup"><span data-stu-id="00fc9-105">1018</span></span>|  
|<span data-ttu-id="00fc9-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="00fc9-106">Keywords</span></span>|<span data-ttu-id="00fc9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="00fc9-107">WFRuntime</span></span>|  
|<span data-ttu-id="00fc9-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="00fc9-108">Level</span></span>|<span data-ttu-id="00fc9-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="00fc9-109">Verbose</span></span>|  
|<span data-ttu-id="00fc9-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="00fc9-110">Channel</span></span>|<span data-ttu-id="00fc9-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="00fc9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="00fc9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="00fc9-112">Description</span></span>  
 <span data-ttu-id="00fc9-113">Označuje, že že cancelactivityworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="00fc9-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="00fc9-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="00fc9-114">Message</span></span>  
 <span data-ttu-id="00fc9-115">Spuštění provádění CancelActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="00fc9-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="00fc9-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="00fc9-116">Details</span></span>  
  
|<span data-ttu-id="00fc9-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="00fc9-117">Data Item Name</span></span>|<span data-ttu-id="00fc9-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="00fc9-118">Data Item Type</span></span>|<span data-ttu-id="00fc9-119">Popis</span><span class="sxs-lookup"><span data-stu-id="00fc9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="00fc9-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="00fc9-120">Activity</span></span>|<span data-ttu-id="00fc9-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="00fc9-121">xs:string</span></span>|<span data-ttu-id="00fc9-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="00fc9-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="00fc9-123">displayName</span><span class="sxs-lookup"><span data-stu-id="00fc9-123">DisplayName</span></span>|<span data-ttu-id="00fc9-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="00fc9-124">xs:string</span></span>|<span data-ttu-id="00fc9-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="00fc9-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="00fc9-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="00fc9-126">InstanceId</span></span>|<span data-ttu-id="00fc9-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="00fc9-127">xs:string</span></span>|<span data-ttu-id="00fc9-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="00fc9-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="00fc9-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="00fc9-129">AppDomain</span></span>|<span data-ttu-id="00fc9-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="00fc9-130">xs:string</span></span>|<span data-ttu-id="00fc9-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="00fc9-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
