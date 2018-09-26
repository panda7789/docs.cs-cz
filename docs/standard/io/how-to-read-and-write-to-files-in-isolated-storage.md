---
title: 'Postupy: Čtení a zápis do souborů v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- files, isolated storage
- reading data
- storing data using isolated storage, reading and writing to files
- writing to files within store
- data storage using isolated storage, reading and writing to files
- reading files within store
- isolated storage, reading and writing to files
- data stores, reading and writing to files
- stores, reading and writing to files
ms.assetid: f977ebdc-1b55-475a-bc3d-3376470b08ae
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9aecf7aef9023439e145d408e40fb4adf5c0e986
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192219"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="f13b7-102">Postupy: Čtení a zápis do souborů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="f13b7-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="f13b7-103">Ke čtení nebo zápis do souboru v izolovaném úložišti, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> objekt s čtečku datového proudu (<xref:System.IO.StreamReader> objekt) nebo zapisovač datového proudu (<xref:System.IO.StreamWriter> objekt).</span><span class="sxs-lookup"><span data-stu-id="f13b7-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f13b7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f13b7-104">Example</span></span>  
 <span data-ttu-id="f13b7-105">Následující příklad kódu získá izolované úložiště a zkontroluje, jestli existuje soubor s názvem TestStore.txt v úložišti.</span><span class="sxs-lookup"><span data-stu-id="f13b7-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="f13b7-106">Pokud neexistuje, vytvoří soubor a zapíše do souboru "Hello izolovaného úložiště".</span><span class="sxs-lookup"><span data-stu-id="f13b7-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="f13b7-107">Pokud TestStore.txt již existuje, vzorový kód přečte ze souboru.</span><span class="sxs-lookup"><span data-stu-id="f13b7-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f13b7-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f13b7-108">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
- <xref:System.IO.FileMode?displayProperty=nameWithType>  
- <xref:System.IO.FileAccess?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader?displayProperty=nameWithType>  
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
- [<span data-ttu-id="f13b7-109">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="f13b7-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="f13b7-110">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="f13b7-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
