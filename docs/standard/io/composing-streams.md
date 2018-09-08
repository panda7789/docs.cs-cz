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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44182461"
---
# <a name="composing-streams"></a><span data-ttu-id="4c0f8-102">Skládání datových proudů</span><span class="sxs-lookup"><span data-stu-id="4c0f8-102">Composing Streams</span></span>
<span data-ttu-id="4c0f8-103">Záložní úložiště je paměťové médium, například disku nebo paměti.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="4c0f8-104">Každý záložní úložiště implementuje vlastní datový proud jako implementace <xref:System.IO.Stream> třídy.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="4c0f8-105">Každý typ datového proudu čte a zapisuje bajtů z a do jeho dané záložního úložiště.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="4c0f8-106">Datové proudy, které se připojují k zálohování úložišť jsou volány základní datové proudy.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="4c0f8-107">Základní datové proudy mít konstruktory, které mají parametry potřebné k připojení datový proud záložního úložiště.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="4c0f8-108">Například <xref:System.IO.FileStream> konstruktory, které určují parametr cesty, která určuje, jak budou sdílet soubor, procesy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="4c0f8-109">Návrh <xref:System.IO> třídy poskytuje zjednodušené vytváření datových proudů.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="4c0f8-110">Základní datové proudy může být připojen k jedné nebo více průchozích datové proudy, které poskytují funkce, které chcete.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="4c0f8-111">Čtečky nebo zapisovače je tak, aby upřednostňované typy může číst nebo zapisovat snadno připojit na konci řetězce.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="4c0f8-112">Následující příklad kódu vytvoří **FileStream** kolem stávající `MyFile.txt` v pořadí do vyrovnávací paměti `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="4c0f8-113">(Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.) Další, <xref:System.IO.StreamReader> je vytvořen pro čtení znaků z **FileStream**, které se předává **StreamReader** jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="4c0f8-114"><xref:System.IO.StreamReader.ReadLine%2A> čte, dokud <xref:System.IO.StreamReader.Peek%2A> nenajde žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="4c0f8-115">Následující příklad kódu vytvoří **FileStream** kolem stávající `MyFile.txt` v pořadí do vyrovnávací paměti `MyFile.txt`.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="4c0f8-116">(Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.) Další, **BinaryReader** je vytvořen pro čtení bajtů z **FileStream**, které se předává **BinaryReader** jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="4c0f8-117"><xref:System.IO.BinaryReader.ReadByte%2A> čte, dokud <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="4c0f8-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="4c0f8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c0f8-118">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
