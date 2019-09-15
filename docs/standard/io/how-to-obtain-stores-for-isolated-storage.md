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
ms.openlocfilehash: d6fbc78c379951e05869a433875d057c49d44594
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969263"
---
# <a name="how-to-obtain-stores-for-isolated-storage"></a><span data-ttu-id="a8110-102">Postupy: Získávání úložišť pro izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="a8110-102">How to: Obtain Stores for Isolated Storage</span></span>
<span data-ttu-id="a8110-103">Izolované úložiště zpřístupňuje virtuální systém souborů v datovém oddílu.</span><span class="sxs-lookup"><span data-stu-id="a8110-103">An isolated store exposes a virtual file system within a data compartment.</span></span> <span data-ttu-id="a8110-104"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> Třída poskytuje řadu metod pro interakci s izolovaným úložištěm.</span><span class="sxs-lookup"><span data-stu-id="a8110-104">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class supplies a number of methods for interacting with an isolated store.</span></span> <span data-ttu-id="a8110-105">Chcete-li vytvořit a načíst <xref:System.IO.IsolatedStorage.IsolatedStorageFile> úložiště, nabízí tři statické metody:</span><span class="sxs-lookup"><span data-stu-id="a8110-105">To create and retrieve stores, <xref:System.IO.IsolatedStorage.IsolatedStorageFile> provides three static methods:</span></span>  
  
- <span data-ttu-id="a8110-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>vrátí úložiště, které je izolované uživatelem a sestavením.</span><span class="sxs-lookup"><span data-stu-id="a8110-106"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> returns storage that is isolated by user and assembly.</span></span>  
  
- <span data-ttu-id="a8110-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>vrátí úložiště, které je izolované podle domény a sestavení.</span><span class="sxs-lookup"><span data-stu-id="a8110-107"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> returns storage that is isolated by domain and assembly.</span></span>  
  
     <span data-ttu-id="a8110-108">Obě metody načtou úložiště, které patří do kódu, ze kterého jsou volány.</span><span class="sxs-lookup"><span data-stu-id="a8110-108">Both methods retrieve a store that belongs to the code from which they are called.</span></span>  
  
