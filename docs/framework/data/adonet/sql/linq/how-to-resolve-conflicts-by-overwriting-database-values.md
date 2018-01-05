---
title: "Postupy: řešení konfliktů přepsáním hodnot v databázi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f3155eca2344e32913aaacbd0e2671603824aaf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="4ca22-102">Postupy: řešení konfliktů přepsáním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="4ca22-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="4ca22-103">Chcete-li sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte odeslat znovu provedené změny, můžete použít <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> přepsat hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="4ca22-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="4ca22-104">Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4ca22-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ca22-105">Ve všech případech je nejprve záznamu v klientovi aktualizovat načtením aktualizovaná data z databáze.</span><span class="sxs-lookup"><span data-stu-id="4ca22-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="4ca22-106">Tato akce je zajištěno, že na další pokus o aktualizaci nebudou na stejném kontrolách souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="4ca22-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ca22-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ca22-107">Example</span></span>  
 <span data-ttu-id="4ca22-108">V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 mezitím změnila sloupce asistenta a oddělení.</span><span class="sxs-lookup"><span data-stu-id="4ca22-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="4ca22-109">V následující tabulce jsou uvedeny situaci.</span><span class="sxs-lookup"><span data-stu-id="4ca22-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="4ca22-110">Správce</span><span class="sxs-lookup"><span data-stu-id="4ca22-110">Manager</span></span>|<span data-ttu-id="4ca22-111">Pomocník pro</span><span class="sxs-lookup"><span data-stu-id="4ca22-111">Assistant</span></span>|<span data-ttu-id="4ca22-112">Oddělení</span><span class="sxs-lookup"><span data-stu-id="4ca22-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="4ca22-113">Při dotazu uživatel1 a uživatel2 původního stavu databáze.</span><span class="sxs-lookup"><span data-stu-id="4ca22-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="4ca22-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="4ca22-114">Alfreds</span></span>|<span data-ttu-id="4ca22-115">Marie</span><span class="sxs-lookup"><span data-stu-id="4ca22-115">Maria</span></span>|<span data-ttu-id="4ca22-116">Prodeje</span><span class="sxs-lookup"><span data-stu-id="4ca22-116">Sales</span></span>|  
|<span data-ttu-id="4ca22-117">Uživatel1 připraví odešle tyto změny.</span><span class="sxs-lookup"><span data-stu-id="4ca22-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="4ca22-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="4ca22-118">Alfred</span></span>||<span data-ttu-id="4ca22-119">Marketingové</span><span class="sxs-lookup"><span data-stu-id="4ca22-119">Marketing</span></span>|  
|<span data-ttu-id="4ca22-120">Uživatel2 již odeslána tyto změny.</span><span class="sxs-lookup"><span data-stu-id="4ca22-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="4ca22-121">Marie</span><span class="sxs-lookup"><span data-stu-id="4ca22-121">Mary</span></span>|<span data-ttu-id="4ca22-122">Služba</span><span class="sxs-lookup"><span data-stu-id="4ca22-122">Service</span></span>|  
  
 <span data-ttu-id="4ca22-123">Uživatel1 rozhodne na tento konflikt vyřešit tak, že přepíše hodnot v databázi s aktuální hodnoty členů klienta.</span><span class="sxs-lookup"><span data-stu-id="4ca22-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="4ca22-124">Když uživatel1 vyřeší konflikt pomocí <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, výsledek v databázi je jako v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="4ca22-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="4ca22-125">Správce</span><span class="sxs-lookup"><span data-stu-id="4ca22-125">Manager</span></span>|<span data-ttu-id="4ca22-126">Pomocník pro</span><span class="sxs-lookup"><span data-stu-id="4ca22-126">Assistant</span></span>|<span data-ttu-id="4ca22-127">Oddělení</span><span class="sxs-lookup"><span data-stu-id="4ca22-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="4ca22-128">Nový stav po řešení konfliktů.</span><span class="sxs-lookup"><span data-stu-id="4ca22-128">New state after conflict resolution.</span></span>|<span data-ttu-id="4ca22-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="4ca22-129">Alfred</span></span><br /><br /> <span data-ttu-id="4ca22-130">(z uživatel1)</span><span class="sxs-lookup"><span data-stu-id="4ca22-130">(from User1)</span></span>|<span data-ttu-id="4ca22-131">Marie</span><span class="sxs-lookup"><span data-stu-id="4ca22-131">Maria</span></span><br /><br /> <span data-ttu-id="4ca22-132">(původní)</span><span class="sxs-lookup"><span data-stu-id="4ca22-132">(original)</span></span>|<span data-ttu-id="4ca22-133">Marketingové</span><span class="sxs-lookup"><span data-stu-id="4ca22-133">Marketing</span></span><br /><br /> <span data-ttu-id="4ca22-134">(z uživatel1)</span><span class="sxs-lookup"><span data-stu-id="4ca22-134">(from User1)</span></span>|  
  
 <span data-ttu-id="4ca22-135">Následující příklad kódu ukazuje, jak chcete přepsat aktuální hodnoty členů klienta hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="4ca22-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="4ca22-136">(Bez kontroly nebo vlastní zpracování konfliktů jednotlivými členy nastane.)</span><span class="sxs-lookup"><span data-stu-id="4ca22-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4ca22-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ca22-137">See Also</span></span>  
 [<span data-ttu-id="4ca22-138">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="4ca22-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
