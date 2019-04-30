---
title: 'Postupy: Správa konfliktů změn'
ms.date: 03/30/2017
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
ms.openlocfilehash: 7858dc304d281dfb99755d83eec19b421f63d2ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903380"
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="09787-102">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="09787-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="09787-103">poskytuje kolekci rozhraní API pro zjišťování, vyhodnocení a vyřešení konfliktů souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="09787-103">provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09787-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="09787-104">In This Section</span></span>  
 [<span data-ttu-id="09787-105">Postupy: Zjištění a vyřešení konfliktních odeslání</span><span class="sxs-lookup"><span data-stu-id="09787-105">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="09787-106">Popisuje postup zjištění a vyřešení konfliktů souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="09787-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="09787-107">Postupy: Určete, že se že mají objevit výjimky souběžnosti při</span><span class="sxs-lookup"><span data-stu-id="09787-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="09787-108">Popisuje, jak určit, při které by měla vycházet z konfliktů souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="09787-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="09787-109">Postupy: Určete, že které členy jsou testovat na konflikty souběžnosti</span><span class="sxs-lookup"><span data-stu-id="09787-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="09787-110">Popisuje, jak atribut členy k určení, zda jsou kontrolovány na konflikty souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="09787-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="09787-111">Postupy: Načtení informací o konfliktech entit</span><span class="sxs-lookup"><span data-stu-id="09787-111">How to: Retrieve Entity Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="09787-112">Popisuje, jak získat informace o konfliktech entit.</span><span class="sxs-lookup"><span data-stu-id="09787-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="09787-113">Postupy: Načtení informací o konfliktech členů</span><span class="sxs-lookup"><span data-stu-id="09787-113">How to: Retrieve Member Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="09787-114">Popisuje, jak získat informace o konfliktech členů.</span><span class="sxs-lookup"><span data-stu-id="09787-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="09787-115">Postupy: Řešení konfliktů zachováním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="09787-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="09787-116">Popisuje, jak přepsat aktuální hodnoty s hodnotami v databázi.</span><span class="sxs-lookup"><span data-stu-id="09787-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="09787-117">Postupy: Řešení konfliktů přepsáním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="09787-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="09787-118">Popisuje, jak zachovat aktuální hodnoty přepsáním hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="09787-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="09787-119">Postupy: Řešení konfliktů sloučení s hodnotami v databázi</span><span class="sxs-lookup"><span data-stu-id="09787-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="09787-120">Popisuje, jak vyřešit konflikt sloučení databáze a aktuální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="09787-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09787-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="09787-121">Related Sections</span></span>  
 [<span data-ttu-id="09787-122">Optimistického řízení souběžnosti: Přehled</span><span class="sxs-lookup"><span data-stu-id="09787-122">Optimistic Concurrency: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)  
 <span data-ttu-id="09787-123">Vysvětluje, která se vztahují k optimistického řízení souběžnosti v [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09787-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
