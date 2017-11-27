---
title: "401 – StopSignPostEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 31cd94e2c988d614babc1e0c203316b41e01f5bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="185dd-102">401 – StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="185dd-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="185dd-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="185dd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="185dd-104">ID</span><span class="sxs-lookup"><span data-stu-id="185dd-104">ID</span></span>|<span data-ttu-id="185dd-105">401</span><span class="sxs-lookup"><span data-stu-id="185dd-105">401</span></span>|  
|<span data-ttu-id="185dd-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="185dd-106">Keywords</span></span>|<span data-ttu-id="185dd-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="185dd-107">Troubleshooting</span></span>|  
|<span data-ttu-id="185dd-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="185dd-108">Level</span></span>|<span data-ttu-id="185dd-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="185dd-109">Information</span></span>|  
|<span data-ttu-id="185dd-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="185dd-110">Channel</span></span>|<span data-ttu-id="185dd-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="185dd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="185dd-112">Popis</span><span class="sxs-lookup"><span data-stu-id="185dd-112">Description</span></span>  
 <span data-ttu-id="185dd-113">Tato událost označuje konec aktivity začátku do konce.</span><span class="sxs-lookup"><span data-stu-id="185dd-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="185dd-114">Obsahuje název aktivity.</span><span class="sxs-lookup"><span data-stu-id="185dd-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="185dd-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="185dd-115">Message</span></span>  
 <span data-ttu-id="185dd-116">Aktivita hranic.</span><span class="sxs-lookup"><span data-stu-id="185dd-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="185dd-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="185dd-117">Details</span></span>  
  
|<span data-ttu-id="185dd-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="185dd-118">Data Item Name</span></span>|<span data-ttu-id="185dd-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="185dd-119">Data Item Type</span></span>|<span data-ttu-id="185dd-120">Popis</span><span class="sxs-lookup"><span data-stu-id="185dd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="185dd-121">Rozšířená Data</span><span class="sxs-lookup"><span data-stu-id="185dd-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="185dd-122">Název aktivity.</span><span class="sxs-lookup"><span data-stu-id="185dd-122">The name of the activity.</span></span>|  
|<span data-ttu-id="185dd-123">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="185dd-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="185dd-124">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="185dd-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
