---
title: 401 – StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: 1776252c362feb3c3ebc04651603944040ceee7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999749"
---
# <a name="401--stopsignpostevent"></a><span data-ttu-id="c32e6-102">401 – StopSignPostEvent</span><span class="sxs-lookup"><span data-stu-id="c32e6-102">401- StopSignPostEvent</span></span>
## <a name="properties"></a><span data-ttu-id="c32e6-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c32e6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c32e6-104">ID</span><span class="sxs-lookup"><span data-stu-id="c32e6-104">ID</span></span>|<span data-ttu-id="c32e6-105">401</span><span class="sxs-lookup"><span data-stu-id="c32e6-105">401</span></span>|  
|<span data-ttu-id="c32e6-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c32e6-106">Keywords</span></span>|<span data-ttu-id="c32e6-107">Poradce při potížích</span><span class="sxs-lookup"><span data-stu-id="c32e6-107">Troubleshooting</span></span>|  
|<span data-ttu-id="c32e6-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="c32e6-108">Level</span></span>|<span data-ttu-id="c32e6-109">Informace o</span><span class="sxs-lookup"><span data-stu-id="c32e6-109">Information</span></span>|  
|<span data-ttu-id="c32e6-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="c32e6-110">Channel</span></span>|<span data-ttu-id="c32e6-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="c32e6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c32e6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c32e6-112">Description</span></span>  
 <span data-ttu-id="c32e6-113">Tato událost označuje konec aktivity začátku do konce.</span><span class="sxs-lookup"><span data-stu-id="c32e6-113">This event marks the end of an end-to-end activity.</span></span> <span data-ttu-id="c32e6-114">Obsahuje název aktivity.</span><span class="sxs-lookup"><span data-stu-id="c32e6-114">It contains the name of the activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c32e6-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="c32e6-115">Message</span></span>  
 <span data-ttu-id="c32e6-116">Hranice aktivity.</span><span class="sxs-lookup"><span data-stu-id="c32e6-116">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c32e6-117">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c32e6-117">Details</span></span>  
  
|<span data-ttu-id="c32e6-118">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="c32e6-118">Data Item Name</span></span>|<span data-ttu-id="c32e6-119">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="c32e6-119">Data Item Type</span></span>|<span data-ttu-id="c32e6-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c32e6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c32e6-121">Rozšířená Data</span><span class="sxs-lookup"><span data-stu-id="c32e6-121">Extended Data</span></span>|`xs:string`|<span data-ttu-id="c32e6-122">Název aktivity.</span><span class="sxs-lookup"><span data-stu-id="c32e6-122">The name of the activity.</span></span>|  
|<span data-ttu-id="c32e6-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c32e6-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c32e6-124">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c32e6-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
