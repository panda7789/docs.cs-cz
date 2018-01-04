---
title: "Postupy: Přidávání a odebírání položek v ConcurrentDictionary"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: thread-safe collections, concurrent dictionary
ms.assetid: 81b64b95-13f7-4532-9249-ab532f629598
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4ef7c8050b26cffeed03cc394193116f8f6797a9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-add-and-remove-items-from-a-concurrentdictionary"></a><span data-ttu-id="014ea-102">Postupy: Přidávání a odebírání položek v ConcurrentDictionary</span><span class="sxs-lookup"><span data-stu-id="014ea-102">How to: Add and Remove Items from a ConcurrentDictionary</span></span>
<span data-ttu-id="014ea-103">Tento příklad ukazuje, jak přidat, získat, aktualizovat a odebrání položek z <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="014ea-103">This example shows how to add, retrieve, update, and remove items from a <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="014ea-104">Tato třída kolekce je implementace bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="014ea-104">This collection class is a thread-safe implementation.</span></span> <span data-ttu-id="014ea-105">Doporučujeme vám, že použít kdykoli více vláken může se pokusit o přístup k prvkům.</span><span class="sxs-lookup"><span data-stu-id="014ea-105">We recommend that you use it whenever multiple threads might be attempting to access the elements concurrently.</span></span>  
  
 <span data-ttu-id="014ea-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602>poskytuje několik vhodných metod, které není nutné, aby kód nejprve zkontrolujte, jestli existuje klíč, předtím než se pokusí přidat nebo odebrat data.</span><span class="sxs-lookup"><span data-stu-id="014ea-106"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> provides several convenience methods that make it unnecessary for code to first check whether a key exists before it attempts to add or remove data.</span></span> <span data-ttu-id="014ea-107">Následující tabulka uvádí tyto metody pohodlí a popisuje jejich použití.</span><span class="sxs-lookup"><span data-stu-id="014ea-107">The following table lists these convenience methods and describes when to use them.</span></span>  
  
