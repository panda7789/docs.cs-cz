---
title: 'Postupy: Řešení konfliktů přepsáním hodnot v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 7b8d7cf8ab2335c064062ed3ab4072d81e8042fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189115"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="92d93-102">Postupy: Řešení konfliktů přepsáním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="92d93-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="92d93-103">Sjednocení rozdílů mezi hodnotami očekávaných a aktuálních databáze, než se pokusíte znovu odeslat změny, můžete použít <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> pro přepsání hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="92d93-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="92d93-104">Další informace najdete v tématu [optimistického řízení souběžnosti: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="92d93-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92d93-105">Ve všech případech se záznam na straně klienta se aktualizují nejprve načtením aktualizovaná data z databáze.</span><span class="sxs-lookup"><span data-stu-id="92d93-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="92d93-106">Tato akce zajistí, že dalším pokusu o aktualizaci nebudou na stejném kontrolách souběžnosti.</span><span class="sxs-lookup"><span data-stu-id="92d93-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92d93-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="92d93-107">Example</span></span>  
 <span data-ttu-id="92d93-108">V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> User1 se pokusí odeslat změny, protože uživatel2 se mezitím změnila Pomocníka s nastavením a oddělení sloupců je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="92d93-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="92d93-109">V následující tabulce jsou uvedeny situace.</span><span class="sxs-lookup"><span data-stu-id="92d93-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="92d93-110">Správce</span><span class="sxs-lookup"><span data-stu-id="92d93-110">Manager</span></span>|<span data-ttu-id="92d93-111">Pomocníka s nastavením</span><span class="sxs-lookup"><span data-stu-id="92d93-111">Assistant</span></span>|<span data-ttu-id="92d93-112">Oddělení</span><span class="sxs-lookup"><span data-stu-id="92d93-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="92d93-113">Když dotazovat uživatel1, uživatel2 tak původní stav databáze.</span><span class="sxs-lookup"><span data-stu-id="92d93-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="92d93-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="92d93-114">Alfreds</span></span>|<span data-ttu-id="92d93-115">Maria</span><span class="sxs-lookup"><span data-stu-id="92d93-115">Maria</span></span>|<span data-ttu-id="92d93-116">Prodej</span><span class="sxs-lookup"><span data-stu-id="92d93-116">Sales</span></span>|  
|<span data-ttu-id="92d93-117">Uživatel1 připravuje k odeslání těchto změn.</span><span class="sxs-lookup"><span data-stu-id="92d93-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="92d93-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="92d93-118">Alfred</span></span>||<span data-ttu-id="92d93-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="92d93-119">Marketing</span></span>|  
|<span data-ttu-id="92d93-120">Uživatel2 už odeslal tyto změny.</span><span class="sxs-lookup"><span data-stu-id="92d93-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="92d93-121">Mary</span><span class="sxs-lookup"><span data-stu-id="92d93-121">Mary</span></span>|<span data-ttu-id="92d93-122">Služba</span><span class="sxs-lookup"><span data-stu-id="92d93-122">Service</span></span>|  
  
 <span data-ttu-id="92d93-123">User1 se rozhodne tento konflikt přepsáním hodnot v databázi pomocí aktuálních hodnot členů klienta.</span><span class="sxs-lookup"><span data-stu-id="92d93-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="92d93-124">Když uživatel User1 konflikt pomocí <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, výsledek v databázi je stejně jako v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="92d93-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="92d93-125">Správce</span><span class="sxs-lookup"><span data-stu-id="92d93-125">Manager</span></span>|<span data-ttu-id="92d93-126">Pomocníka s nastavením</span><span class="sxs-lookup"><span data-stu-id="92d93-126">Assistant</span></span>|<span data-ttu-id="92d93-127">Oddělení</span><span class="sxs-lookup"><span data-stu-id="92d93-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="92d93-128">Nový stav po vyřešení konfliktu.</span><span class="sxs-lookup"><span data-stu-id="92d93-128">New state after conflict resolution.</span></span>|<span data-ttu-id="92d93-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="92d93-129">Alfred</span></span><br /><br /> <span data-ttu-id="92d93-130">(z User1)</span><span class="sxs-lookup"><span data-stu-id="92d93-130">(from User1)</span></span>|<span data-ttu-id="92d93-131">Maria</span><span class="sxs-lookup"><span data-stu-id="92d93-131">Maria</span></span><br /><br /> <span data-ttu-id="92d93-132">(původní)</span><span class="sxs-lookup"><span data-stu-id="92d93-132">(original)</span></span>|<span data-ttu-id="92d93-133">Marketing</span><span class="sxs-lookup"><span data-stu-id="92d93-133">Marketing</span></span><br /><br /> <span data-ttu-id="92d93-134">(z User1)</span><span class="sxs-lookup"><span data-stu-id="92d93-134">(from User1)</span></span>|  
  
 <span data-ttu-id="92d93-135">Následující příklad kódu ukazuje, jak přepsat aktuální hodnoty členů klienta hodnot v databázi.</span><span class="sxs-lookup"><span data-stu-id="92d93-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="92d93-136">(Žádné kontroly nebo vlastního zpracování konfliktů jednotliví členové dojde k.)</span><span class="sxs-lookup"><span data-stu-id="92d93-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="92d93-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92d93-137">See also</span></span>

- [<span data-ttu-id="92d93-138">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="92d93-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
