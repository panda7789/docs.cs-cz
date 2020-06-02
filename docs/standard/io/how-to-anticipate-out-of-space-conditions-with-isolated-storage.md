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
ms.openlocfilehash: bdc2cee343e9d9be44230e84ff45d6fa54901f48
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288586"
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="58a19-102">Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště</span><span class="sxs-lookup"><span data-stu-id="58a19-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>

<span data-ttu-id="58a19-103">Kód, který používá izolované úložiště, je omezený [kvótou](isolated-storage.md#quotas) , která určuje maximální velikost datového oddílu, ve kterém existují izolované soubory úložiště a adresáře.</span><span class="sxs-lookup"><span data-stu-id="58a19-103">Code that uses isolated storage is constrained by a [quota](isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="58a19-104">Kvóta je definována zásadami zabezpečení a správci je můžou konfigurovat.</span><span class="sxs-lookup"><span data-stu-id="58a19-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="58a19-105">Pokud při pokusu o zápis dat dojde k překročení maximální povolené velikosti, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka a operace se nezdařila.</span><span class="sxs-lookup"><span data-stu-id="58a19-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="58a19-106">To pomáhá zabránit škodlivým útokům při odepření služby, které by mohly způsobit zamítnutí požadavků, protože úložiště dat je vyplněno.</span><span class="sxs-lookup"><span data-stu-id="58a19-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>

<span data-ttu-id="58a19-107">Aby bylo možné určit, zda se daný pokus o zápis pravděpodobně z tohoto důvodu nezdaří, <xref:System.IO.IsolatedStorage.IsolatedStorage> Třída poskytuje tři vlastnosti jen pro čtení: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> , <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A> a <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> .</span><span class="sxs-lookup"><span data-stu-id="58a19-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="58a19-108">Tyto vlastnosti můžete použít k určení, jestli zápis do úložiště způsobí překročení maximální povolené velikosti úložiště.</span><span class="sxs-lookup"><span data-stu-id="58a19-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="58a19-109">Pamatujte na to, že izolované úložiště je možné používat souběžně; Proto když počítáte množství zbývajících úložišť, může být prostor úložiště spotřebovaný při pokusu o zápis do úložiště.</span><span class="sxs-lookup"><span data-stu-id="58a19-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="58a19-110">Můžete ale použít maximální velikost úložiště, která vám pomůže určit, jestli se má dosáhnout horní meze dostupného úložiště.</span><span class="sxs-lookup"><span data-stu-id="58a19-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>

<span data-ttu-id="58a19-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>Vlastnost závisí na správném legitimaci sestavení, aby fungovala správně.</span><span class="sxs-lookup"><span data-stu-id="58a19-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="58a19-112">Z tohoto důvodu byste měli načíst tuto vlastnost pouze pro <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty, které byly vytvořeny pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A> metody, nebo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> .</span><span class="sxs-lookup"><span data-stu-id="58a19-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="58a19-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>objekty, které byly vytvořeny jakýmkoli jiným způsobem (například objekty, které byly vráceny z <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metody), nevrátí přesnou maximální velikost.</span><span class="sxs-lookup"><span data-stu-id="58a19-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>

## <a name="example"></a><span data-ttu-id="58a19-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="58a19-114">Example</span></span>

<span data-ttu-id="58a19-115">Následující příklad kódu získá izolovaný obchod, vytvoří několik souborů a načte <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="58a19-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="58a19-116">Zbývající místo je hlášeno v bajtech.</span><span class="sxs-lookup"><span data-stu-id="58a19-116">The remaining space is reported in bytes.</span></span>

[!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
[!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
[!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]

## <a name="see-also"></a><span data-ttu-id="58a19-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="58a19-117">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="58a19-118">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="58a19-118">Isolated Storage</span></span>](isolated-storage.md)
- [<span data-ttu-id="58a19-119">Postupy: Získávání úložišť pro izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="58a19-119">How to: Obtain Stores for Isolated Storage</span></span>](how-to-obtain-stores-for-isolated-storage.md)
