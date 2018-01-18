---
title: "Postupy: řešení konfliktů sloučením s hodnotami databáze"
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
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 942313f87f19345b3656ec241e4c673d3f12601d
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="c33d3-102">Postupy: řešení konfliktů sloučením s hodnotami databáze</span><span class="sxs-lookup"><span data-stu-id="c33d3-102">How to: Resolve Conflicts by Merging with Database Values</span></span>
<span data-ttu-id="c33d3-103">Chcete-li sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte odeslat znovu provedené změny, můžete použít <xref:System.Data.Linq.RefreshMode.KeepChanges> sloučit hodnot v databázi s aktuální hodnoty členů klienta.</span><span class="sxs-lookup"><span data-stu-id="c33d3-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="c33d3-104">Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c33d3-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c33d3-105">Ve všech případech je nejprve záznamu v klientovi aktualizovat načtením aktualizovaná data z databáze.</span><span class="sxs-lookup"><span data-stu-id="c33d3-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="c33d3-106">Tato akce je zajištěno, že na další pokus o aktualizaci nebudou na stejném kontrolách souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="c33d3-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c33d3-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="c33d3-107">Example</span></span>  
 <span data-ttu-id="c33d3-108">V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 mezitím změnila sloupce asistenta a oddělení.</span><span class="sxs-lookup"><span data-stu-id="c33d3-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="c33d3-109">V následující tabulce jsou uvedeny situaci.</span><span class="sxs-lookup"><span data-stu-id="c33d3-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="c33d3-110">Správce</span><span class="sxs-lookup"><span data-stu-id="c33d3-110">Manager</span></span>|<span data-ttu-id="c33d3-111">Pomocník pro</span><span class="sxs-lookup"><span data-stu-id="c33d3-111">Assistant</span></span>|<span data-ttu-id="c33d3-112">Oddělení</span><span class="sxs-lookup"><span data-stu-id="c33d3-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c33d3-113">Při dotazu uživatel1 a uživatel2 původního stavu databáze.</span><span class="sxs-lookup"><span data-stu-id="c33d3-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="c33d3-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="c33d3-114">Alfreds</span></span>|<span data-ttu-id="c33d3-115">Marie</span><span class="sxs-lookup"><span data-stu-id="c33d3-115">Maria</span></span>|<span data-ttu-id="c33d3-116">Prodeje</span><span class="sxs-lookup"><span data-stu-id="c33d3-116">Sales</span></span>|  
|<span data-ttu-id="c33d3-117">Uživatel1 připraví odešle tyto změny.</span><span class="sxs-lookup"><span data-stu-id="c33d3-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="c33d3-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="c33d3-118">Alfred</span></span>||<span data-ttu-id="c33d3-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="c33d3-119">Marketing</span></span>|  
|<span data-ttu-id="c33d3-120">Uživatel2 již odeslána tyto změny.</span><span class="sxs-lookup"><span data-stu-id="c33d3-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="c33d3-121">Marie</span><span class="sxs-lookup"><span data-stu-id="c33d3-121">Mary</span></span>|<span data-ttu-id="c33d3-122">Služba</span><span class="sxs-lookup"><span data-stu-id="c33d3-122">Service</span></span>|  
  
 <span data-ttu-id="c33d3-123">Uživatel1 rozhodne na tento konflikt vyřešte sloučením hodnot v databázi s aktuální hodnoty členů klienta.</span><span class="sxs-lookup"><span data-stu-id="c33d3-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="c33d3-124">Výsledkem bude, že databáze, které hodnoty budou přepsána jenom v případě, že aktuální změn také změnil tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c33d3-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="c33d3-125">Když uživatel1 vyřeší konflikt pomocí <xref:System.Data.Linq.RefreshMode.KeepChanges>, výsledek v databázi je stejně jako v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="c33d3-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="c33d3-126">Správce</span><span class="sxs-lookup"><span data-stu-id="c33d3-126">Manager</span></span>|<span data-ttu-id="c33d3-127">Pomocník pro</span><span class="sxs-lookup"><span data-stu-id="c33d3-127">Assistant</span></span>|<span data-ttu-id="c33d3-128">Oddělení</span><span class="sxs-lookup"><span data-stu-id="c33d3-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c33d3-129">Nový stav po řešení konfliktů.</span><span class="sxs-lookup"><span data-stu-id="c33d3-129">New state after conflict resolution.</span></span>|<span data-ttu-id="c33d3-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="c33d3-130">Alfred</span></span><br /><br /> <span data-ttu-id="c33d3-131">(z uživatel1)</span><span class="sxs-lookup"><span data-stu-id="c33d3-131">(from User1)</span></span>|<span data-ttu-id="c33d3-132">Marie</span><span class="sxs-lookup"><span data-stu-id="c33d3-132">Mary</span></span><br /><br /> <span data-ttu-id="c33d3-133">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="c33d3-133">(from User2)</span></span>|<span data-ttu-id="c33d3-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="c33d3-134">Marketing</span></span><br /><br /> <span data-ttu-id="c33d3-135">(z uživatel1)</span><span class="sxs-lookup"><span data-stu-id="c33d3-135">(from User1)</span></span>|  
  
 <span data-ttu-id="c33d3-136">Následující příklad ukazuje způsob sloučení hodnot v databázi s aktuální hodnoty členů klienta (Pokud klient změnil tuto hodnotu).</span><span class="sxs-lookup"><span data-stu-id="c33d3-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="c33d3-137">Dojde k žádné kontroly nebo vlastní zpracování konfliktů jednotlivými členy.</span><span class="sxs-lookup"><span data-stu-id="c33d3-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c33d3-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="c33d3-138">See Also</span></span>  
 [<span data-ttu-id="c33d3-139">Postupy: Řešení konfliktů přepsáním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="c33d3-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [<span data-ttu-id="c33d3-140">Postupy: Řešení konfliktů zachováním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="c33d3-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [<span data-ttu-id="c33d3-141">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="c33d3-141">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
