---
title: 'Postupy: Získávání úložišť pro izolované úložiště'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0968443af28e2d403b08a1af50846e7a1369db49
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751745"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="d6ee2-102">Postupy: Získávání úložišť pro izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="d6ee2-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="d6ee2-103">Izolované úložiště poskytuje virtuální systém souborů v rámci datové přihrádky.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="d6ee2-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje několik metod pro interakci s izolované úložiště.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="d6ee2-105">K vytvoření a načtení úložišť, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> poskytuje tři statické metody:</span><span class="sxs-lookup"><span data-stu-id="d6ee2-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
- <span data-ttu-id="d6ee2-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> vrátí úložiště, které je izolováno podle uživatele a sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
- <span data-ttu-id="d6ee2-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> vrátí úložiště, která je izolovaná podle domény a sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="d6ee2-108">Obě metody načíst úložiště, které patří do kódu, ve kterém jsou volány.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
- <span data-ttu-id="d6ee2-109">Statická metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> vrátí izolované úložiště, které je určeno předáním kombinací parametry oboru.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="d6ee2-110">Následující kód vrátí úložiště, které je izolováno podle uživatele, sestavení a domény.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="d6ee2-111">Můžete použít <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody k určení, že úložiště spolu s cestovní profil uživatele.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="d6ee2-112">Podrobnosti o tom, jak nastavit tuto možnost najdete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="d6ee2-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="d6ee2-113">Izolované úložiště získané v rámci různých sestaveních jsou ve výchozím nastavení různých obchodech.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="d6ee2-114">Úložišti domény nebo jiném sestavení se zpřístupní po předání v legitimaci sestavení nebo domény v parametrech <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="d6ee2-115">To vyžaduje oprávnění pro přístup k izolovanému úložišti podle identity domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="d6ee2-116">Další informace najdete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="d6ee2-117"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, A <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody vrátit <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objektu.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="d6ee2-118">Abyste mohli rozhodnout, jaký typ izolace je nejvhodnější pro vaši situaci, naleznete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="d6ee2-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="d6ee2-119">Až budete mít objekt souboru izolovaného úložiště, můžete použít metody izolovaného úložiště pro čtení, zápis, vytvářet a odstraňovat soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="d6ee2-120">Neexistuje žádný mechanismus, který zabrání předání kódu <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekt na kód, který nemá dostatečný přístup k získání samotného úložiště.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="d6ee2-121">Domény a sestavení identit a oprávnění izolovaného úložiště jsou kontrolovány pouze v případě, že odkaz na <xref:System.IO.IsolatedStorage.IsolatedStorage> objekt získán, obvykle v <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, nebo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="d6ee2-122">Ochrana odkazů na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty zodpovídá, proto kód, který používá tyto odkazy.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6ee2-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6ee2-123">Example</span></span>  
 <span data-ttu-id="d6ee2-124">Následující kód nabízí jednoduchý příklad třídy získání úložiště, které je izolováno podle uživatele a sestavení.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="d6ee2-125">Kód lze změnit pro načtení úložiště, které je izolováno podle uživatele, domény a sestavení tak, že přidáte <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> na argumenty, které <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda předává.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="d6ee2-126">Po spuštění kódu můžete potvrdit, že úložiště bylo vytvořeno zadáním **/list StoreAdm** na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="d6ee2-127">Toto řešení běží [Nástroj izolovaného úložiště (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) a jsou uvedeny všechny aktuální izolované úložiště pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="d6ee2-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="d6ee2-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6ee2-128">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [<span data-ttu-id="d6ee2-129">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="d6ee2-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="d6ee2-130">Typy izolace</span><span class="sxs-lookup"><span data-stu-id="d6ee2-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)
- [<span data-ttu-id="d6ee2-131">Sestavení v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="d6ee2-131">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
