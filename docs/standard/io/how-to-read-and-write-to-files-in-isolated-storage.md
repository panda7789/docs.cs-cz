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
ms.openlocfilehash: a1ea65b0b8280faf51595b2fe9edcbf17eaabd8f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706683"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a><span data-ttu-id="c2620-102">Postupy: Čtení a zápis do souborů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="c2620-102">How to: Read and Write to Files in Isolated Storage</span></span>
<span data-ttu-id="c2620-103">Chcete-li číst ze souboru v izolovaném úložišti nebo do něj zapisovat, použijte objekt <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> s modulem pro čtení datového proudu (<xref:System.IO.StreamReader> objekt) nebo zapisovačem datového proudu (objekt<xref:System.IO.StreamWriter>).</span><span class="sxs-lookup"><span data-stu-id="c2620-103">To read from, or write to, a file in an isolated store, use an <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> object with a stream reader (<xref:System.IO.StreamReader> object) or stream writer (<xref:System.IO.StreamWriter> object).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2620-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2620-104">Example</span></span>  
 <span data-ttu-id="c2620-105">Následující příklad kódu získá izolované úložiště a ověří, zda soubor s názvem TestStore. txt existuje v úložišti.</span><span class="sxs-lookup"><span data-stu-id="c2620-105">The following code example obtains an isolated store and checks whether a file named TestStore.txt exists in the store.</span></span> <span data-ttu-id="c2620-106">Pokud neexistuje, vytvoří soubor a zapíše do souboru "izolované úložiště Hello".</span><span class="sxs-lookup"><span data-stu-id="c2620-106">If it doesn't exist, it creates the file and writes "Hello Isolated Storage" to the file.</span></span> <span data-ttu-id="c2620-107">Pokud TestStore. txt již existuje, ukázkový kód přečte ze souboru.</span><span class="sxs-lookup"><span data-stu-id="c2620-107">If TestStore.txt already exists, the example code reads from the file.</span></span>  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="c2620-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2620-108">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [<span data-ttu-id="c2620-109">Vstup/výstup souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="c2620-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="c2620-110">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="c2620-110">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
