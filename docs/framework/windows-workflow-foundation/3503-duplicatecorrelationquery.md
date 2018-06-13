---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511397"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="225d5-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="225d5-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="225d5-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="225d5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="225d5-104">ID</span><span class="sxs-lookup"><span data-stu-id="225d5-104">ID</span></span>|<span data-ttu-id="225d5-105">3503</span><span class="sxs-lookup"><span data-stu-id="225d5-105">3503</span></span>|  
|<span data-ttu-id="225d5-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="225d5-106">Keywords</span></span>|<span data-ttu-id="225d5-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="225d5-107">WFServices</span></span>|  
|<span data-ttu-id="225d5-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="225d5-108">Level</span></span>|<span data-ttu-id="225d5-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="225d5-109">Warning</span></span>|  
|<span data-ttu-id="225d5-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="225d5-110">Channel</span></span>|<span data-ttu-id="225d5-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="225d5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="225d5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="225d5-112">Description</span></span>  
 <span data-ttu-id="225d5-113">Označuje, že byl nalezen duplicitní CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="225d5-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="225d5-114">Duplicitní dotaz nebude používat při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="225d5-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="225d5-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="225d5-115">Message</span></span>  
 <span data-ttu-id="225d5-116">Místo, kde byla nalezena duplicitní CorrelationQuery = '%1'.</span><span class="sxs-lookup"><span data-stu-id="225d5-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="225d5-117">Tento dotaz duplicitní nebude používat při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="225d5-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="225d5-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="225d5-118">Details</span></span>  
  
|<span data-ttu-id="225d5-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="225d5-119">Data Item Name</span></span>|<span data-ttu-id="225d5-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="225d5-120">Data Item Type</span></span>|<span data-ttu-id="225d5-121">Popis</span><span class="sxs-lookup"><span data-stu-id="225d5-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="225d5-122">Where</span><span class="sxs-lookup"><span data-stu-id="225d5-122">Where</span></span>|<span data-ttu-id="225d5-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="225d5-123">xs:string</span></span>|<span data-ttu-id="225d5-124">Where část dotazu korelace.</span><span class="sxs-lookup"><span data-stu-id="225d5-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="225d5-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="225d5-125">AppDomain</span></span>|<span data-ttu-id="225d5-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="225d5-126">xs:string</span></span>|<span data-ttu-id="225d5-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="225d5-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
