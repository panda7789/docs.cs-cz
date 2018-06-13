---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510390"
---
# <a name="1036---runtimetransactioncompletionrequested"></a><span data-ttu-id="af3ff-102">1036 - RuntimeTransactionCompletionRequested</span><span class="sxs-lookup"><span data-stu-id="af3ff-102">1036 - RuntimeTransactionCompletionRequested</span></span>
## <a name="properties"></a><span data-ttu-id="af3ff-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="af3ff-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="af3ff-104">ID</span><span class="sxs-lookup"><span data-stu-id="af3ff-104">ID</span></span>|<span data-ttu-id="af3ff-105">1036</span><span class="sxs-lookup"><span data-stu-id="af3ff-105">1036</span></span>|  
|<span data-ttu-id="af3ff-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="af3ff-106">Keywords</span></span>|<span data-ttu-id="af3ff-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="af3ff-107">WFRuntime</span></span>|  
|<span data-ttu-id="af3ff-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="af3ff-108">Level</span></span>|<span data-ttu-id="af3ff-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="af3ff-109">Verbose</span></span>|  
|<span data-ttu-id="af3ff-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="af3ff-110">Channel</span></span>|<span data-ttu-id="af3ff-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="af3ff-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="af3ff-112">Popis</span><span class="sxs-lookup"><span data-stu-id="af3ff-112">Description</span></span>  
 <span data-ttu-id="af3ff-113">Označuje, že aktivita má naplánované na dokončení transakce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="af3ff-113">Indicates an activity has scheduled the completion of the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="af3ff-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="af3ff-114">Message</span></span>  
 <span data-ttu-id="af3ff-115">Aktivita "%1", DisplayName: %2, identifikátor InstanceId: '%3' má naplánované dokončení transakce modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="af3ff-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has scheduled completion of the runtime transaction.</span></span>  
  
## <a name="details"></a><span data-ttu-id="af3ff-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="af3ff-116">Details</span></span>  
  
|<span data-ttu-id="af3ff-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="af3ff-117">Data Item Name</span></span>|<span data-ttu-id="af3ff-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="af3ff-118">Data Item Type</span></span>|<span data-ttu-id="af3ff-119">Popis</span><span class="sxs-lookup"><span data-stu-id="af3ff-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="af3ff-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="af3ff-120">Activity</span></span>|<span data-ttu-id="af3ff-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="af3ff-121">xs:string</span></span>|<span data-ttu-id="af3ff-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="af3ff-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="af3ff-123">displayName</span><span class="sxs-lookup"><span data-stu-id="af3ff-123">DisplayName</span></span>|<span data-ttu-id="af3ff-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="af3ff-124">xs:string</span></span>|<span data-ttu-id="af3ff-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="af3ff-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="af3ff-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="af3ff-126">InstanceId</span></span>|<span data-ttu-id="af3ff-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="af3ff-127">xs:string</span></span>|<span data-ttu-id="af3ff-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="af3ff-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="af3ff-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="af3ff-129">AppDomain</span></span>|<span data-ttu-id="af3ff-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="af3ff-130">xs:string</span></span>|<span data-ttu-id="af3ff-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="af3ff-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
