---
title: 'Postupy: Řešení konfliktů sloučením s hodnotami v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 18a7eceeec63d9caadefab8d98942f10d82c99ca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793361"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="99453-102">Postupy: Řešení konfliktů sloučením s hodnotami v databázi</span><span class="sxs-lookup"><span data-stu-id="99453-102">How to: Resolve Conflicts by Merging with Database Values</span></span>
<span data-ttu-id="99453-103">Pro sjednocení rozdílů mezi očekávanými a skutečnými hodnotami databáze předtím, než se pokusíte znovu odeslat změny <xref:System.Data.Linq.RefreshMode.KeepChanges> , můžete použít ke sloučení hodnot databáze s aktuálními hodnotami členů klienta.</span><span class="sxs-lookup"><span data-stu-id="99453-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="99453-104">Další informace najdete v tématu [Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="99453-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99453-105">Ve všech případech se záznam v klientovi poprvé aktualizuje načtením aktualizovaných dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="99453-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="99453-106">Tato akce zajistí, že se další pokus o aktualizaci nebude při stejných kontrolách souběžnosti selhat.</span><span class="sxs-lookup"><span data-stu-id="99453-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99453-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="99453-107">Example</span></span>  
 <span data-ttu-id="99453-108">V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 má mezitím změněné sloupce asistent a oddělení.</span><span class="sxs-lookup"><span data-stu-id="99453-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="99453-109">V následující tabulce je uvedena situace.</span><span class="sxs-lookup"><span data-stu-id="99453-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="99453-110">Správce</span><span class="sxs-lookup"><span data-stu-id="99453-110">Manager</span></span>|<span data-ttu-id="99453-111">Pomocníka</span><span class="sxs-lookup"><span data-stu-id="99453-111">Assistant</span></span>|<span data-ttu-id="99453-112">Oddělení</span><span class="sxs-lookup"><span data-stu-id="99453-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="99453-113">Původní stav databáze při dotazování od uživatele User1 a uživatel2.</span><span class="sxs-lookup"><span data-stu-id="99453-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="99453-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="99453-114">Alfreds</span></span>|<span data-ttu-id="99453-115">Maria</span><span class="sxs-lookup"><span data-stu-id="99453-115">Maria</span></span>|<span data-ttu-id="99453-116">Prodej</span><span class="sxs-lookup"><span data-stu-id="99453-116">Sales</span></span>|  
|<span data-ttu-id="99453-117">Uživatel1 připraví odeslání těchto změn.</span><span class="sxs-lookup"><span data-stu-id="99453-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="99453-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="99453-118">Alfred</span></span>||<span data-ttu-id="99453-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="99453-119">Marketing</span></span>|  
|<span data-ttu-id="99453-120">Uživatel2 již odeslal tyto změny.</span><span class="sxs-lookup"><span data-stu-id="99453-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="99453-121">Marie</span><span class="sxs-lookup"><span data-stu-id="99453-121">Mary</span></span>|<span data-ttu-id="99453-122">Služba</span><span class="sxs-lookup"><span data-stu-id="99453-122">Service</span></span>|  
  
 <span data-ttu-id="99453-123">Uživatel1 se rozhodne tento konflikt vyřešit sloučením hodnot databáze s aktuálními hodnotami členů klienta.</span><span class="sxs-lookup"><span data-stu-id="99453-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="99453-124">Výsledkem bude, že hodnoty databáze budou přepsány pouze v případě, že aktuální sada změn také změnila tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="99453-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="99453-125">Když uživatel1 vyřeší konflikt <xref:System.Data.Linq.RefreshMode.KeepChanges>pomocí, výsledek v databázi je, jak je uvedeno v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="99453-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="99453-126">Správce</span><span class="sxs-lookup"><span data-stu-id="99453-126">Manager</span></span>|<span data-ttu-id="99453-127">Pomocníka</span><span class="sxs-lookup"><span data-stu-id="99453-127">Assistant</span></span>|<span data-ttu-id="99453-128">Oddělení</span><span class="sxs-lookup"><span data-stu-id="99453-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="99453-129">Nový stav po vyřešení konfliktu.</span><span class="sxs-lookup"><span data-stu-id="99453-129">New state after conflict resolution.</span></span>|<span data-ttu-id="99453-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="99453-130">Alfred</span></span><br /><br /> <span data-ttu-id="99453-131">(od uživatele user1)</span><span class="sxs-lookup"><span data-stu-id="99453-131">(from User1)</span></span>|<span data-ttu-id="99453-132">Marie</span><span class="sxs-lookup"><span data-stu-id="99453-132">Mary</span></span><br /><br /> <span data-ttu-id="99453-133">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="99453-133">(from User2)</span></span>|<span data-ttu-id="99453-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="99453-134">Marketing</span></span><br /><br /> <span data-ttu-id="99453-135">(od uživatele user1)</span><span class="sxs-lookup"><span data-stu-id="99453-135">(from User1)</span></span>|  
  
 <span data-ttu-id="99453-136">Následující příklad ukazuje, jak sloučit hodnoty databáze s aktuálními hodnotami členů klienta (Pokud klient nezměnil také tuto hodnotu).</span><span class="sxs-lookup"><span data-stu-id="99453-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="99453-137">Nedochází k žádné kontrole nebo vlastní manipulaci s jednotlivými konflikty členů.</span><span class="sxs-lookup"><span data-stu-id="99453-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="99453-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99453-138">See also</span></span>

- [<span data-ttu-id="99453-139">Postupy: Řešení konfliktů přepsáním hodnot databáze</span><span class="sxs-lookup"><span data-stu-id="99453-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [<span data-ttu-id="99453-140">Postupy: Řešení konfliktů zachováním hodnot databáze</span><span class="sxs-lookup"><span data-stu-id="99453-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)
- [<span data-ttu-id="99453-141">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="99453-141">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
