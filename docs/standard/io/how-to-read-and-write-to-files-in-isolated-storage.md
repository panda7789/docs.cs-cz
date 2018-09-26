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
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079026"
---
# <a name="how-to-read-and-write-to-files-in-isolated-storage"></a>Postupy: Čtení a zápis do souborů v izolovaném úložišti
Ke čtení nebo zápis do souboru v izolovaném úložišti, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> objekt s čtečku datového proudu (<xref:System.IO.StreamReader> objekt) nebo zapisovač datového proudu (<xref:System.IO.StreamWriter> objekt).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu získá izolované úložiště a zkontroluje, jestli existuje soubor s názvem TestStore.txt v úložišti. Pokud neexistuje, vytvoří soubor a zapíše do souboru "Hello izolovaného úložiště". Pokud TestStore.txt již existuje, vzorový kód přečte ze souboru.  
  
 [!code-csharp[Conceptual.IsolatedStorage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source5.cs#5)]
 [!code-vb[Conceptual.IsolatedStorage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source5.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
- <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
- <xref:System.IO.FileMode?displayProperty=nameWithType>  
- <xref:System.IO.FileAccess?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader?displayProperty=nameWithType>  
- <xref:System.IO.StreamWriter?displayProperty=nameWithType>  
- [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)  
- [Izolované úložiště](../../../docs/standard/io/isolated-storage.md)
