---
title: 'Postupy: čtení a zápis do nově vytvořeného datového souboru'
description: Přečtěte si, jak číst a zapisovat do nově vytvořeného datového souboru v rozhraní .NET pomocí tříd System. IO. BinaryReader a System. IO. BinaryWriter.
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
ms.openlocfilehash: 9a6b2985b7f532476c0f4c0f998d710f95e55d3a
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769155"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>Postupy: čtení a zápis do nově vytvořeného datového souboru
<xref:System.IO.BinaryWriter?displayProperty=nameWithType>Třídy a <xref:System.IO.BinaryReader?displayProperty=nameWithType> jsou používány pro zápis a čtení jiných dat než řetězců znaků. Následující příklad ukazuje, jak vytvořit prázdný datový proud souboru, zapsat do něj data a číst z něj data.

Příklad vytvoří datový soubor s názvem *test. data* v aktuálním adresáři, vytvoří přidružené <xref:System.IO.BinaryWriter> objekty a a <xref:System.IO.BinaryReader> pomocí <xref:System.IO.BinaryWriter> objektu zapíše celá čísla 0 až 10 pro *test. data*, která na konci souboru ponechají ukazatel na soubor. <xref:System.IO.BinaryReader>Objekt pak nastaví ukazatel na soubor zpět na počátek a přečte zadaný obsah.  
  
> [!NOTE]
> IF *test. data* již v aktuálním adresáři existují, <xref:System.IO.IOException> je vyvolána výjimka. Místo toho použijte možnost režim souboru, <xref:System.IO.FileMode.Create?displayProperty=nameWithType> nikoli <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> vždy vytvořit nový soubor bez vyvolání výjimky.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [Postupy: zobrazení výčtu adresářů a souborů](how-to-enumerate-directories-and-files.md)  
- [Postupy: otevření a připojení k souboru protokolu](how-to-open-and-append-to-a-log-file.md)  
- [Postupy: čtení textu ze souboru](how-to-read-text-from-a-file.md)  
- [Postupy: zápis textu do souboru](how-to-write-text-to-a-file.md)  
- [Postupy: čtení znaků z řetězce](how-to-read-characters-from-a-string.md)  
- [Postupy: zápis znaků do řetězce](how-to-write-characters-to-a-string.md)  
- [Vstup/výstup souborů a streamů](index.md)
