---
title: 'Postupy: Řešení konfliktů zachováním hodnot v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: 828f0a21ca1ea4155f31dfbc87b01dc8c4b81e40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928738"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="cd847-102">Postupy: Řešení konfliktů zachováním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="cd847-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="cd847-103">Pro sjednocení rozdílů mezi očekávanými a skutečnými hodnotami databáze předtím, než se pokusíte znovu odeslat změny <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> , můžete použít k zachování hodnot nalezených v databázi.</span><span class="sxs-lookup"><span data-stu-id="cd847-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="cd847-104">Aktuální hodnoty v objektovém modelu jsou poté přepsány.</span><span class="sxs-lookup"><span data-stu-id="cd847-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="cd847-105">Další informace najdete v tématu [Optimistická souběžnost: Přehled](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cd847-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd847-106">Ve všech případech se záznam v klientovi poprvé aktualizuje načtením aktualizovaných dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="cd847-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="cd847-107">Tato akce zajistí, že se další pokus o aktualizaci nebude při stejných kontrolách souběžnosti selhat.</span><span class="sxs-lookup"><span data-stu-id="cd847-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd847-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd847-108">Example</span></span>  
 <span data-ttu-id="cd847-109">V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 má mezitím změněné sloupce asistent a oddělení.</span><span class="sxs-lookup"><span data-stu-id="cd847-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="cd847-110">V následující tabulce je uvedena situace.</span><span class="sxs-lookup"><span data-stu-id="cd847-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="cd847-111">Správce</span><span class="sxs-lookup"><span data-stu-id="cd847-111">Manager</span></span>|<span data-ttu-id="cd847-112">Pomocníka</span><span class="sxs-lookup"><span data-stu-id="cd847-112">Assistant</span></span>|<span data-ttu-id="cd847-113">Oddělení</span><span class="sxs-lookup"><span data-stu-id="cd847-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="cd847-114">Původní stav databáze při dotazování od uživatele User1 a uživatel2.</span><span class="sxs-lookup"><span data-stu-id="cd847-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="cd847-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="cd847-115">Alfreds</span></span>|<span data-ttu-id="cd847-116">Maria</span><span class="sxs-lookup"><span data-stu-id="cd847-116">Maria</span></span>|<span data-ttu-id="cd847-117">Prodej</span><span class="sxs-lookup"><span data-stu-id="cd847-117">Sales</span></span>|  
|<span data-ttu-id="cd847-118">Uživatel1 připraví odeslání těchto změn.</span><span class="sxs-lookup"><span data-stu-id="cd847-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="cd847-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="cd847-119">Alfred</span></span>||<span data-ttu-id="cd847-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="cd847-120">Marketing</span></span>|  
|<span data-ttu-id="cd847-121">Uživatel2 již odeslal tyto změny.</span><span class="sxs-lookup"><span data-stu-id="cd847-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="cd847-122">Marie</span><span class="sxs-lookup"><span data-stu-id="cd847-122">Mary</span></span>|<span data-ttu-id="cd847-123">Služba</span><span class="sxs-lookup"><span data-stu-id="cd847-123">Service</span></span>|  
  
 <span data-ttu-id="cd847-124">Uživatel1 se rozhodne tento konflikt vyřešit tak, že novější hodnoty databáze přepíší aktuální hodnoty v objektovém modelu.</span><span class="sxs-lookup"><span data-stu-id="cd847-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="cd847-125">Když uživatel1 vyřeší konflikt <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>pomocí, výsledek v databázi je následující v tabulce:</span><span class="sxs-lookup"><span data-stu-id="cd847-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="cd847-126">Správce</span><span class="sxs-lookup"><span data-stu-id="cd847-126">Manager</span></span>|<span data-ttu-id="cd847-127">Pomocníka</span><span class="sxs-lookup"><span data-stu-id="cd847-127">Assistant</span></span>|<span data-ttu-id="cd847-128">Oddělení</span><span class="sxs-lookup"><span data-stu-id="cd847-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="cd847-129">Nový stav po vyřešení konfliktu.</span><span class="sxs-lookup"><span data-stu-id="cd847-129">New state after conflict resolution.</span></span>|<span data-ttu-id="cd847-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="cd847-130">Alfreds</span></span><br /><br /> <span data-ttu-id="cd847-131">původně</span><span class="sxs-lookup"><span data-stu-id="cd847-131">(original)</span></span>|<span data-ttu-id="cd847-132">Marie</span><span class="sxs-lookup"><span data-stu-id="cd847-132">Mary</span></span><br /><br /> <span data-ttu-id="cd847-133">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="cd847-133">(from User2)</span></span>|<span data-ttu-id="cd847-134">Služba</span><span class="sxs-lookup"><span data-stu-id="cd847-134">Service</span></span><br /><br /> <span data-ttu-id="cd847-135">(z uživatel2)</span><span class="sxs-lookup"><span data-stu-id="cd847-135">(from User2)</span></span>|  
  
 <span data-ttu-id="cd847-136">Následující příklad kódu ukazuje, jak přepsat aktuální hodnoty v objektovém modelu s hodnotami databáze.</span><span class="sxs-lookup"><span data-stu-id="cd847-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="cd847-137">(K žádné kontrole nebo vlastní manipulaci s jednotlivými členy nedochází.)</span><span class="sxs-lookup"><span data-stu-id="cd847-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cd847-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd847-138">See also</span></span>

- [<span data-ttu-id="cd847-139">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="cd847-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
