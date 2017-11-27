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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: be35a4d478f4f2af0921cac942ebb95d6aed38d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="d9369-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="d9369-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d9369-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d9369-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d9369-104">ID</span><span class="sxs-lookup"><span data-stu-id="d9369-104">ID</span></span>|<span data-ttu-id="d9369-105">1027</span><span class="sxs-lookup"><span data-stu-id="d9369-105">1027</span></span>|  
|<span data-ttu-id="d9369-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d9369-106">Keywords</span></span>|<span data-ttu-id="d9369-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d9369-107">WFRuntime</span></span>|  
|<span data-ttu-id="d9369-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="d9369-108">Level</span></span>|<span data-ttu-id="d9369-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="d9369-109">Verbose</span></span>|  
|<span data-ttu-id="d9369-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="d9369-110">Channel</span></span>|<span data-ttu-id="d9369-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="d9369-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d9369-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d9369-112">Description</span></span>  
 <span data-ttu-id="d9369-113">Označuje, že že transactioncontextworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="d9369-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d9369-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="d9369-114">Message</span></span>  
 <span data-ttu-id="d9369-115">Spuštění provádění TransactionContextWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d9369-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d9369-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d9369-116">Details</span></span>  
  
|<span data-ttu-id="d9369-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="d9369-117">Data Item Name</span></span>|<span data-ttu-id="d9369-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="d9369-118">Data Item Type</span></span>|<span data-ttu-id="d9369-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d9369-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d9369-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="d9369-120">Activity</span></span>|<span data-ttu-id="d9369-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="d9369-121">xs:string</span></span>|<span data-ttu-id="d9369-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="d9369-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d9369-123">displayName</span><span class="sxs-lookup"><span data-stu-id="d9369-123">DisplayName</span></span>|<span data-ttu-id="d9369-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="d9369-124">xs:string</span></span>|<span data-ttu-id="d9369-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="d9369-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d9369-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="d9369-126">InstanceId</span></span>|<span data-ttu-id="d9369-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="d9369-127">xs:string</span></span>|<span data-ttu-id="d9369-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="d9369-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d9369-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="d9369-129">AppDomain</span></span>|<span data-ttu-id="d9369-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="d9369-130">xs:string</span></span>|<span data-ttu-id="d9369-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d9369-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
