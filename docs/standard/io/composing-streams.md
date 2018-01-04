---
title: "Skládání datových proudů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d49661e93675b80bcd579a6cd341b3dc88a688c2
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="composing-streams"></a>Skládání datových proudů
Úložiště zálohování je úložiště médium, například na disku nebo paměti. Každé záložní úložiště implementuje vlastní datový proud jako implementaci <xref:System.IO.Stream> třídy. Každý typ datového proudu čte a zapisuje bajtů od a do jeho daného záložního úložiště. Datové proudy, které se připojují k záložnímu úložišti se nazývají základní datové proudy. Základní datové proudy mít konstruktory, které mají parametry, které jsou potřebné pro připojení datového proudu k záložnímu úložišti. Například <xref:System.IO.FileStream> má konstruktory, které určí parametr cesty, která určuje, jak bude soubor sdílen procesy a podobně.  
  
 Návrh <xref:System.IO> třídy poskytuje zjednodušené vytváření datových proudů. Základní datové proudy lze připojit k jedné nebo více průchozích datových proudů, které poskytují funkce, které chcete. Čtečka nebo zapisovač lze tak, aby upřednostňované typy můžou číst nebo zapisovat snadno připojit na konci řetězce.  
  
 Následující příklad kódu vytvoří **FileStream** kolem existující `MyFile.txt` v pořadí do vyrovnávací paměti `MyFile.txt`. (Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.) Další, <xref:System.IO.StreamReader> je vytvořen pro čtení znaků z **FileStream**, který je předán **StreamReader** jako argument konstruktoru. <xref:System.IO.StreamReader.ReadLine%2A>čte, dokud <xref:System.IO.StreamReader.Peek%2A> nenajde žádné další znaky.  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 Následující příklad kódu vytvoří **FileStream** kolem existující `MyFile.txt` v pořadí do vyrovnávací paměti `MyFile.txt`. (Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.) Další, **BinaryReader** je vytvořen pro čtení bajtů z **FileStream**, který je předán **BinaryReader** jako argument konstruktoru. <xref:System.IO.BinaryReader.ReadByte%2A>čte, dokud <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další znaky.  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
