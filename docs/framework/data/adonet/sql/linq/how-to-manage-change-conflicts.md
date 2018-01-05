---
title: "Postupy: Správa je v konfliktu změn"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3059adbc9cd2c67035d5f6579e292df80cd87ef3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="b55b2-102">Postupy: Správa je v konfliktu změn</span><span class="sxs-lookup"><span data-stu-id="b55b2-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="b55b2-103">poskytuje kolekci rozhraní API můžete zjistit, hodnocení a řešení konfliktů souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="b55b2-103"> provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b55b2-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b55b2-104">In This Section</span></span>  
 [<span data-ttu-id="b55b2-105">Postupy: Zjištění a vyřešení konfliktních odeslání</span><span class="sxs-lookup"><span data-stu-id="b55b2-105">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="b55b2-106">Popisuje postup zjištění a vyřešení konfliktů souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="b55b2-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="b55b2-107">Postupy: Určení, kdy se mají objevit výjimky souběžnosti</span><span class="sxs-lookup"><span data-stu-id="b55b2-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="b55b2-108">Popisuje, jak určit, když jste musí být informováni o souběžnosti konflikty.</span><span class="sxs-lookup"><span data-stu-id="b55b2-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="b55b2-109">Postupy: Určení, kdy se mají členové testovat na konflikty souběžnosti</span><span class="sxs-lookup"><span data-stu-id="b55b2-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="b55b2-110">Popisuje, jak do atribut členy k určení, zda je provedena kontrola souběžnosti konflikty.</span><span class="sxs-lookup"><span data-stu-id="b55b2-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="b55b2-111">Postupy: Načtení informací o konfliktech entit</span><span class="sxs-lookup"><span data-stu-id="b55b2-111">How to: Retrieve Entity Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="b55b2-112">Popisuje, jak získat informace o konfliktech entity.</span><span class="sxs-lookup"><span data-stu-id="b55b2-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="b55b2-113">Postupy: Načtení informací o konfliktech členů</span><span class="sxs-lookup"><span data-stu-id="b55b2-113">How to: Retrieve Member Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="b55b2-114">Popisuje, jak získat informace o člen je v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="b55b2-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="b55b2-115">Postupy: Řešení konfliktů zachováním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="b55b2-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="b55b2-116">Popisuje, jak chcete přepsat aktuální hodnoty hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="b55b2-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="b55b2-117">Postupy: Řešení konfliktů přepsáním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="b55b2-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="b55b2-118">Popisuje, jak chcete zachovat aktuální hodnoty tak, že přepíše hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="b55b2-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="b55b2-119">Postupy: Řešení konfliktů sloučení s hodnotami v databázi</span><span class="sxs-lookup"><span data-stu-id="b55b2-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="b55b2-120">Popisuje, jak vyřešit konflikt sloučením databáze a aktuální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b55b2-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b55b2-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="b55b2-121">Related Sections</span></span>  
 [<span data-ttu-id="b55b2-122">Optimistická metoda souběžného zpracování: Přehled</span><span class="sxs-lookup"><span data-stu-id="b55b2-122">Optimistic Concurrency: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)  
 <span data-ttu-id="b55b2-123">Popisuje podmínky, které platí pro optimistickou metodu souběžného v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b55b2-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
