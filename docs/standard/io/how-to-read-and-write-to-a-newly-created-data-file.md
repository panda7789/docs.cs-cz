---
title: 'Postupy: čtení a zápis do nově vytvořeného datového souboru'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
ms.openlocfilehash: 3772aeeb25d1251a13fde2a0e51a913e5e39eabc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155747"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Postupy: čtení a zápis do nově vytvořeného datového souboru
Třídy <xref:System.IO.BinaryWriter?displayProperty=nameWithType> a <xref:System.IO.BinaryReader?displayProperty=nameWithType> jsou používány pro zápis a čtení jiných dat než řetězců znaků. Následující příklad ukazuje, jak vytvořit prázdný datový proud souboru, zapsat do něj data a číst z něj data.

Příklad vytvoří datový soubor s názvem *test. data* v aktuálním adresáři, vytvoří přidružené objekty <xref:System.IO.BinaryWriter> a <xref:System.IO.BinaryReader> a pomocí objektu <xref:System.IO.BinaryWriter> zapíše celá čísla 0 až 10 pro *test. data*, která ponechají ukazatel na soubor na konci souboru. Objekt <xref:System.IO.BinaryReader> pak nastaví ukazatel na soubor zpět na počátek a přečte zadaný obsah.  
  
> [!NOTE]
> IF *test. data* již v aktuálním adresáři existují, je vyvolána výjimka <xref:System.IO.IOException>. Použijte možnost režim souboru <xref:System.IO.FileMode.Create?displayProperty=nameWithType> místo <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType>, pokud chcete vždy vytvořit nový soubor bez vyvolání výjimky.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Postupy: zobrazení výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Postupy: otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Postupy: čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Postupy: zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postupy: čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Postupy: zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Vstupně-výstupní operace se soubory a datovým proudem](../../../docs/standard/io/index.md)
