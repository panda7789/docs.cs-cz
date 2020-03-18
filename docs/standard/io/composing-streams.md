---
title: Skládat proudy
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160102"
---
# <a name="compose-streams"></a>Skládat proudy
*Záložní úložiště* je paměťové médium, například disk nebo paměť. Každý jiný záložní úložiště implementuje vlastní <xref:System.IO.Stream> datový proud jako implementace třídy.

Každý typ datového proudu čte a zapisuje bajty z a do jeho daného úložiště zálohování. Datové proudy, které se připojují k zálohování úložišť se nazývají *základní datové proudy*. Základní datové proudy mají konstruktory s parametry potřebné k připojení datového proudu k záložnímu úložišti. Například <xref:System.IO.FileStream> má konstruktory, které určují parametr cesty, který určuje, jak bude soubor sdílen procesy.  

Návrh <xref:System.IO> tříd poskytuje zjednodušenou kompozici datového proudu. Základní datové proudy můžete připojit k jednomu nebo více předávacím datovým proudům, které poskytují požadované funkce. Můžete připojit čtečku nebo zapisovač na konec řetězce, takže upřednostňované typy lze snadno číst nebo zapisovat.  

Následující příklady kódu vytvářejí **soubor FileStream** kolem existujícího *souboru MyFile.txt* za účelem ukládání *souboru MyFile.txt do vyrovnávací*paměti . Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.

>[!IMPORTANT]
>Příklady předpokládají, že soubor s názvem *MyFile.txt* již existuje ve stejné složce jako aplikace.  

## <a name="example-use-streamreader"></a>Příklad: Použití streamreaderu
Následující příklad vytvoří <xref:System.IO.StreamReader> číst znaky z **FileStream**, který je předán **StreamReader** jako jeho argument konstruktoru. <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>pak čte, dokud <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> nenajde žádné další znaky.  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>Příklad: Použití binaryreaderu
Následující příklad vytvoří <xref:System.IO.BinaryReader> číst bajty z **FileStream**, který je předán **BinaryReader** jako jeho konstruktor argument. <xref:System.IO.BinaryReader.ReadByte%2A>pak čte, dokud <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další bajty.  
  
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
