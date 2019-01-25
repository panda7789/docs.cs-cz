---
title: 'Postupy: Řešení konfliktů zachováním hodnot v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: f647dad951acfbc309257212018db32e655169df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531262"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="d87e2-102">Postupy: Řešení konfliktů zachováním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="d87e2-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="d87e2-103">Sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte znovu odeslat změny, můžete použít <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> zachovat na hodnoty zjištěné v databázi.</span><span class="sxs-lookup"><span data-stu-id="d87e2-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="d87e2-104">Pak budou přepsány aktuální hodnoty v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="d87e2-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="d87e2-105">Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d87e2-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d87e2-106">Ve všech případech se záznam na straně klienta se aktualizují nejprve načtením aktualizovaná data z databáze.</span><span class="sxs-lookup"><span data-stu-id="d87e2-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="d87e2-107">Tato akce zajistí, že dalším pokusu o aktualizaci nebudou na stejném kontrolách souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="d87e2-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d87e2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d87e2-108">Example</span></span>  
 <span data-ttu-id="d87e2-109">V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> User1 se pokusí odeslat změny, protože uživatel2 se mezitím změnila Pomocníka s nastavením a oddělení sloupců je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d87e2-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="d87e2-110">V následující tabulce jsou uvedeny situace.</span><span class="sxs-lookup"><span data-stu-id="d87e2-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="d87e2-111">Správce</span><span class="sxs-lookup"><span data-stu-id="d87e2-111">Manager</span></span>|<span data-ttu-id="d87e2-112">Pomocníka s nastavením</span><span class="sxs-lookup"><span data-stu-id="d87e2-112">Assistant</span></span>|<span data-ttu-id="d87e2-113">Oddělení</span><span class="sxs-lookup"><span data-stu-id="d87e2-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="d87e2-114">Když dotazovat uživatel1, uživatel2 tak původní stav databáze.</span><span class="sxs-lookup"><span data-stu-id="d87e2-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="d87e2-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="d87e2-115">Alfreds</span></span>|<span data-ttu-id="d87e2-116">Maria</span><span class="sxs-lookup"><span data-stu-id="d87e2-116">Maria</span></span>|<span data-ttu-id="d87e2-117">Prodej</span><span class="sxs-lookup"><span data-stu-id="d87e2-117">Sales</span></span>|  
|<span data-ttu-id="d87e2-118">Uživatel1 připravuje k odeslání těchto změn.</span><span class="sxs-lookup"><span data-stu-id="d87e2-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="d87e2-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="d87e2-119">Alfred</span></span>||<span data-ttu-id="d87e2-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="d87e2-120">Marketing</span></span>|  
|<span data-ttu-id="d87e2-121">Uživatel2 už odeslal tyto změny.</span><span class="sxs-lookup"><span data-stu-id="d87e2-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="d87e2-122">Mary</span><span class="sxs-lookup"><span data-stu-id="d87e2-122">Mary</span></span>|<span data-ttu-id="d87e2-123">Služba</span><span class="sxs-lookup"><span data-stu-id="d87e2-123">Service</span></span>|  
  
 <span data-ttu-id="d87e2-124">Uživatel User1 se rozhodne tento konflikt vyřešit tím, že novější hodnot v databázi přepsat aktuální hodnoty v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="d87e2-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="d87e2-125">Když uživatel User1 konflikt pomocí <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, výsledek v databázi je následujícím způsobem v tabulce:</span><span class="sxs-lookup"><span data-stu-id="d87e2-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="d87e2-126">Správce</span><span class="sxs-lookup"><span data-stu-id="d87e2-126">Manager</span></span>|<span data-ttu-id="d87e2-127">Pomocníka s nastavením</span><span class="sxs-lookup"><span data-stu-id="d87e2-127">Assistant</span></span>|<span data-ttu-id="d87e2-128">Oddělení</span><span class="sxs-lookup"><span data-stu-id="d87e2-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="d87e2-129">Nový stav po vyřešení konfliktu.</span><span class="sxs-lookup"><span data-stu-id="d87e2-129">New state after conflict resolution.</span></span>|<span data-ttu-id="d87e2-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="d87e2-130">Alfreds</span></span><br /><br /> <span data-ttu-id="d87e2-131">(původní)</span><span class="sxs-lookup"><span data-stu-id="d87e2-131">(original)</span></span>|<span data-ttu-id="d87e2-132">Mary</span><span class="sxs-lookup"><span data-stu-id="d87e2-132">Mary</span></span><br /><br /> <span data-ttu-id="d87e2-133">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="d87e2-133">(from User2)</span></span>|<span data-ttu-id="d87e2-134">Služba</span><span class="sxs-lookup"><span data-stu-id="d87e2-134">Service</span></span><br /><br /> <span data-ttu-id="d87e2-135">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="d87e2-135">(from User2)</span></span>|  
  
 <span data-ttu-id="d87e2-136">Následující příklad kódu ukazuje, jak přepsat aktuální hodnoty v objektovém modelu pomocí hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="d87e2-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="d87e2-137">(Žádné kontroly nebo vlastního zpracování konfliktů jednotliví členové dojde k.)</span><span class="sxs-lookup"><span data-stu-id="d87e2-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d87e2-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d87e2-138">See also</span></span>
- [<span data-ttu-id="d87e2-139">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="d87e2-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
