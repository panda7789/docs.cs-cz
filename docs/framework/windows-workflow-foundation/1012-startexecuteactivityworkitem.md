---
title: 1012 - StartExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 29e9b1c6-c5d7-4b58-b59d-a06a923d3c80
ms.openlocfilehash: d6b330bc454c39584e5027f757fd9d9d3434d941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510377"
---
# <a name="1012---startexecuteactivityworkitem"></a><span data-ttu-id="a26b8-102">1012 - StartExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="a26b8-102">1012 - StartExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="a26b8-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a26b8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a26b8-104">ID</span><span class="sxs-lookup"><span data-stu-id="a26b8-104">ID</span></span>|<span data-ttu-id="a26b8-105">1012</span><span class="sxs-lookup"><span data-stu-id="a26b8-105">1012</span></span>|  
|<span data-ttu-id="a26b8-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="a26b8-106">Keywords</span></span>|<span data-ttu-id="a26b8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a26b8-107">WFRuntime</span></span>|  
|<span data-ttu-id="a26b8-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="a26b8-108">Level</span></span>|<span data-ttu-id="a26b8-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="a26b8-109">Verbose</span></span>|  
|<span data-ttu-id="a26b8-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="a26b8-110">Channel</span></span>|<span data-ttu-id="a26b8-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="a26b8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a26b8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a26b8-112">Description</span></span>  
 <span data-ttu-id="a26b8-113">Označuje, že že executeactivityworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="a26b8-113">Indicates an ExecuteActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a26b8-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="a26b8-114">Message</span></span>  
 <span data-ttu-id="a26b8-115">Od spuštění ExecuteActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="a26b8-115">Starting execution of an ExecuteActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a26b8-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a26b8-116">Details</span></span>  
  
|<span data-ttu-id="a26b8-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="a26b8-117">Data Item Name</span></span>|<span data-ttu-id="a26b8-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="a26b8-118">Data Item Type</span></span>|<span data-ttu-id="a26b8-119">Popis</span><span class="sxs-lookup"><span data-stu-id="a26b8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a26b8-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="a26b8-120">Activity</span></span>|<span data-ttu-id="a26b8-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="a26b8-121">xs:string</span></span>|<span data-ttu-id="a26b8-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="a26b8-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a26b8-123">displayName</span><span class="sxs-lookup"><span data-stu-id="a26b8-123">DisplayName</span></span>|<span data-ttu-id="a26b8-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="a26b8-124">xs:string</span></span>|<span data-ttu-id="a26b8-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="a26b8-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a26b8-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="a26b8-126">InstanceId</span></span>|<span data-ttu-id="a26b8-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="a26b8-127">xs:string</span></span>|<span data-ttu-id="a26b8-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="a26b8-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a26b8-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="a26b8-129">AppDomain</span></span>|<span data-ttu-id="a26b8-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="a26b8-130">xs:string</span></span>|<span data-ttu-id="a26b8-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a26b8-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
