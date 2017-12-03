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
ms.openlocfilehash: 4b86289340c35d24552b1d524a3cceaacb2f0420
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="f4cd9-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="f4cd9-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="f4cd9-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f4cd9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4cd9-104">ID</span><span class="sxs-lookup"><span data-stu-id="f4cd9-104">ID</span></span>|<span data-ttu-id="f4cd9-105">3503</span><span class="sxs-lookup"><span data-stu-id="f4cd9-105">3503</span></span>|  
|<span data-ttu-id="f4cd9-106">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f4cd9-106">Keywords</span></span>|<span data-ttu-id="f4cd9-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="f4cd9-107">WFServices</span></span>|  
|<span data-ttu-id="f4cd9-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="f4cd9-108">Level</span></span>|<span data-ttu-id="f4cd9-109">Upozornění</span><span class="sxs-lookup"><span data-stu-id="f4cd9-109">Warning</span></span>|  
|<span data-ttu-id="f4cd9-110">Kanál</span><span class="sxs-lookup"><span data-stu-id="f4cd9-110">Channel</span></span>|<span data-ttu-id="f4cd9-111">Aplikaci Microsoft Windows Server – aplikace nebo analytické</span><span class="sxs-lookup"><span data-stu-id="f4cd9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f4cd9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f4cd9-112">Description</span></span>  
 <span data-ttu-id="f4cd9-113">Označuje, že byl nalezen duplicitní CorrelationQuery.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="f4cd9-114">Duplicitní dotaz nebude používat při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f4cd9-115">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f4cd9-115">Message</span></span>  
 <span data-ttu-id="f4cd9-116">Místo, kde byla nalezena duplicitní CorrelationQuery = '%1'.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="f4cd9-117">Tento dotaz duplicitní nebude používat při výpočtu korelace.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f4cd9-118">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="f4cd9-118">Details</span></span>  
  
|<span data-ttu-id="f4cd9-119">Název položky dat</span><span class="sxs-lookup"><span data-stu-id="f4cd9-119">Data Item Name</span></span>|<span data-ttu-id="f4cd9-120">Datová položka – Typ</span><span class="sxs-lookup"><span data-stu-id="f4cd9-120">Data Item Type</span></span>|<span data-ttu-id="f4cd9-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f4cd9-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f4cd9-122">Where</span><span class="sxs-lookup"><span data-stu-id="f4cd9-122">Where</span></span>|<span data-ttu-id="f4cd9-123">xs:String</span><span class="sxs-lookup"><span data-stu-id="f4cd9-123">xs:string</span></span>|<span data-ttu-id="f4cd9-124">Where část dotazu korelace.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="f4cd9-125">Domény aplikace</span><span class="sxs-lookup"><span data-stu-id="f4cd9-125">AppDomain</span></span>|<span data-ttu-id="f4cd9-126">xs:String</span><span class="sxs-lookup"><span data-stu-id="f4cd9-126">xs:string</span></span>|<span data-ttu-id="f4cd9-127">Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f4cd9-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
