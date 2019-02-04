---
title: 'Postupy: Čtení a zápis do nově vytvořeného datového souboru'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 065907ae0d4a38ff2ef68de6025251e28220ee96
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674617"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Postupy: Čtení a zápis do nově vytvořeného datového souboru
<xref:System.IO.BinaryWriter?displayProperty=nameWithType> a <xref:System.IO.BinaryReader?displayProperty=nameWithType> třídy se používají pro zápis a čtení dat než řetězců znaků. Následující příklad ukazuje, jak vytvořit prázdný soubor proud, zápis dat do a z něj číst data. 

V příkladu se vytvoří datový soubor s názvem *Test.data* v aktuálním adresáři vytvoří přidružený <xref:System.IO.BinaryWriter> a <xref:System.IO.BinaryReader> objekty a používá <xref:System.IO.BinaryWriter> objekt k zápisu celých čísel 0 až 10 *Test.data*, které nechá ukazatel na soubor na konci souboru. <xref:System.IO.BinaryReader> Objekt pak nastaví ukazatele souboru zpět k původu a přečte zadaný obsah.  
  
> [!NOTE]
> Pokud *Test.data* již existuje v aktuálním adresáři <xref:System.IO.IOException> je vyvolána výjimka. Použijte volbu režimu souboru <xref:System.IO.FileMode.Create?displayProperty=nameWithType> spíše než <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> vždy vytvořit nový soubor bez vyvolání výjimky.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Postupy: Vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Postupy: Otevření a připojení k souboru protokolu](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Postupy: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postupy: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Postupy: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Vstupně-výstupních operací souborů a datových proudů](../../../docs/standard/io/index.md)
