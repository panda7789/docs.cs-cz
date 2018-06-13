---
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: 806a437822cef8802a2bef6a54f924f84c88ef60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511384"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="d0b00-102">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="d0b00-102">1028 - CompleteTransactionContextWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="d0b00-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d0b00-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d0b00-104">ID</span><span class="sxs-lookup"><span data-stu-id="d0b00-104">ID</span></span>|<span data-ttu-id="d0b00-105">1028</span><span class="sxs-lookup"><span data-stu-id="d0b00-105">1028</span></span>|  
|<span data-ttu-id="d0b00-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d0b00-106">Keywords</span></span>|<span data-ttu-id="d0b00-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="d0b00-107">WFRuntime</span></span>|  
|<span data-ttu-id="d0b00-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="d0b00-108">Level</span></span>|<span data-ttu-id="d0b00-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="d0b00-109">Verbose</span></span>|  
|<span data-ttu-id="d0b00-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="d0b00-110">Channel</span></span>|<span data-ttu-id="d0b00-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="d0b00-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d0b00-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d0b00-112">Description</span></span>  
 <span data-ttu-id="d0b00-113">Označuje, že je dokončená TransactionContextWorkItem.</span><span class="sxs-lookup"><span data-stu-id="d0b00-113">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d0b00-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="d0b00-114">Message</span></span>  
 <span data-ttu-id="d0b00-115">TransactionContextWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="d0b00-115">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d0b00-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="d0b00-116">Details</span></span>  
  
|<span data-ttu-id="d0b00-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="d0b00-117">Data Item Name</span></span>|<span data-ttu-id="d0b00-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="d0b00-118">Data Item Type</span></span>|<span data-ttu-id="d0b00-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d0b00-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d0b00-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="d0b00-120">Activity</span></span>|<span data-ttu-id="d0b00-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="d0b00-121">xs:string</span></span>|<span data-ttu-id="d0b00-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="d0b00-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="d0b00-123">displayName</span><span class="sxs-lookup"><span data-stu-id="d0b00-123">DisplayName</span></span>|<span data-ttu-id="d0b00-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="d0b00-124">xs:string</span></span>|<span data-ttu-id="d0b00-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="d0b00-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="d0b00-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="d0b00-126">InstanceId</span></span>|<span data-ttu-id="d0b00-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="d0b00-127">xs:string</span></span>|<span data-ttu-id="d0b00-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="d0b00-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="d0b00-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="d0b00-129">AppDomain</span></span>|<span data-ttu-id="d0b00-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="d0b00-130">xs:string</span></span>|<span data-ttu-id="d0b00-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="d0b00-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
