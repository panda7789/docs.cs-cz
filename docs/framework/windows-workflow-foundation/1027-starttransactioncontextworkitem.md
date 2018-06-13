---
title: 1027 - StartTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 116ae5ec-b9d5-4231-824e-270d00eea7b8
ms.openlocfilehash: 231a7607f2ce9a38e8dd6c1486a68bc9eb459e5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510806"
---
# <a name="1027---starttransactioncontextworkitem"></a><span data-ttu-id="bc539-102">1027 - StartTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="bc539-102">1027 - StartTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="bc539-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bc539-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc539-104">ID</span><span class="sxs-lookup"><span data-stu-id="bc539-104">ID</span></span>|<span data-ttu-id="bc539-105">1027</span><span class="sxs-lookup"><span data-stu-id="bc539-105">1027</span></span>|  
|<span data-ttu-id="bc539-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="bc539-106">Keywords</span></span>|<span data-ttu-id="bc539-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="bc539-107">WFRuntime</span></span>|  
|<span data-ttu-id="bc539-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="bc539-108">Level</span></span>|<span data-ttu-id="bc539-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="bc539-109">Verbose</span></span>|  
|<span data-ttu-id="bc539-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="bc539-110">Channel</span></span>|<span data-ttu-id="bc539-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="bc539-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bc539-112">Popis</span><span class="sxs-lookup"><span data-stu-id="bc539-112">Description</span></span>  
 <span data-ttu-id="bc539-113">Označuje, že že transactioncontextworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="bc539-113">Indicates a TransactionContextWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bc539-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="bc539-114">Message</span></span>  
 <span data-ttu-id="bc539-115">Spuštění provádění TransactionContextWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="bc539-115">Starting execution of a TransactionContextWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bc539-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bc539-116">Details</span></span>  
  
|<span data-ttu-id="bc539-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="bc539-117">Data Item Name</span></span>|<span data-ttu-id="bc539-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="bc539-118">Data Item Type</span></span>|<span data-ttu-id="bc539-119">Popis</span><span class="sxs-lookup"><span data-stu-id="bc539-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bc539-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="bc539-120">Activity</span></span>|<span data-ttu-id="bc539-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="bc539-121">xs:string</span></span>|<span data-ttu-id="bc539-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="bc539-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="bc539-123">displayName</span><span class="sxs-lookup"><span data-stu-id="bc539-123">DisplayName</span></span>|<span data-ttu-id="bc539-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="bc539-124">xs:string</span></span>|<span data-ttu-id="bc539-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="bc539-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="bc539-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="bc539-126">InstanceId</span></span>|<span data-ttu-id="bc539-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="bc539-127">xs:string</span></span>|<span data-ttu-id="bc539-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="bc539-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="bc539-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="bc539-129">AppDomain</span></span>|<span data-ttu-id="bc539-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="bc539-130">xs:string</span></span>|<span data-ttu-id="bc539-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bc539-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
