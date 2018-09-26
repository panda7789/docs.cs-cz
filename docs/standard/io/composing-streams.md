---
title: Skládání datových proudů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e52b827f337892c33ec61b9affa1cc646a759c5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082302"
---
# <a name="composing-streams"></a>Skládání datových proudů
Záložní úložiště je paměťové médium, například disku nebo paměti. Každý záložní úložiště implementuje vlastní datový proud jako implementace <xref:System.IO.Stream> třídy. Každý typ datového proudu čte a zapisuje bajtů z a do jeho dané záložního úložiště. Datové proudy, které se připojují k zálohování úložišť jsou volány základní datové proudy. Základní datové proudy mít konstruktory, které mají parametry potřebné k připojení datový proud záložního úložiště. Například <xref:System.IO.FileStream> konstruktory, které určují parametr cesty, která určuje, jak budou sdílet soubor, procesy a tak dále.  
  
 Návrh <xref:System.IO> třídy poskytuje zjednodušené vytváření datových proudů. Základní datové proudy může být připojen k jedné nebo více průchozích datové proudy, které poskytují funkce, které chcete. Čtečky nebo zapisovače je tak, aby upřednostňované typy může číst nebo zapisovat snadno připojit na konci řetězce.  
  
 Následující příklad kódu vytvoří **FileStream** kolem stávající `MyFile.txt` v pořadí do vyrovnávací paměti `MyFile.txt`. (Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.) Další, <xref:System.IO.StreamReader> je vytvořen pro čtení znaků z **FileStream**, které se předává **StreamReader** jako argument konstruktoru. <xref:System.IO.StreamReader.ReadLine%2A> čte, dokud <xref:System.IO.StreamReader.Peek%2A> nenajde žádné další znaky.  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 Následující příklad kódu vytvoří **FileStream** kolem stávající `MyFile.txt` v pořadí do vyrovnávací paměti `MyFile.txt`. (Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.) Další, **BinaryReader** je vytvořen pro čtení bajtů z **FileStream**, které se předává **BinaryReader** jako argument konstruktoru. <xref:System.IO.BinaryReader.ReadByte%2A> čte, dokud <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další znaky.  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamReader>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
