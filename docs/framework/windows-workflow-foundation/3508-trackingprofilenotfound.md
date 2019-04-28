---
title: 3508 – TrackingProfileNotFound
ms.date: 03/30/2017
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
ms.openlocfilehash: 94c7ce231df241778f7c6ec5fe5998eae364750d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755568"
---
# <a name="3508---trackingprofilenotfound"></a><span data-ttu-id="62805-102">3508 – TrackingProfileNotFound</span><span class="sxs-lookup"><span data-stu-id="62805-102">3508 - TrackingProfileNotFound</span></span>
## <a name="properties"></a><span data-ttu-id="62805-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="62805-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="62805-104">ID</span><span class="sxs-lookup"><span data-stu-id="62805-104">ID</span></span>|<span data-ttu-id="62805-105">3508</span><span class="sxs-lookup"><span data-stu-id="62805-105">3508</span></span>|  
|<span data-ttu-id="62805-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="62805-106">Keywords</span></span>|<span data-ttu-id="62805-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="62805-107">WFServices</span></span>|  
|<span data-ttu-id="62805-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="62805-108">Level</span></span>|<span data-ttu-id="62805-109">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="62805-109">Verbose</span></span>|  
|<span data-ttu-id="62805-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="62805-110">Channel</span></span>|<span data-ttu-id="62805-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="62805-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="62805-112">Popis</span><span class="sxs-lookup"><span data-stu-id="62805-112">Description</span></span>  
 <span data-ttu-id="62805-113">Označuje buď nebyl nalezen profil TrackingProfile v konfiguračním souboru nebo ActivityDefinitionId neodpovídá profilu.</span><span class="sxs-lookup"><span data-stu-id="62805-113">Indicates either a TrackingProfile is not found in the config file or the ActivityDefinitionId does not match the profile.</span></span>  
  
## <a name="message"></a><span data-ttu-id="62805-114">Zpráva</span><span class="sxs-lookup"><span data-stu-id="62805-114">Message</span></span>  
 <span data-ttu-id="62805-115">Profil TrackingProfile '%1' pro ActivityDefinitionId '%2' nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="62805-115">TrackingProfile '%1' for the ActivityDefinitionId '%2' not found.</span></span> <span data-ttu-id="62805-116">Buď nebyl nalezen profil TrackingProfile v konfiguračním souboru nebo ActivityDefinitionId neodpovídá.</span><span class="sxs-lookup"><span data-stu-id="62805-116">Either the TrackingProfile is not found in the config file or the ActivityDefinitionId does not match.</span></span>  
  
## <a name="details"></a><span data-ttu-id="62805-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="62805-117">Details</span></span>  
  
|<span data-ttu-id="62805-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="62805-118">Data Item Name</span></span>|<span data-ttu-id="62805-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="62805-119">Data Item Type</span></span>|<span data-ttu-id="62805-120">Popis</span><span class="sxs-lookup"><span data-stu-id="62805-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="62805-121">vlastnosti TrackingProfile.</span><span class="sxs-lookup"><span data-stu-id="62805-121">TrackingProfile</span></span>|<span data-ttu-id="62805-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="62805-122">xs:string</span></span>|<span data-ttu-id="62805-123">Název profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="62805-123">The name of the tracking profile.</span></span>|  
|<span data-ttu-id="62805-124">ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="62805-124">ActivityDefinitionId</span></span>|<span data-ttu-id="62805-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="62805-125">xs:string</span></span>|<span data-ttu-id="62805-126">Id definice aktivity.</span><span class="sxs-lookup"><span data-stu-id="62805-126">The activity definition id.</span></span>|  
|<span data-ttu-id="62805-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="62805-127">AppDomain</span></span>|<span data-ttu-id="62805-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="62805-128">xs:string</span></span>|<span data-ttu-id="62805-129">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="62805-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
