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
ms.openlocfilehash: 75800210a52620c5b08a01c5f8fa888bf40843fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="composing-streams"></a><span data-ttu-id="3a167-102">Skládání datových proudů</span><span class="sxs-lookup"><span data-stu-id="3a167-102">Composing Streams</span></span>
<span data-ttu-id="3a167-103">Úložiště zálohování je úložiště médium, například na disku nebo paměti.</span><span class="sxs-lookup"><span data-stu-id="3a167-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="3a167-104">Každé záložní úložiště implementuje vlastní datový proud jako implementaci <xref:System.IO.Stream> třídy.</span><span class="sxs-lookup"><span data-stu-id="3a167-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="3a167-105">Každý typ datového proudu čte a zapisuje bajtů od a do jeho daného záložního úložiště.</span><span class="sxs-lookup"><span data-stu-id="3a167-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="3a167-106">Datové proudy, které se připojují k záložnímu úložišti se nazývají základní datové proudy.</span><span class="sxs-lookup"><span data-stu-id="3a167-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="3a167-107">Základní datové proudy mít konstruktory, které mají parametry, které jsou potřebné pro připojení datového proudu k záložnímu úložišti.</span><span class="sxs-lookup"><span data-stu-id="3a167-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="3a167-108">Například <xref:System.IO.FileStream> má konstruktory, které určí parametr cesty, která určuje, jak bude soubor sdílen procesy a podobně.</span><span class="sxs-lookup"><span data-stu-id="3a167-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="3a167-109">Návrh <xref:System.IO> třídy poskytuje zjednodušené vytváření datových proudů.</span><span class="sxs-lookup"><span data-stu-id="3a167-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="3a167-110">Základní datové proudy lze připojit k jedné nebo více průchozích datových proudů, které poskytují funkce, které chcete.</span><span class="sxs-lookup"><span data-stu-id="3a167-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="3a167-111">Čtečka nebo zapisovač lze tak, aby upřednostňované typy můžou číst nebo zapisovat snadno připojit na konci řetězce.</span><span class="sxs-lookup"><span data-stu-id="3a167-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="3a167-112">Následující příklad kódu vytvoří **FileStream** kolem existující `MyFile.txt` v pořadí do vyrovnávací paměti `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="3a167-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="3a167-113">(Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.) Další, <xref:System.IO.StreamReader> je vytvořen pro čtení znaků z **FileStream**, který je předán **StreamReader** jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3a167-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="3a167-114"><xref:System.IO.StreamReader.ReadLine%2A>čte, dokud <xref:System.IO.StreamReader.Peek%2A> nenajde žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="3a167-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="3a167-115">Následující příklad kódu vytvoří **FileStream** kolem existující `MyFile.txt` v pořadí do vyrovnávací paměti `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="3a167-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="3a167-116">(Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.) Další, **BinaryReader** je vytvořen pro čtení bajtů z **FileStream**, který je předán **BinaryReader** jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3a167-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="3a167-117"><xref:System.IO.BinaryReader.ReadByte%2A>čte, dokud <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="3a167-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="3a167-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a167-118">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
