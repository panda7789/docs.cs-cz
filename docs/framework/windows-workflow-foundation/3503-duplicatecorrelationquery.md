---
title: 3503 - DuplicateCorrelationQuery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60367b33e1e57cce8646b4fcde79c7d4fd20a4cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="8a8e4-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="8a8e4-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="8a8e4-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8a8e4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a8e4-104">ID</span><span class="sxs-lookup"><span data-stu-id="8a8e4-104">ID</span></span>|<span data-ttu-id="8a8e4-105">3503</span><span class="sxs-lookup"><span data-stu-id="8a8e4-105">3503</span></span>|  
|<span data-ttu-id="8a8e4-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="8a8e4-106">Keywords</span></span>|<span data-ttu-id="8a8e4-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8a8e4-107">WFServices</span></span>|  
|<span data-ttu-id="8a8e4-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="8a8e4-108">Level</span></span>|<span data-ttu-id="8a8e4-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="8a8e4-109">Warning</span></span>|  
|<span data-ttu-id="8a8e4-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="8a8e4-110">Channel</span></span>|<span data-ttu-id="8a8e4-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="8a8e4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8a8e4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8a8e4-112">Description</span></span>  
 <span data-ttu-id="8a8e4-113">Označuje, že byl nalezen duplicitní CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="8a8e4-114">Duplicitní dotaz nebude používat při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8a8e4-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="8a8e4-115">Message</span></span>  
 <span data-ttu-id="8a8e4-116">Místo, kde byla nalezena duplicitní CorrelationQuery = '%1'.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="8a8e4-117">Tento dotaz duplicitní nebude používat při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8a8e4-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8a8e4-118">Details</span></span>  
  
|<span data-ttu-id="8a8e4-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="8a8e4-119">Data Item Name</span></span>|<span data-ttu-id="8a8e4-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="8a8e4-120">Data Item Type</span></span>|<span data-ttu-id="8a8e4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="8a8e4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8a8e4-122">Where</span><span class="sxs-lookup"><span data-stu-id="8a8e4-122">Where</span></span>|<span data-ttu-id="8a8e4-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="8a8e4-123">xs:string</span></span>|<span data-ttu-id="8a8e4-124">Where část dotazu korelace.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="8a8e4-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="8a8e4-125">AppDomain</span></span>|<span data-ttu-id="8a8e4-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="8a8e4-126">xs:string</span></span>|<span data-ttu-id="8a8e4-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
