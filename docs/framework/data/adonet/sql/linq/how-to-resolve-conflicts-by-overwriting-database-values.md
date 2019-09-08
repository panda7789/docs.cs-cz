---
title: 'Postupy: Řešení konfliktů přepsáním hodnot v databázi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 1da2abcbbb3b87d44aa99016112d9ef2674912c6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781715"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="978fd-102">Postupy: Řešení konfliktů přepsáním hodnot v databázi</span><span class="sxs-lookup"><span data-stu-id="978fd-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="978fd-103">Chcete-li sjednotit rozdíly mezi očekávanými a skutečnými hodnotami databáze před tím, než se pokusíte znovu <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> odeslat změny, můžete použít k přepsání hodnot databáze.</span><span class="sxs-lookup"><span data-stu-id="978fd-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="978fd-104">Další informace najdete v tématu [Optimistická souběžnost: Přehled](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="978fd-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="978fd-105">Ve všech případech se záznam v klientovi poprvé aktualizuje načtením aktualizovaných dat z databáze.</span><span class="sxs-lookup"><span data-stu-id="978fd-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="978fd-106">Tato akce zajistí, že se další pokus o aktualizaci nebude při stejných kontrolách souběžnosti selhat.</span><span class="sxs-lookup"><span data-stu-id="978fd-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="978fd-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="978fd-107">Example</span></span>  
 <span data-ttu-id="978fd-108">V tomto scénáři <xref:System.Data.Linq.ChangeConflictException> je vyvolána výjimka, když se uživatel1 pokusí odeslat změny, protože uživatel2 má mezitím změněné sloupce asistent a oddělení.</span><span class="sxs-lookup"><span data-stu-id="978fd-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="978fd-109">V následující tabulce je uvedena situace.</span><span class="sxs-lookup"><span data-stu-id="978fd-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="978fd-110">Správce</span><span class="sxs-lookup"><span data-stu-id="978fd-110">Manager</span></span>|<span data-ttu-id="978fd-111">Pomocníka</span><span class="sxs-lookup"><span data-stu-id="978fd-111">Assistant</span></span>|<span data-ttu-id="978fd-112">Oddělení</span><span class="sxs-lookup"><span data-stu-id="978fd-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="978fd-113">Původní stav databáze při dotazování od uživatele User1 a uživatel2.</span><span class="sxs-lookup"><span data-stu-id="978fd-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="978fd-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="978fd-114">Alfreds</span></span>|<span data-ttu-id="978fd-115">Maria</span><span class="sxs-lookup"><span data-stu-id="978fd-115">Maria</span></span>|<span data-ttu-id="978fd-116">Prodej</span><span class="sxs-lookup"><span data-stu-id="978fd-116">Sales</span></span>|  
|<span data-ttu-id="978fd-117">Uživatel1 připraví odeslání těchto změn.</span><span class="sxs-lookup"><span data-stu-id="978fd-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="978fd-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="978fd-118">Alfred</span></span>||<span data-ttu-id="978fd-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="978fd-119">Marketing</span></span>|  
|<span data-ttu-id="978fd-120">Uživatel2 již odeslal tyto změny.</span><span class="sxs-lookup"><span data-stu-id="978fd-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="978fd-121">Marie</span><span class="sxs-lookup"><span data-stu-id="978fd-121">Mary</span></span>|<span data-ttu-id="978fd-122">Služba</span><span class="sxs-lookup"><span data-stu-id="978fd-122">Service</span></span>|  
  
 <span data-ttu-id="978fd-123">Uživatel1 se rozhodne tento konflikt vyřešit přepsáním hodnot databáze s aktuálními hodnotami členů klienta.</span><span class="sxs-lookup"><span data-stu-id="978fd-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="978fd-124">Když uživatel1 vyřeší konflikt <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>pomocí, je výsledek v databázi jako v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="978fd-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="978fd-125">Správce</span><span class="sxs-lookup"><span data-stu-id="978fd-125">Manager</span></span>|<span data-ttu-id="978fd-126">Pomocníka</span><span class="sxs-lookup"><span data-stu-id="978fd-126">Assistant</span></span>|<span data-ttu-id="978fd-127">Oddělení</span><span class="sxs-lookup"><span data-stu-id="978fd-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="978fd-128">Nový stav po vyřešení konfliktu.</span><span class="sxs-lookup"><span data-stu-id="978fd-128">New state after conflict resolution.</span></span>|<span data-ttu-id="978fd-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="978fd-129">Alfred</span></span><br /><br /> <span data-ttu-id="978fd-130">(od uživatele user1)</span><span class="sxs-lookup"><span data-stu-id="978fd-130">(from User1)</span></span>|<span data-ttu-id="978fd-131">Maria</span><span class="sxs-lookup"><span data-stu-id="978fd-131">Maria</span></span><br /><br /> <span data-ttu-id="978fd-132">původně</span><span class="sxs-lookup"><span data-stu-id="978fd-132">(original)</span></span>|<span data-ttu-id="978fd-133">Marketing</span><span class="sxs-lookup"><span data-stu-id="978fd-133">Marketing</span></span><br /><br /> <span data-ttu-id="978fd-134">(od uživatele user1)</span><span class="sxs-lookup"><span data-stu-id="978fd-134">(from User1)</span></span>|  
  
 <span data-ttu-id="978fd-135">Následující příklad kódu ukazuje, jak přepsat hodnoty databáze aktuálními hodnotami členů klienta.</span><span class="sxs-lookup"><span data-stu-id="978fd-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="978fd-136">(K žádné kontrole nebo vlastní manipulaci s jednotlivými členy nedochází.)</span><span class="sxs-lookup"><span data-stu-id="978fd-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="978fd-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="978fd-137">See also</span></span>

- [<span data-ttu-id="978fd-138">Postupy: Správa konfliktů změn</span><span class="sxs-lookup"><span data-stu-id="978fd-138">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
