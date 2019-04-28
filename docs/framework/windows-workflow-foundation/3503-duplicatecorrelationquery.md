---
title: 3503 – DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755594"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="80044-102">3503 – DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="80044-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="80044-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="80044-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80044-104">ID</span><span class="sxs-lookup"><span data-stu-id="80044-104">ID</span></span>|<span data-ttu-id="80044-105">3503</span><span class="sxs-lookup"><span data-stu-id="80044-105">3503</span></span>|  
|<span data-ttu-id="80044-106">klíčová slova</span><span class="sxs-lookup"><span data-stu-id="80044-106">Keywords</span></span>|<span data-ttu-id="80044-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="80044-107">WFServices</span></span>|  
|<span data-ttu-id="80044-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="80044-108">Level</span></span>|<span data-ttu-id="80044-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="80044-109">Warning</span></span>|  
|<span data-ttu-id="80044-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="80044-110">Channel</span></span>|<span data-ttu-id="80044-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="80044-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="80044-112">Popis</span><span class="sxs-lookup"><span data-stu-id="80044-112">Description</span></span>  
 <span data-ttu-id="80044-113">Označuje, že duplicitní CorrelationQuery byl nalezen.</span><span class="sxs-lookup"><span data-stu-id="80044-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="80044-114">Duplicitní dotaz nebude použit při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="80044-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="80044-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="80044-115">Message</span></span>  
 <span data-ttu-id="80044-116">Duplicitní CorrelationQuery byl nalezen s klauzulí Where = '%1'.</span><span class="sxs-lookup"><span data-stu-id="80044-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="80044-117">Tento duplicitní dotaz nebude použit při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="80044-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="80044-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="80044-118">Details</span></span>  
  
|<span data-ttu-id="80044-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="80044-119">Data Item Name</span></span>|<span data-ttu-id="80044-120">Datový typ položky</span><span class="sxs-lookup"><span data-stu-id="80044-120">Data Item Type</span></span>|<span data-ttu-id="80044-121">Popis</span><span class="sxs-lookup"><span data-stu-id="80044-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="80044-122">Where</span><span class="sxs-lookup"><span data-stu-id="80044-122">Where</span></span>|<span data-ttu-id="80044-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="80044-123">xs:string</span></span>|<span data-ttu-id="80044-124">Where korelace dotazu.</span><span class="sxs-lookup"><span data-stu-id="80044-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="80044-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="80044-125">AppDomain</span></span>|<span data-ttu-id="80044-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="80044-126">xs:string</span></span>|<span data-ttu-id="80044-127">Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="80044-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
