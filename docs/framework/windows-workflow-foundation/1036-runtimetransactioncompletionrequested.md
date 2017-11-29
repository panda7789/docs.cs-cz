---
title: 1036 - RuntimeTransactionCompletionRequested
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4f497d777221a98b38603b2ced29342651b1020b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="e63c1-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="e63c1-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="e63c1-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e63c1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e63c1-104">ID</span><span class="sxs-lookup"><span data-stu-id="e63c1-104">ID</span></span>|<span data-ttu-id="e63c1-105">1036</span><span class="sxs-lookup"><span data-stu-id="e63c1-105">1036</span></span>|  
|<span data-ttu-id="e63c1-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="e63c1-106">Keywords</span></span>|<span data-ttu-id="e63c1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e63c1-107">WFRuntime</span></span>|  
|<span data-ttu-id="e63c1-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e63c1-108">Level</span></span>|<span data-ttu-id="e63c1-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="e63c1-109">Verbose</span></span>|  
|<span data-ttu-id="e63c1-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="e63c1-110">Channel</span></span>|<span data-ttu-id="e63c1-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="e63c1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e63c1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="e63c1-112">Description</span></span>  
 <span data-ttu-id="e63c1-113">Označuje, že aktivita má naplánované na dokončení transakce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e63c1-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e63c1-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e63c1-114">Message</span></span>  
 <span data-ttu-id="e63c1-115">Aktivita "%1", DisplayName: %2, identifikátor InstanceId: '%3' má naplánované dokončení transakce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="e63c1-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e63c1-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e63c1-116">Details</span></span>  
  
|<span data-ttu-id="e63c1-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="e63c1-117">Data Item Name</span></span>|<span data-ttu-id="e63c1-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="e63c1-118">Data Item Type</span></span>|<span data-ttu-id="e63c1-119">Popis</span><span class="sxs-lookup"><span data-stu-id="e63c1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e63c1-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="e63c1-120">Activity</span></span>|<span data-ttu-id="e63c1-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="e63c1-121">xs:string</span></span>|<span data-ttu-id="e63c1-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="e63c1-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="e63c1-123">displayName</span><span class="sxs-lookup"><span data-stu-id="e63c1-123">DisplayName</span></span>|<span data-ttu-id="e63c1-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="e63c1-124">xs:string</span></span>|<span data-ttu-id="e63c1-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="e63c1-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="e63c1-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="e63c1-126">InstanceId</span></span>|<span data-ttu-id="e63c1-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="e63c1-127">xs:string</span></span>|<span data-ttu-id="e63c1-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="e63c1-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="e63c1-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="e63c1-129">AppDomain</span></span>|<span data-ttu-id="e63c1-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="e63c1-130">xs:string</span></span>|<span data-ttu-id="e63c1-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e63c1-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
