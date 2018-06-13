---
title: 'Postupy: řešení konfliktů zachováním hodnot v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: d0d59c520beaab2d6c8c1594ee81a3eaecf1d03e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361692"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="27feb-102">Postupy: řešení konfliktů zachováním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="27feb-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="27feb-103">Chcete-li sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte odeslat znovu provedené změny, můžete použít <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> uchovat na hodnoty zjištěné v databázi.</span><span class="sxs-lookup"><span data-stu-id="27feb-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="27feb-104">Aktuální hodnoty v objektu model se pak přepíší.</span><span class="sxs-lookup"><span data-stu-id="27feb-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="27feb-105">Další informace najdete v tématu [optimistickou metodu souběžného: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="27feb-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27feb-106">Ve všech případech je nejprve záznamu v klientovi aktualizovat načtením aktualizovaná data z databáze.</span><span class="sxs-lookup"><span data-stu-id="27feb-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="27feb-107">Tato akce je zajištěno, že na další pokus o aktualizaci nebudou na stejném kontrolách souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="27feb-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27feb-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="27feb-108">Example</span></span>  
 <span data-ttu-id="27feb-109">V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 mezitím změnila sloupce asistenta a oddělení.</span><span class="sxs-lookup"><span data-stu-id="27feb-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="27feb-110">V následující tabulce jsou uvedeny situaci.</span><span class="sxs-lookup"><span data-stu-id="27feb-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="27feb-111">Správce</span><span class="sxs-lookup"><span data-stu-id="27feb-111">Manager</span></span>|<span data-ttu-id="27feb-112">Pomocník pro</span><span class="sxs-lookup"><span data-stu-id="27feb-112">Assistant</span></span>|<span data-ttu-id="27feb-113">Oddělení</span><span class="sxs-lookup"><span data-stu-id="27feb-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="27feb-114">Při dotazu uživatel1 a uživatel2 původního stavu databáze.</span><span class="sxs-lookup"><span data-stu-id="27feb-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="27feb-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="27feb-115">Alfreds</span></span>|<span data-ttu-id="27feb-116">Marie</span><span class="sxs-lookup"><span data-stu-id="27feb-116">Maria</span></span>|<span data-ttu-id="27feb-117">Prodeje</span><span class="sxs-lookup"><span data-stu-id="27feb-117">Sales</span></span>|  
|<span data-ttu-id="27feb-118">Uživatel1 připraví odešle tyto změny.</span><span class="sxs-lookup"><span data-stu-id="27feb-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="27feb-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="27feb-119">Alfred</span></span>||<span data-ttu-id="27feb-120">Marketingové</span><span class="sxs-lookup"><span data-stu-id="27feb-120">Marketing</span></span>|  
|<span data-ttu-id="27feb-121">Uživatel2 již odeslána tyto změny.</span><span class="sxs-lookup"><span data-stu-id="27feb-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="27feb-122">Marie</span><span class="sxs-lookup"><span data-stu-id="27feb-122">Mary</span></span>|<span data-ttu-id="27feb-123">Služba</span><span class="sxs-lookup"><span data-stu-id="27feb-123">Service</span></span>|  
  
 <span data-ttu-id="27feb-124">Uživatel1 rozhodne na tento konflikt vyřešit tak, že novější hodnot v databázi přepsat aktuální hodnoty v objektu modelu.</span><span class="sxs-lookup"><span data-stu-id="27feb-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="27feb-125">Když uživatel1 vyřeší konflikt pomocí <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, výsledek v databázi je v tabulce následující:</span><span class="sxs-lookup"><span data-stu-id="27feb-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="27feb-126">Správce</span><span class="sxs-lookup"><span data-stu-id="27feb-126">Manager</span></span>|<span data-ttu-id="27feb-127">Pomocník pro</span><span class="sxs-lookup"><span data-stu-id="27feb-127">Assistant</span></span>|<span data-ttu-id="27feb-128">Oddělení</span><span class="sxs-lookup"><span data-stu-id="27feb-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="27feb-129">Nový stav po řešení konfliktů.</span><span class="sxs-lookup"><span data-stu-id="27feb-129">New state after conflict resolution.</span></span>|<span data-ttu-id="27feb-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="27feb-130">Alfreds</span></span><br /><br /> <span data-ttu-id="27feb-131">(původní)</span><span class="sxs-lookup"><span data-stu-id="27feb-131">(original)</span></span>|<span data-ttu-id="27feb-132">Marie</span><span class="sxs-lookup"><span data-stu-id="27feb-132">Mary</span></span><br /><br /> <span data-ttu-id="27feb-133">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="27feb-133">(from User2)</span></span>|<span data-ttu-id="27feb-134">Služba</span><span class="sxs-lookup"><span data-stu-id="27feb-134">Service</span></span><br /><br /> <span data-ttu-id="27feb-135">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="27feb-135">(from User2)</span></span>|  
  
 <span data-ttu-id="27feb-136">Následující příklad kódu ukazuje, jak přepsat aktuální hodnoty v objektovém modelu pomocí hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="27feb-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="27feb-137">(Bez kontroly nebo vlastní zpracování konfliktů jednotlivými členy nastane.)</span><span class="sxs-lookup"><span data-stu-id="27feb-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="27feb-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="27feb-138">See Also</span></span>  
 [<span data-ttu-id="27feb-139">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="27feb-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
