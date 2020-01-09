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
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>Postupy: Čtení a zápis do souborů v izolovaném úložišti
Chcete-li číst ze souboru v izolovaném úložišti nebo do něj zapisovat, použijte objekt <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> s modulem pro čtení datového proudu (<xref:System.IO.StreamReader> objekt) nebo zapisovačem datového proudu (objekt<xref:System.IO.StreamWriter>).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu získá izolované úložiště a ověří, zda soubor s názvem TestStore. txt existuje v úložišti. Pokud neexistuje, vytvoří soubor a zapíše do souboru "izolované úložiště Hello". Pokud TestStore. txt již existuje, ukázkový kód přečte ze souboru.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>
- <xref:System.IO.FileMode?displayProperty=nameWithType>
- <xref:System.IO.FileAccess?displayProperty=nameWithType>
- <xref:System.IO.StreamReader?displayProperty=nameWithType>
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>
- [Vstup/výstup souborů a datových proudů](../../../docs/standard/io/index.md)
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
