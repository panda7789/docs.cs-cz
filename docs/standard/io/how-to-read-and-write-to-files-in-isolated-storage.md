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
ms.openlocfilehash: 90195e4e1a368f8b8b0fcf04fd8d86afce3ea7c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573773"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="5ae9d-102">Postupy: Čtení a zápis do souborů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="5ae9d-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="5ae9d-103">Chcete-li číst nebo zapisovat do souboru v izolovaném úložišti, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> objekt s čtečku datového proudu (<xref:System.IO.StreamReader> objektu) nebo zapisovač datového proudu (<xref:System.IO.StreamWriter> objekt).</span><span class="sxs-lookup"><span data-stu-id="5ae9d-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ae9d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ae9d-104">Example</span></span>  
 <span data-ttu-id="5ae9d-105">Následující příklad kódu získá izolované úložiště a ověří, zda soubor s názvem TestStore.txt existuje v úložišti.</span><span class="sxs-lookup"><span data-stu-id="5ae9d-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="5ae9d-106">Pokud neexistuje, vytvoří soubor a zapíše "Hello izolované úložiště" do souboru.</span><span class="sxs-lookup"><span data-stu-id="5ae9d-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="5ae9d-107">Pokud TestStore.txt již existuje, ukázkový kód čte ze souboru.</span><span class="sxs-lookup"><span data-stu-id="5ae9d-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="5ae9d-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ae9d-108">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 <xref:System.IO.FileMode?displayProperty=nameWithType>  
 <xref:System.IO.FileAccess?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader?displayProperty=nameWithType>  
 <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
 [<span data-ttu-id="5ae9d-109">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="5ae9d-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="5ae9d-110">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="5ae9d-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
