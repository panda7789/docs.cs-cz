---
title: "Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště"
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
- data stores, quotas
- isolated storage, quotas
- quanitity of isolated storage used
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
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e04b4b85b9a14e842c94226017fcd903ad1cbb40
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-anticipate-out-of-space-conditions-with-isolated-storage"></a><span data-ttu-id="4902d-102">Postupy: Příprava na vyčerpání volného prostoru pomocí izolovaného úložiště</span><span class="sxs-lookup"><span data-stu-id="4902d-102">How to: Anticipate Out-of-Space Conditions with Isolated Storage</span></span>
<span data-ttu-id="4902d-103">Kód, který používá izolované úložiště je omezen [kvóty](../../../docs/standard/io/isolated-storage.md#quotas) , určuje maximální velikost datového oddílu, ve kterém izolované úložiště souborů a adresářů neexistuje.</span><span class="sxs-lookup"><span data-stu-id="4902d-103">Code that uses isolated storage is constrained by a [quota](../../../docs/standard/io/isolated-storage.md#quotas) that specifies the maximum size for the data compartment in which isolated storage files and directories exist.</span></span> <span data-ttu-id="4902d-104">Kvóta je definován pomocí zásad zabezpečení a konfigurovat správci.</span><span class="sxs-lookup"><span data-stu-id="4902d-104">The quota is defined by security policy and is configurable by administrators.</span></span> <span data-ttu-id="4902d-105">Pokud maximální povolená velikost je překročena při pokusu o zápis dat, <xref:System.IO.IsolatedStorage.IsolatedStorageException> je vyvolána výjimka, a operace se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="4902d-105">If the maximum allowed size is exceeded when you try to write data, an <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception is thrown and the operation fails.</span></span> <span data-ttu-id="4902d-106">To pomáhá zabránit nebezpečné útoky odmítnutí služby, které by mohly způsobit aplikace odmítala požadavků z důvodu zaplnění datového úložiště.</span><span class="sxs-lookup"><span data-stu-id="4902d-106">This helps prevent malicious denial-of-service attacks that could cause the application to refuse requests because data storage is filled.</span></span>  
  
 <span data-ttu-id="4902d-107">Můžete určit, zda je pokus o zápis, pravděpodobně selžou z tohoto důvodu <xref:System.IO.IsolatedStorage.IsolatedStorage> třída poskytuje tři vlastnosti jen pro čtení: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, a <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span><span class="sxs-lookup"><span data-stu-id="4902d-107">To help you determine whether a given write attempt is likely to fail for this reason, the <xref:System.IO.IsolatedStorage.IsolatedStorage> class provides three read-only properties: <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorage.UsedSize%2A>, and <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A>.</span></span> <span data-ttu-id="4902d-108">Tyto vlastnosti můžete použít k určení, zda zápis do úložiště způsobí, že maximální povolená velikost úložiště bude překročena.</span><span class="sxs-lookup"><span data-stu-id="4902d-108">You can use these properties to determine whether writing to the store will cause the maximum allowed size of the store to be exceeded.</span></span> <span data-ttu-id="4902d-109">Mějte na paměti, která izolované úložiště je přístupná souběžně; Proto když můžete vypočítat množství paměti zbývající úložiště, v prostoru úložiště by mohly spotřebovat čas pokusu o zápis do úložiště.</span><span class="sxs-lookup"><span data-stu-id="4902d-109">Keep in mind that isolated storage can be accessed concurrently; therefore, when you compute the amount of remaining storage, the storage space could be consumed by the time you try to write to the store.</span></span> <span data-ttu-id="4902d-110">Můžete ale maximální velikost úložiště sloužící k určení, zda horní limit na úložiště k dispozici je chystáte dostupný.</span><span class="sxs-lookup"><span data-stu-id="4902d-110">However, you can use the maximum size of the store to help determine whether the upper limit on available storage is about to be reached.</span></span>  
  
 <span data-ttu-id="4902d-111"><xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> Vlastnost závisí na důkazy od sestavení správně fungovat.</span><span class="sxs-lookup"><span data-stu-id="4902d-111">The <xref:System.IO.IsolatedStorage.IsolatedStorage.Quota%2A> property depends on evidence from the assembly to work properly.</span></span> <span data-ttu-id="4902d-112">Z tohoto důvodu by tato vlastnost načíst pouze na <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objekty, které byly vytvořeny pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, nebo <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4902d-112">For this reason, you should retrieve this property only on <xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForDomain%2A>, or <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> method.</span></span> <span data-ttu-id="4902d-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile>objekty, které byly vytvořeny jiným způsobem (například objekty, které byly vráceny z <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> metoda), nevrátí přesné maximální velikost.</span><span class="sxs-lookup"><span data-stu-id="4902d-113"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> objects that were created in any other way (for example, objects that were returned from the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetEnumerator%2A> method) will not return an accurate maximum size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4902d-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4902d-114">Example</span></span>  
 <span data-ttu-id="4902d-115">Následující příklad kódu získá izolované úložiště, vytvoří několik souborů a načte <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4902d-115">The following code example obtains an isolated store, creates a few files, and retrieves the <xref:System.IO.IsolatedStorage.IsolatedStorage.AvailableFreeSpace%2A> property.</span></span> <span data-ttu-id="4902d-116">Zbývající místo je uveden v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4902d-116">The remaining space is reported in bytes.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source7.cpp#8)]
 [!code-csharp[Conceptual.IsolatedStorage#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source7.cs#8)]
 [!code-vb[Conceptual.IsolatedStorage#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source7.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="4902d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4902d-117">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="4902d-118">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="4902d-118">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
 [<span data-ttu-id="4902d-119">Postupy: Získávání úložišť pro izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="4902d-119">How to: Obtain Stores for Isolated Storage</span></span>](../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)
