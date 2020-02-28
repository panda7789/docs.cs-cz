---
title: Vytváření datových proudů
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
ms.openlocfilehash: 3f18712793254f4942c092c87a3e64c73b492ae0
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160102"
---
# <a name="compose-streams"></a>Vytváření datových proudů
*Záložní úložiště* je úložné médium, například disk nebo paměť. Každé jiné záložní úložiště implementuje svůj vlastní Stream jako implementaci třídy <xref:System.IO.Stream>.

Každý typ datového proudu čte a zapisuje bajty z a do daného záložního úložiště. Streamy, které se připojují k záložním úložištím, se nazývají *základní proudy* Základní datové proudy mají konstruktory s parametry nezbytnými pro připojení datového proudu k záložnímu úložišti. Například <xref:System.IO.FileStream> obsahuje konstruktory, které určují parametr cesty, který určuje, jak bude soubor sdílen procesy.  

Návrh tříd <xref:System.IO> poskytuje zjednodušené složení datových proudů. Základní datové proudy můžete připojit k jednomu nebo více průchozím proudům, které poskytují požadované funkce. Ke konci řetězce můžete připojit čtecí modul nebo zapisovač, takže preferované typy lze snadno číst nebo zapisovat.  

Následující příklady kódu vytvoří **FileStream** kolem stávajícího *soubor MyFile. txt* , aby bylo možné ukládat do vyrovnávací paměti *soubor MyFile. txt*. Všimněte si, že ve výchozím nastavení jsou **datové proudy** ve vyrovnávací paměti.

>[!IMPORTANT]
>V příkladech se předpokládá, že soubor s názvem *MyFile. txt* už existuje ve stejné složce jako aplikace.  

## <a name="example-use-streamreader"></a>Příklad: Použití StreamReader
Následující příklad vytvoří <xref:System.IO.StreamReader> ke čtení znaků z **FileStream**, která je předána na **StreamReader** jako argument konstruktoru. <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> pak přečte, dokud <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> nenajde žádné další znaky.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Příklad: použití BinaryReader
Následující příklad vytvoří <xref:System.IO.BinaryReader> pro čtení bajtů z **FileStream**, který je předán metodě **BinaryReader** jako argument konstruktoru. <xref:System.IO.BinaryReader.ReadByte%2A> pak přečte, dokud <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další bajty.  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
