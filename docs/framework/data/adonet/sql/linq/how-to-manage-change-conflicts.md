---
title: 'Postupy: Správa konfliktů změn'
ms.date: 03/30/2017
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
ms.openlocfilehash: 49ccb08a375b612e62a8911e98f8ec08058802db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781835"
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="c0794-102">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="c0794-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c0794-103">poskytuje kolekci rozhraní API, která vám pomůžou odhalit, vyhodnocovat a řešit konflikty souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="c0794-103">provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c0794-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c0794-104">In This Section</span></span>  
 [<span data-ttu-id="c0794-105">Postupy: Zjištění a vyřešení konfliktních odeslání</span><span class="sxs-lookup"><span data-stu-id="c0794-105">How to: Detect and Resolve Conflicting Submissions</span></span>](how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="c0794-106">Popisuje, jak detekovat a řešit konflikty souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="c0794-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="c0794-107">Postupy: Určete, kdy jsou vyvolány výjimky souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="c0794-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="c0794-108">Popisuje, jak určit, kdy byste měli být informováni o konfliktech souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="c0794-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="c0794-109">Postupy: Určení členů, kteří jsou testováni pro konflikty souběžnosti</span><span class="sxs-lookup"><span data-stu-id="c0794-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="c0794-110">Popisuje způsob, jakým členové atributu určují, zda mají být kontrolovány konflikty souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="c0794-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="c0794-111">Postupy: Načíst informace o konfliktu entity</span><span class="sxs-lookup"><span data-stu-id="c0794-111">How to: Retrieve Entity Conflict Information</span></span>](how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="c0794-112">Popisuje, jak shromažďovat informace o konfliktech entit.</span><span class="sxs-lookup"><span data-stu-id="c0794-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="c0794-113">Postupy: Načíst informace o konfliktu členů</span><span class="sxs-lookup"><span data-stu-id="c0794-113">How to: Retrieve Member Conflict Information</span></span>](how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="c0794-114">Popisuje, jak získat informace o konfliktech členů.</span><span class="sxs-lookup"><span data-stu-id="c0794-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="c0794-115">Postupy: Řešení konfliktů zachováním hodnot databáze</span><span class="sxs-lookup"><span data-stu-id="c0794-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="c0794-116">Popisuje, jak přepsat aktuální hodnoty hodnotami databáze.</span><span class="sxs-lookup"><span data-stu-id="c0794-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="c0794-117">Postupy: Řešení konfliktů přepsáním hodnot databáze</span><span class="sxs-lookup"><span data-stu-id="c0794-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="c0794-118">Popisuje, jak zachovat aktuální hodnoty přepsáním hodnot databáze.</span><span class="sxs-lookup"><span data-stu-id="c0794-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="c0794-119">Postupy: Řešení konfliktů sloučením s hodnotami databáze</span><span class="sxs-lookup"><span data-stu-id="c0794-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="c0794-120">Popisuje, jak vyřešit konflikt sloučením databáze a aktuálních hodnot.</span><span class="sxs-lookup"><span data-stu-id="c0794-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c0794-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="c0794-121">Related Sections</span></span>  
 [<span data-ttu-id="c0794-122">Optimistická souběžnost: Přehled</span><span class="sxs-lookup"><span data-stu-id="c0794-122">Optimistic Concurrency: Overview</span></span>](optimistic-concurrency-overview.md)  
 <span data-ttu-id="c0794-123">Vysvětluje podmínky, které se vztahují na optimistickou souběžnost v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0794-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
