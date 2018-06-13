---
title: 1018 - StartCancelActivityWorkItem
ms.date: 03/30/2017
ms.assetid: 68b4fa1d-eee6-4a2a-8c16-7e9d89f08ab9
ms.openlocfilehash: 8d7045b0a7f31ecfd5dd90f319192bd202804353
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510650"
---
# <a name="1018---startcancelactivityworkitem"></a><span data-ttu-id="95a8b-102">1018 - StartCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="95a8b-102">1018 - StartCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="95a8b-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="95a8b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95a8b-104">ID</span><span class="sxs-lookup"><span data-stu-id="95a8b-104">ID</span></span>|<span data-ttu-id="95a8b-105">1018</span><span class="sxs-lookup"><span data-stu-id="95a8b-105">1018</span></span>|  
|<span data-ttu-id="95a8b-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="95a8b-106">Keywords</span></span>|<span data-ttu-id="95a8b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="95a8b-107">WFRuntime</span></span>|  
|<span data-ttu-id="95a8b-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="95a8b-108">Level</span></span>|<span data-ttu-id="95a8b-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="95a8b-109">Verbose</span></span>|  
|<span data-ttu-id="95a8b-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="95a8b-110">Channel</span></span>|<span data-ttu-id="95a8b-111">Aplikaci Microsoft Windows Server – aplikace/Debug</span><span class="sxs-lookup"><span data-stu-id="95a8b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="95a8b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="95a8b-112">Description</span></span>  
 <span data-ttu-id="95a8b-113">Označuje, že že cancelactivityworkitem zahajuje provádění.</span><span class="sxs-lookup"><span data-stu-id="95a8b-113">Indicates a CancelActivityWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="95a8b-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="95a8b-114">Message</span></span>  
 <span data-ttu-id="95a8b-115">Spuštění provádění CancelActivityWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="95a8b-115">Starting execution of a CancelActivityWorkItem for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="95a8b-116">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="95a8b-116">Details</span></span>  
  
|<span data-ttu-id="95a8b-117">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="95a8b-117">Data Item Name</span></span>|<span data-ttu-id="95a8b-118">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="95a8b-118">Data Item Type</span></span>|<span data-ttu-id="95a8b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="95a8b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="95a8b-120">Aktivita</span><span class="sxs-lookup"><span data-stu-id="95a8b-120">Activity</span></span>|<span data-ttu-id="95a8b-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="95a8b-121">xs:string</span></span>|<span data-ttu-id="95a8b-122">Název typu aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a8b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="95a8b-123">displayName</span><span class="sxs-lookup"><span data-stu-id="95a8b-123">DisplayName</span></span>|<span data-ttu-id="95a8b-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="95a8b-124">xs:string</span></span>|<span data-ttu-id="95a8b-125">Zobrazovaný název aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a8b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="95a8b-126">identifikátor instanceId</span><span class="sxs-lookup"><span data-stu-id="95a8b-126">InstanceId</span></span>|<span data-ttu-id="95a8b-127">xs:String</span><span class="sxs-lookup"><span data-stu-id="95a8b-127">xs:string</span></span>|<span data-ttu-id="95a8b-128">Id instance aktivity.</span><span class="sxs-lookup"><span data-stu-id="95a8b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="95a8b-129">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="95a8b-129">AppDomain</span></span>|<span data-ttu-id="95a8b-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="95a8b-130">xs:string</span></span>|<span data-ttu-id="95a8b-131">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="95a8b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