- <span data-ttu-id="a8110-109">Statická metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> vrací izolované úložiště, které je určeno předáním kombinace parametrů oboru.</span><span class="sxs-lookup"><span data-stu-id="a8110-109">The static method <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> returns an isolated store that is specified by passing in a combination of scope parameters.</span></span>  
  
 <span data-ttu-id="a8110-110">Následující kód vrátí úložiště, které je izolované uživatelem, sestavením a doménou.</span><span class="sxs-lookup"><span data-stu-id="a8110-110">The following code returns a store that is isolated by user, assembly, and domain.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#6)]
 [!code-csharp[Conceptual.IsolatedStorage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#6)]
 [!code-vb[Conceptual.IsolatedStorage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#6)]  
  
 <span data-ttu-id="a8110-111">Tuto <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metodu můžete použít k určení, že by úložiště mělo roaming s cestovním profilem uživatele.</span><span class="sxs-lookup"><span data-stu-id="a8110-111">You can use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method to specify that a store should roam with a roaming user profile.</span></span> <span data-ttu-id="a8110-112">Podrobnosti o tom, jak tento postup nastavit, najdete v tématu [typy izolace](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="a8110-112">For details on how to set this up, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span>  
  
 <span data-ttu-id="a8110-113">Izolované obchody získané v různých sestaveních jsou ve výchozím nastavení různými obchody.</span><span class="sxs-lookup"><span data-stu-id="a8110-113">Isolated stores obtained from within different assemblies are, by default, different stores.</span></span> <span data-ttu-id="a8110-114">Můžete získat přístup k úložišti jiného sestavení nebo domény předáním do sestavení nebo legitimace domény v parametrech <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a8110-114">You can access the store of a different assembly or domain by passing in the assembly or domain evidence in the parameters of the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="a8110-115">To vyžaduje oprávnění pro přístup k izolovanému úložišti pomocí identity aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="a8110-115">This requires permission to access isolated storage by application domain identity.</span></span> <span data-ttu-id="a8110-116">Další informace naleznete v tématu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="a8110-116">For more information, see the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method overloads.</span></span>  
  
 <span data-ttu-id="a8110-117">Metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>a vrací<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> objekt<xref:System.IO.IsolatedStorage.IsolatedStorageFile> .</span><span class="sxs-lookup"><span data-stu-id="a8110-117">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> methods return an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object.</span></span> <span data-ttu-id="a8110-118">K tomu, abyste se mohli rozhodnout, který typ izolace je pro vaši situaci nejvhodnější, přečtěte si téma [typy izolace](../../../docs/standard/io/types-of-isolation.md).</span><span class="sxs-lookup"><span data-stu-id="a8110-118">To help you decide which isolation type is most appropriate for your situation, see [Types of Isolation](../../../docs/standard/io/types-of-isolation.md).</span></span> <span data-ttu-id="a8110-119">Pokud máte izolovaný objekt úložiště, můžete použít metody izolovaného úložiště ke čtení, zápisu, vytváření a odstraňování souborů a adresářů.</span><span class="sxs-lookup"><span data-stu-id="a8110-119">When you have an isolated storage file object, you can use the isolated storage methods to read, write, create, and delete files and directories.</span></span>  
  
 <span data-ttu-id="a8110-120">Neexistuje žádný mechanismus, který brání kódu v předání <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objektu do kódu, který nemá dostatečný přístup k získání samotného úložiště.</span><span class="sxs-lookup"><span data-stu-id="a8110-120">There is no mechanism that prevents code from passing an <xref:System.IO.IsolatedStorage.IsolatedStorageFile> object to code that does not have sufficient access to get the store itself.</span></span> <span data-ttu-id="a8110-121">Identity domény a sestavení a oprávnění izolovaného úložiště jsou kontrolovány pouze <xref:System.IO.IsolatedStorage.IsolatedStorage> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>v případě, že je získán odkaz na objekt, obvykle v metodě <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> , <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>nebo.</span><span class="sxs-lookup"><span data-stu-id="a8110-121">Domain and assembly identities and isolated storage permissions are checked only when a reference to an <xref:System.IO.IsolatedStorage.IsolatedStorage> object is obtained, typically in the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="a8110-122">Ochrana odkazů na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty je proto odpovědností kódu, který používá tyto odkazy.</span><span class="sxs-lookup"><span data-stu-id="a8110-122">Protecting references to <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects is, therefore, the responsibility of the code that uses these references.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8110-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8110-123">Example</span></span>  
 <span data-ttu-id="a8110-124">Následující kód poskytuje jednoduchý příklad třídy, která získá úložiště izolované uživatelem a sestavením.</span><span class="sxs-lookup"><span data-stu-id="a8110-124">The following code provides a simple example of a class obtaining a store that is isolated by user and assembly.</span></span> <span data-ttu-id="a8110-125">Kód může být změněn tak, aby načetl úložiště izolované uživatelem, doménou a sestavením přidáním <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> k argumentům <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> , které Metoda projde.</span><span class="sxs-lookup"><span data-stu-id="a8110-125">The code can be changed to retrieve a store that is isolated by user, domain, and assembly by adding <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Domain?displayProperty=nameWithType> to the arguments that the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method passes.</span></span>  
  
 <span data-ttu-id="a8110-126">Po spuštění kódu se můžete ujistit, že se vytvořilo úložiště, a to zadáním **Storeadm/list** do příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="a8110-126">After you run the code, you can confirm that a store was created by typing **StoreAdm /LIST** at the command line.</span></span> <span data-ttu-id="a8110-127">Spustí se [Nástroj izolovaného úložiště (Storeadm. exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) a vypíše všechna aktuální izolovaná úložiště pro daného uživatele.</span><span class="sxs-lookup"><span data-stu-id="a8110-127">This runs the [Isolated Storage tool (Storeadm.exe)](../../../docs/framework/tools/storeadm-exe-isolated-storage-tool.md) and lists all the current isolated stores for the user.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source6.cpp#7)]
 [!code-csharp[Conceptual.IsolatedStorage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source6.cs#7)]
 [!code-vb[Conceptual.IsolatedStorage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a8110-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8110-128">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [<span data-ttu-id="a8110-129">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="a8110-129">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="a8110-130">Typy izolace</span><span class="sxs-lookup"><span data-stu-id="a8110-130">Types of Isolation</span></span>](../../../docs/standard/io/types-of-isolation.md)
- [<span data-ttu-id="a8110-131">Sestavení v .NET</span><span class="sxs-lookup"><span data-stu-id="a8110-131">Assemblies in .NET</span></span>](../assembly/index.md)
