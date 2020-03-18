---
title: 'Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data stores, quotas
- isolated storage, quotas
- quantity of isolated storage used
- limit on isolated storage used
- stores, quotas
- stores, out of space conditions
- data storage using isolated storage, quotas
- storing data using isolated storage, quotas
- space remaining in isolated storage
- data stores, out of space conditions
- storing data using isolated storage, out of space conditions
- quotas for isolated storage
- isolated storage, out of space conditions
- data storage using isolated storage, out of space conditions
ms.assetid: e35d4535-3732-421e-b1a3-37412e036145
ms.openlocfilehash: 5666019e1a65880221261ef5ad704f82c37263b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708112"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="7c85b-102">Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště</span><span class="sxs-lookup"><span data-stu-id="7c85b-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="7c85b-103">Kód, který používá izolované úložiště, je omezen [kvótou,](../../../docs/standard/io/isolated-storage.md#quotas) která určuje maximální velikost datového oddílu, ve kterém existují soubory a adresáře izolovaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="7c85b-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="7c85b-104">Kvóta je definována zásadami zabezpečení a je konfigurovatelná správci.</span><span class="sxs-lookup"><span data-stu-id="7c85b-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="7c85b-105">Pokud je při pokusu o zápis dat překročena maximální povolená velikost, je vyvolána <xref:System.IO.IsolatedStorage.IsolatedStorageException> výjimka a operace se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="7c85b-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="7c85b-106">To pomáhá zabránit škodlivým útokům odmítnutí služby, které by mohly způsobit, že aplikace odmítne požadavky, protože je vyplněno úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="7c85b-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="7c85b-107">Chcete-li zjistit, zda daný pokus o zápis je <xref:System.IO.IsolatedStorage.IsolatedStorage> pravděpodobné, že selhání <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>z <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>tohoto <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>důvodu, třída poskytuje tři vlastnosti jen pro čtení: , a .</span><span class="sxs-lookup"><span data-stu-id="7c85b-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="7c85b-108">Tyto vlastnosti můžete použít k určení, zda zápis do úložiště způsobí překročení maximální povolené velikosti úložiště.</span><span class="sxs-lookup"><span data-stu-id="7c85b-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="7c85b-109">Mějte na paměti, že izolované úložiště lze přistupovat souběžně; Proto při výpočtu množství zbývající úložiště, úložný prostor může být spotřebována v době, kdy se pokusíte zapsat do úložiště.</span><span class="sxs-lookup"><span data-stu-id="7c85b-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="7c85b-110">Maximální velikost úložiště však můžete použít k určení, zda má být dosaženo horního limitu dostupného úložiště.</span><span class="sxs-lookup"><span data-stu-id="7c85b-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="7c85b-111">Vlastnost <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> závisí na důkazy ze sestavení pracovat správně.</span><span class="sxs-lookup"><span data-stu-id="7c85b-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="7c85b-112">Z tohoto důvodu byste měli načíst tuto vlastnost <xref:System.IO.IsolatedStorage.IsolatedStorageFile> pouze <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>u <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> objektů, které byly vytvořeny pomocí metody , nebo nebo.</span><span class="sxs-lookup"><span data-stu-id="7c85b-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="7c85b-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>objekty, které byly vytvořeny jiným způsobem (například <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> objekty, které byly vráceny z metody) nevrátí přesnou maximální velikost.</span><span class="sxs-lookup"><span data-stu-id="7c85b-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="7c85b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c85b-114">Example</span></span>

<span data-ttu-id="7c85b-115">Následující příklad kódu získá izolované úložiště, vytvoří několik souborů <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> a načte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7c85b-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="7c85b-116">Zbývající místo je hlášeno v bajtů.</span><span class="sxs-lookup"><span data-stu-id="7c85b-116">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="7c85b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c85b-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="7c85b-118">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="7c85b-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
- [<span data-ttu-id="7c85b-119">Postupy: Získávání úložišť pro izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="7c85b-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
