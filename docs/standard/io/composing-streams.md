---
title: Vytvoření datových proudů
ms.date: 01/21/2019
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
ms.openlocfilehash: 452071e9726a95b4b3d9bb9cefe720d39bbc3e0c
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674344"
---
# <a name="compose-streams"></a>Vytvoření datových proudů
A *záložní úložiště* je paměťové médium, například disku nebo paměti. Každý záložní úložiště implementuje vlastní datový proud jako implementace <xref:System.IO.Stream> třídy. 

Každý typ datového proudu čte a zapisuje bajtů z a do jeho dané záložního úložiště. Datové proudy, které se připojují k zálohování úložišť se nazývají *základní datové proudy*. Základní datové proudy mít konstruktory s parametry, které jsou potřebné k připojení datový proud záložního úložiště. Například <xref:System.IO.FileStream> konstruktory, které určují parametr cesty, která určuje, jak budou sdílet soubor procesy.  

Návrh <xref:System.IO> třídy poskytuje zjednodušené stream složení. Základní datové proudy můžete na jeden nebo více průchozích datové proudy, které poskytují funkce, které chcete připojit. Čtečky nebo zapisovače může připojit na konec řetězce, takže upřednostňované typy může číst nebo zapisovat snadno.  

Vytvořte následující příklady kódu **FileStream** kolem stávající *MyFile.txt* v pořadí do vyrovnávací paměti *MyFile.txt*. Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.

>[!IMPORTANT]
>V příkladech se předpokládá, že soubor s názvem *MyFile.txt* již existuje ve stejné složce jako aplikace.  

## <a name="example-use-streamreader"></a>Příklad: Pomocí třídy StreamReader
Následující příklad vytvoří <xref:System.IO.StreamReader> ke čtení znaků z **FileStream**, které se předává **StreamReader** jako argument konstruktoru. <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> pak načte do <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> nenajde žádné další znaky.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Příklad: Použití BinaryReader
Následující příklad vytvoří <xref:System.IO.BinaryReader> čtení bajtů z **FileStream**, které se předává **BinaryReader** jako argument konstruktoru. <xref:System.IO.BinaryReader.ReadByte%2A> pak načte do <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další znaky.  
  
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
