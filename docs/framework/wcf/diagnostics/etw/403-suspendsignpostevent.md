---
title: "403 – SuspendSignpostEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb2e6f29-e556-47b4-b4c1-acd6b8879702
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 10e745ded72caa493119d7e27a5c777b2185b96e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="403---suspendsignpostevent"></a><span data-ttu-id="afec3-102">403 – SuspendSignpostEvent</span><span class="sxs-lookup"><span data-stu-id="afec3-102">403 - SuspendSignpostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="afec3-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="afec3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="afec3-104">ID</span><span class="sxs-lookup"><span data-stu-id="afec3-104">ID</span></span>|<span data-ttu-id="afec3-105">403</span><span class="sxs-lookup"><span data-stu-id="afec3-105">403</span></span>|  
|<span data-ttu-id="afec3-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="afec3-106">Keywords</span></span>|<span data-ttu-id="afec3-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="afec3-107">Troubleshooting</span></span>|  
|<span data-ttu-id="afec3-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="afec3-108">Level</span></span>|<span data-ttu-id="afec3-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="afec3-109">Information</span></span>|  
|<span data-ttu-id="afec3-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="afec3-110">Channel</span></span>|<span data-ttu-id="afec3-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="afec3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="afec3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="afec3-112">Description</span></span>  
 <span data-ttu-id="afec3-113">Tato událost označuje pozastavení aktivity začátku do konce.</span><span class="sxs-lookup"><span data-stu-id="afec3-113">This event marks the suspension of an end-to-end activity.</span></span> <span data-ttu-id="afec3-114">Obsahuje název aktivity.</span><span class="sxs-lookup"><span data-stu-id="afec3-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="afec3-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="afec3-115">Message</span></span>  
 <span data-ttu-id="afec3-116">Aktivita hranic.</span><span class="sxs-lookup"><span data-stu-id="afec3-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="afec3-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="afec3-117">Details</span></span>  
  
|<span data-ttu-id="afec3-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="afec3-118">Data Item Name</span></span>|<span data-ttu-id="afec3-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="afec3-119">Data Item Type</span></span>|<span data-ttu-id="afec3-120">Popis</span><span class="sxs-lookup"><span data-stu-id="afec3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="afec3-121">Rozšířená Data</span><span class="sxs-lookup"><span data-stu-id="afec3-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="afec3-122">Název aktivity.</span><span class="sxs-lookup"><span data-stu-id="afec3-122">The name of the activity.</span></span>|  
|<span data-ttu-id="afec3-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="afec3-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="afec3-124">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="afec3-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
