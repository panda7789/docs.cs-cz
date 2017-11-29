---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb5636057193fcfb59e5062f6f3833a62b4f3027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="5ec12-102">3508 - TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="5ec12-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="5ec12-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5ec12-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5ec12-104">ID</span><span class="sxs-lookup"><span data-stu-id="5ec12-104">ID</span></span>|<span data-ttu-id="5ec12-105">3508</span><span class="sxs-lookup"><span data-stu-id="5ec12-105">3508</span></span>|  
|<span data-ttu-id="5ec12-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="5ec12-106">Keywords</span></span>|<span data-ttu-id="5ec12-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="5ec12-107">WFServices</span></span>|  
|<span data-ttu-id="5ec12-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="5ec12-108">Level</span></span>|<span data-ttu-id="5ec12-109">Verbose</span><span class="sxs-lookup"><span data-stu-id="5ec12-109">Verbose</span></span>|  
|<span data-ttu-id="5ec12-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="5ec12-110">Channel</span></span>|<span data-ttu-id="5ec12-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="5ec12-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5ec12-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5ec12-112">Description</span></span>  
 <span data-ttu-id="5ec12-113">Označuje TrackingProfile nebyl nalezen v konfiguračním souboru nebo ActivityDefinitionId neodpovídá profil.</span><span class="sxs-lookup"><span data-stu-id="5ec12-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5ec12-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5ec12-114">Message</span></span>  
 <span data-ttu-id="5ec12-115">'%1' TrackingProfile ActivityDefinitionId '%2' nebyla nalezena.</span><span class="sxs-lookup"><span data-stu-id="5ec12-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="5ec12-116">Buď TrackingProfile nebyl nalezen v konfiguračním souboru nebo ActivityDefinitionId neodpovídá.</span><span class="sxs-lookup"><span data-stu-id="5ec12-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5ec12-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5ec12-117">Details</span></span>  
  
|<span data-ttu-id="5ec12-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="5ec12-118">Data Item Name</span></span>|<span data-ttu-id="5ec12-119">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="5ec12-119">Data Item Type</span></span>|<span data-ttu-id="5ec12-120">Popis</span><span class="sxs-lookup"><span data-stu-id="5ec12-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5ec12-121">TrackingProfile</span><span class="sxs-lookup"><span data-stu-id="5ec12-121">TrackingProfile</span></span>|<span data-ttu-id="5ec12-122">xs:String</span><span class="sxs-lookup"><span data-stu-id="5ec12-122">xs:string</span></span>|<span data-ttu-id="5ec12-123">Název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="5ec12-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="5ec12-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="5ec12-124">ActivityDefinitionId</span></span>|<span data-ttu-id="5ec12-125">xs:String</span><span class="sxs-lookup"><span data-stu-id="5ec12-125">xs:string</span></span>|<span data-ttu-id="5ec12-126">Id definice aktivity.</span><span class="sxs-lookup"><span data-stu-id="5ec12-126">The activity definition id.</span></span>|  
|<span data-ttu-id="5ec12-127">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="5ec12-127">AppDomain</span></span>|<span data-ttu-id="5ec12-128">xs:String</span><span class="sxs-lookup"><span data-stu-id="5ec12-128">xs:string</span></span>|<span data-ttu-id="5ec12-129">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5ec12-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
