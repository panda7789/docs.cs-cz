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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 997bdf4423364e9b5361635820849a6bde9e8960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="3b897-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="3b897-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="3b897-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3b897-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3b897-104">ID</span><span class="sxs-lookup"><span data-stu-id="3b897-104">ID</span></span>|<span data-ttu-id="3b897-105">3503</span><span class="sxs-lookup"><span data-stu-id="3b897-105">3503</span></span>|  
|<span data-ttu-id="3b897-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3b897-106">Keywords</span></span>|<span data-ttu-id="3b897-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="3b897-107">WFServices</span></span>|  
|<span data-ttu-id="3b897-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="3b897-108">Level</span></span>|<span data-ttu-id="3b897-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="3b897-109">Warning</span></span>|  
|<span data-ttu-id="3b897-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="3b897-110">Channel</span></span>|<span data-ttu-id="3b897-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="3b897-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3b897-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3b897-112">Description</span></span>  
 <span data-ttu-id="3b897-113">Označuje, že byl nalezen duplicitní CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="3b897-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="3b897-114">Duplicitní dotaz nebude používat při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="3b897-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3b897-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3b897-115">Message</span></span>  
 <span data-ttu-id="3b897-116">Místo, kde byla nalezena duplicitní CorrelationQuery = '%1'.</span><span class="sxs-lookup"><span data-stu-id="3b897-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="3b897-117">Tento dotaz duplicitní nebude používat při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="3b897-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3b897-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="3b897-118">Details</span></span>  
  
|<span data-ttu-id="3b897-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="3b897-119">Data Item Name</span></span>|<span data-ttu-id="3b897-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="3b897-120">Data Item Type</span></span>|<span data-ttu-id="3b897-121">Popis</span><span class="sxs-lookup"><span data-stu-id="3b897-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3b897-122">Where</span><span class="sxs-lookup"><span data-stu-id="3b897-122">Where</span></span>|<span data-ttu-id="3b897-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="3b897-123">xs:string</span></span>|<span data-ttu-id="3b897-124">Where část dotazu korelace.</span><span class="sxs-lookup"><span data-stu-id="3b897-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="3b897-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="3b897-125">AppDomain</span></span>|<span data-ttu-id="3b897-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="3b897-126">xs:string</span></span>|<span data-ttu-id="3b897-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3b897-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
