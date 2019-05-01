---
title: 'Postupy: Řešení konfliktů zachováním hodnot v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: 8440ffe61e254403357970d771aea207a6eb6092
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037658"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="01407-102">Postupy: Řešení konfliktů zachováním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="01407-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="01407-103">Sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte znovu odeslat změny, můžete použít <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> zachovat na hodnoty zjištěné v databázi.</span><span class="sxs-lookup"><span data-stu-id="01407-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="01407-104">Pak budou přepsány aktuální hodnoty v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="01407-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="01407-105">Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="01407-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01407-106">Ve všech případech se záznam na straně klienta se aktualizují nejprve načtením aktualizovaná data z databáze.</span><span class="sxs-lookup"><span data-stu-id="01407-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="01407-107">Tato akce zajistí, že dalším pokusu o aktualizaci nebudou na stejném kontrolách souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="01407-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01407-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="01407-108">Example</span></span>  
 <span data-ttu-id="01407-109">V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> User1 se pokusí odeslat změny, protože uživatel2 se mezitím změnila Pomocníka s nastavením a oddělení sloupců je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="01407-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="01407-110">V následující tabulce jsou uvedeny situace.</span><span class="sxs-lookup"><span data-stu-id="01407-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="01407-111">Správce</span><span class="sxs-lookup"><span data-stu-id="01407-111">Manager</span></span>|<span data-ttu-id="01407-112">Pomocníka s nastavením</span><span class="sxs-lookup"><span data-stu-id="01407-112">Assistant</span></span>|<span data-ttu-id="01407-113">Oddělení</span><span class="sxs-lookup"><span data-stu-id="01407-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="01407-114">Když dotazovat uživatel1, uživatel2 tak původní stav databáze.</span><span class="sxs-lookup"><span data-stu-id="01407-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="01407-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="01407-115">Alfreds</span></span>|<span data-ttu-id="01407-116">Maria</span><span class="sxs-lookup"><span data-stu-id="01407-116">Maria</span></span>|<span data-ttu-id="01407-117">Prodej</span><span class="sxs-lookup"><span data-stu-id="01407-117">Sales</span></span>|  
|<span data-ttu-id="01407-118">Uživatel1 připravuje k odeslání těchto změn.</span><span class="sxs-lookup"><span data-stu-id="01407-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="01407-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="01407-119">Alfred</span></span>||<span data-ttu-id="01407-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="01407-120">Marketing</span></span>|  
|<span data-ttu-id="01407-121">Uživatel2 už odeslal tyto změny.</span><span class="sxs-lookup"><span data-stu-id="01407-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="01407-122">Mary</span><span class="sxs-lookup"><span data-stu-id="01407-122">Mary</span></span>|<span data-ttu-id="01407-123">Služba</span><span class="sxs-lookup"><span data-stu-id="01407-123">Service</span></span>|  
  
 <span data-ttu-id="01407-124">Uživatel User1 se rozhodne tento konflikt vyřešit tím, že novější hodnot v databázi přepsat aktuální hodnoty v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="01407-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="01407-125">Když uživatel User1 konflikt pomocí <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, výsledek v databázi je následujícím způsobem v tabulce:</span><span class="sxs-lookup"><span data-stu-id="01407-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="01407-126">Správce</span><span class="sxs-lookup"><span data-stu-id="01407-126">Manager</span></span>|<span data-ttu-id="01407-127">Pomocníka s nastavením</span><span class="sxs-lookup"><span data-stu-id="01407-127">Assistant</span></span>|<span data-ttu-id="01407-128">Oddělení</span><span class="sxs-lookup"><span data-stu-id="01407-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="01407-129">Nový stav po vyřešení konfliktu.</span><span class="sxs-lookup"><span data-stu-id="01407-129">New state after conflict resolution.</span></span>|<span data-ttu-id="01407-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="01407-130">Alfreds</span></span><br /><br /> <span data-ttu-id="01407-131">(původní)</span><span class="sxs-lookup"><span data-stu-id="01407-131">(original)</span></span>|<span data-ttu-id="01407-132">Mary</span><span class="sxs-lookup"><span data-stu-id="01407-132">Mary</span></span><br /><br /> <span data-ttu-id="01407-133">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="01407-133">(from User2)</span></span>|<span data-ttu-id="01407-134">Služba</span><span class="sxs-lookup"><span data-stu-id="01407-134">Service</span></span><br /><br /> <span data-ttu-id="01407-135">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="01407-135">(from User2)</span></span>|  
  
 <span data-ttu-id="01407-136">Následující příklad kódu ukazuje, jak přepsat aktuální hodnoty v objektovém modelu pomocí hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="01407-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="01407-137">(Žádné kontroly nebo vlastního zpracování konfliktů jednotliví členové dojde k.)</span><span class="sxs-lookup"><span data-stu-id="01407-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="01407-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01407-138">See also</span></span>

- [<span data-ttu-id="01407-139">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="01407-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
