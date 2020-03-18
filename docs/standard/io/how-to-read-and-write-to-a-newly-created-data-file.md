---
title: 'Postup: Čtení a zápis do nově vytvořeného datového souboru'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155747"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Postup: Čtení a zápis do nově vytvořeného datového souboru
<xref:System.IO.BinaryWriter?displayProperty=nameWithType> Třídy <xref:System.IO.BinaryReader?displayProperty=nameWithType> a se používají pro zápis a čtení dat jiných než řetězce znaků. Následující příklad ukazuje, jak vytvořit prázdný datový proud souboru, zapisovat do něj data a číst data z něj.

V příkladu se vytvoří datový soubor s názvem *Test.data* v aktuálním adresáři, <xref:System.IO.BinaryWriter> vytvoří přidružené a <xref:System.IO.BinaryReader> objekty a použije <xref:System.IO.BinaryWriter> objekt k zápisu celá čísla 0 až 10 do *Test.data*, který ponechává ukazatel souboru na konci souboru. Objekt <xref:System.IO.BinaryReader> pak nastaví ukazatel souboru zpět na počátek a přečte zadaný obsah.  
  
> [!NOTE]
> Pokud *Test.data* již existuje v aktuálním adresáři, je vyvolána <xref:System.IO.IOException> výjimka. Použijte možnost <xref:System.IO.FileMode.Create?displayProperty=nameWithType> režimu <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> souboru, nikoli vždy vytvořit nový soubor bez vyvolání výjimky.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Postup: Výčet adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Postup: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Postup: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Postup: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postup: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Postup: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Vstupně-tono-videa](../../../docs/standard/io/index.md)
