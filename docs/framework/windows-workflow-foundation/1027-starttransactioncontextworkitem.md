---
title: 1027 - StartTransactionContextWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: baa644cb7693b8608f119cf211b3b08ab4b1a2b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="3eceb-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="3eceb-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3eceb-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3eceb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3eceb-104">ID</span><span class="sxs-lookup"><span data-stu-id="3eceb-104">ID</span></span>|<span data-ttu-id="3eceb-105">1027</span><span class="sxs-lookup"><span data-stu-id="3eceb-105">1027</span></span>|  
|<span data-ttu-id="3eceb-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3eceb-106">Keywords</span></span>|<span data-ttu-id="3eceb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3eceb-107">WFRuntime</span></span>|  
|<span data-ttu-id="3eceb-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="3eceb-108">Level</span></span>|<span data-ttu-id="3eceb-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="3eceb-109">Verbose</span></span>|  
|<span data-ttu-id="3eceb-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="3eceb-110">Channel</span></span>|<span data-ttu-id="3eceb-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="3eceb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3eceb-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3eceb-112">Description</span></span>  
 <span data-ttu-id="3eceb-113">Označuje, že že transactioncontextworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="3eceb-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3eceb-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3eceb-114">Message</span></span>  
 <span data-ttu-id="3eceb-115">Spuštění provádění TransactionContextWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="3eceb-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3eceb-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3eceb-116">Details</span></span>  
  
|<span data-ttu-id="3eceb-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="3eceb-117">Data Item Name</span></span>|<span data-ttu-id="3eceb-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="3eceb-118">Data Item Type</span></span>|<span data-ttu-id="3eceb-119">Popis</span><span class="sxs-lookup"><span data-stu-id="3eceb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3eceb-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="3eceb-120">Activity</span></span>|<span data-ttu-id="3eceb-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="3eceb-121">xs:string</span></span>|<span data-ttu-id="3eceb-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="3eceb-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3eceb-123">displayName</span><span class="sxs-lookup"><span data-stu-id="3eceb-123">DisplayName</span></span>|<span data-ttu-id="3eceb-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="3eceb-124">xs:string</span></span>|<span data-ttu-id="3eceb-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="3eceb-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3eceb-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="3eceb-126">InstanceId</span></span>|<span data-ttu-id="3eceb-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="3eceb-127">xs:string</span></span>|<span data-ttu-id="3eceb-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="3eceb-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3eceb-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="3eceb-129">AppDomain</span></span>|<span data-ttu-id="3eceb-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="3eceb-130">xs:string</span></span>|<span data-ttu-id="3eceb-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3eceb-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