|<span data-ttu-id="014ea-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="014ea-108">Method</span></span>|<span data-ttu-id="014ea-109">Použijte, když...</span><span class="sxs-lookup"><span data-stu-id="014ea-109">Use when…</span></span>|  
|------------|---------------|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>|<span data-ttu-id="014ea-110">Chcete přidat novou hodnotu pro zadaný klíč, a pokud klíč již existuje, chcete nahradit jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="014ea-110">You want to add a new value for a specified key and, if the key already exists, you want to replace its value.</span></span>|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>|<span data-ttu-id="014ea-111">Můžete obnovit existující hodnotu pro zadaný klíč, a pokud klíč neexistuje, můžete chtít zadat dvojice klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="014ea-111">You want to retrieve the existing value for a specified key and, if the key does not exist, you want to specify a key/value pair.</span></span>|  
|<span data-ttu-id="014ea-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span><span class="sxs-lookup"><span data-stu-id="014ea-112"><xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryAdd%2A>, <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryGetValue%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryUpdate%2A> , <xref:System.Collections.Concurrent.ConcurrentDictionary%602.TryRemove%2A></span></span>|<span data-ttu-id="014ea-113">Chcete přidat, získat, aktualizovat nebo odebrat dvojici klíč/hodnota, a pokud klíč již existuje nebo pokus selže z jiného důvodu, kterou chcete provést některé alternativní akce.</span><span class="sxs-lookup"><span data-stu-id="014ea-113">You want to add, get, update, or remove a key/value pair, and, if the key already exists or the attempt fails for any other reason, you want to take some alternative action.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="014ea-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="014ea-114">Example</span></span>  
 <span data-ttu-id="014ea-115">Následující příklad používá dva <xref:System.Threading.Tasks.Task> instance k přidání některých prvků <xref:System.Collections.Concurrent.ConcurrentDictionary%602> současně a pak uloží veškerý obsah, aby zobrazil, že byly úspěšně přidány elementy.</span><span class="sxs-lookup"><span data-stu-id="014ea-115">The following example uses two <xref:System.Threading.Tasks.Task> instances to add some elements to a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> concurrently, and then outputs all of the contents to show that the elements were added successfully.</span></span> <span data-ttu-id="014ea-116">Příklad také ukazuje způsob použití <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> metody pro přidání, aktualizace a načítat položky z kolekce.</span><span class="sxs-lookup"><span data-stu-id="014ea-116">The example also shows how to use the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>, <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>, and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to add, update, and retrieve  items from the collection.</span></span>  
  
 [!code-csharp[CDS#16](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds_dictionaryhowto.cs#16)]
 [!code-vb[CDS#16](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/cds_concdict.vb#16)]  
  
 <span data-ttu-id="014ea-117"><xref:System.Collections.Concurrent.ConcurrentDictionary%602>je určená pro scénáře s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="014ea-117"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> is designed for multithreaded scenarios.</span></span> <span data-ttu-id="014ea-118">Není nutné používat zámky v kódu k přidání nebo odebrání položky z kolekce.</span><span class="sxs-lookup"><span data-stu-id="014ea-118">You do not have to use locks in your code to add or remove items from the collection.</span></span> <span data-ttu-id="014ea-119">Vždycky je však možné jedno vlákno k načtení hodnoty a jiné vlákno okamžitě aktualizovat kolekci tím, že se stejným klíčem novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="014ea-119">However, it is always possible for one thread to retrieve a value, and another thread to immediately update the collection by giving the same key a new value.</span></span>  
  
 <span data-ttu-id="014ea-120">Také i když všechny metody <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jsou bezpečné pro vlákna, ne všechny metody jsou atomic, konkrétně <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.</span><span class="sxs-lookup"><span data-stu-id="014ea-120">Also, although all methods of <xref:System.Collections.Concurrent.ConcurrentDictionary%602> are thread-safe, not all methods are atomic, specifically <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A>.</span></span> <span data-ttu-id="014ea-121">Uživatel delegáta, který je předán tyto metody je vyvolána mimo interní zámku slovník.</span><span class="sxs-lookup"><span data-stu-id="014ea-121">The user delegate that is passed to these methods is invoked outside of the dictionary's internal lock.</span></span> <span data-ttu-id="014ea-122">(To se provádí zabránit blokování všechna vlákna neznámý kód). Proto je možné pro toto pořadí k událostem:</span><span class="sxs-lookup"><span data-stu-id="014ea-122">(This is done to prevent unknown code from blocking all threads.) Therefore it is possible for this sequence of events to occur:</span></span>  
  
 <span data-ttu-id="014ea-123">1\) threadA volání <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, vyhledá žádná položka a vytvoří novou položku do přidat vyvoláním valueFactory delegáta.</span><span class="sxs-lookup"><span data-stu-id="014ea-123">1\) threadA calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A>, finds no item and creates a new item to Add by invoking the valueFactory delegate.</span></span>  
  
 <span data-ttu-id="014ea-124">2\) threadB volání <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> souběžně, je vyvolána jeho valueFactory delegáta a zpráva dorazí na interní zámek před threadA a proto jeho nový pár klíč hodnota se přidá do slovníku.</span><span class="sxs-lookup"><span data-stu-id="014ea-124">2\) threadB calls <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> concurrently, its valueFactory delegate is invoked and it arrives at the internal lock before threadA, and so its new key-value pair is added to the dictionary.</span></span>  
  
 <span data-ttu-id="014ea-125">3\) dokončí delegáta threadA na uživatele a vlákno dorazí na zámek, ale nyní uvidí, že položka již existuje</span><span class="sxs-lookup"><span data-stu-id="014ea-125">3\) threadA's user delegate completes, and the thread arrives at the lock, but now sees that the item exists already</span></span>  
  
 <span data-ttu-id="014ea-126">4\) threadA provede "Get" a vrátí data, která byla dříve přidal threadB.</span><span class="sxs-lookup"><span data-stu-id="014ea-126">4\) threadA performs a "Get", and returns the data that was previously added by threadB.</span></span>  
  
 <span data-ttu-id="014ea-127">Proto není zaručeno, že data, která vrátí <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> je stejná data, která byla vytvořená valueFactory vlákna.</span><span class="sxs-lookup"><span data-stu-id="014ea-127">Therefore, it is not guaranteed that the data that is returned by <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> is the same data that was created by the thread's valueFactory.</span></span> <span data-ttu-id="014ea-128">Podobně jako posloupnost událostí, může dojít, když <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> je volána.</span><span class="sxs-lookup"><span data-stu-id="014ea-128">A similar sequence of events can occur when <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> is called.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014ea-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="014ea-129">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="014ea-130">Kolekce se zabezpečenými vlákny</span><span class="sxs-lookup"><span data-stu-id="014ea-130">Thread-Safe Collections</span></span>](../../../../docs/standard/collections/thread-safe/index.md)
