---
title: "Postupy: Získávání úložišť pro izolované úložiště"
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
- cpp
helpviewer_keywords:
- stores, obtaining
- storing data using isolated storage, obtaining stores
- isolated storage, obtaining stores
- data stores, obtaining
- data storage using isolated storage, obtaining stores
ms.assetid: fcb6b178-d526-47c4-b029-e946f880f9db
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb0b877aa0f4cee36bd1f8c1cea624cf9368fbaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="7d8e7-102">Postupy: Získávání úložišť pro izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="7d8e7-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="7d8e7-103">Izolované úložiště zpřístupní virtuálním souborovém systému v rámci datový prostor.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="7d8e7-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje několik metod pro interakci s izolované úložiště.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="7d8e7-105">Vytvoření a načtení úložiště, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> poskytuje tři statické metody:</span><span class="sxs-lookup"><span data-stu-id="7d8e7-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
-   <span data-ttu-id="7d8e7-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>vrátí úložiště, která je izolovaná podle uživatele a sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
-   <span data-ttu-id="7d8e7-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>vrátí úložiště, která je izolovaná podle domény a sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="7d8e7-108">Obě metody načíst úložiště, které patří do kódu, ze které se nazývají.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
-   <span data-ttu-id="7d8e7-109">Statickou metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> vrátí izolované úložiště, které je určeno předáním kombinace parametrů rozsahu.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="7d8e7-110">Následující kód vrátí úložiště, která je izolovaná uživatelem, sestavení a domény.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="7d8e7-111">Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda k určení, že úložiště spolu s cestovní profil uživatele.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="7d8e7-112">Podrobnosti o tom, jak nastavit tuto možnost najdete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="7d8e7-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="7d8e7-113">Izolované úložiště získané v rámci různých sestavení jsou ve výchozím nastavení různých úložišť.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="7d8e7-114">V sestavení nebo domény důkaz v parametrech získáváte přístup úložišti domény nebo jiném sestavení předáním <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="7d8e7-115">To vyžaduje oprávnění pro přístup k izolovanému úložišti podle identity domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="7d8e7-116">Další informace najdete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="7d8e7-117"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, A <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody vrací <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objektu.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="7d8e7-118">Pomoc při rozhodování, který typ izolace je nejvhodnější pro vaši situaci, najdete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="7d8e7-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="7d8e7-119">Až budete mít objekt souboru izolovaného úložiště, můžete použít metody izolovaného úložiště pro čtení, zápisu, vytvořte a odstraňování souborů a adresářů.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="7d8e7-120">Neexistuje žádný mechanismus, který zabrání předávání kódu <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekt, který má kód, který nemá dostatečný přístup k získání samotného úložiště.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="7d8e7-121">Identity domény a sestavení a oprávnění izolovaného úložiště se kontroluje jenom v případě, že odkaz na <xref:System.IO.IsolatedStorage.IsolatedStorage> objekt získán, obvykle v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, nebo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="7d8e7-122">Ochrana odkazů na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty zodpovídá, tedy kód, který používá tyto odkazy.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d8e7-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d8e7-123">Example</span></span>  
 <span data-ttu-id="7d8e7-124">Následující kód poskytuje jednoduchý příklad třídy pro získání úložiště, která je izolovaná podle uživatele a sestavení.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="7d8e7-125">Kód můžete změnit tak, aby načíst úložiště, která je izolovaná uživatele, domény a sestavení přidáním <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> na argumenty, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> předává metoda.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="7d8e7-126">Po spuštění kódu můžete potvrdit, že úložiště bylo vytvořeno zadáním **StoreAdm/list** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="7d8e7-127">Toto spouští [Nástroj izolovaného úložiště (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) a obsahuje všechna aktuální izolované úložiště pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="7d8e7-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="7d8e7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d8e7-128">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [<span data-ttu-id="7d8e7-129">Izolovaná úložiště</span><span class="sxs-lookup"><span data-stu-id="7d8e7-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="7d8e7-130">Typy izolace</span><span class="sxs-lookup"><span data-stu-id="7d8e7-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)  
 [<span data-ttu-id="7d8e7-131">Sestavení v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="7d8e7-131">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
