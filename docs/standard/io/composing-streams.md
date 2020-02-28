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
# <a name="compose-streams"></a><span data-ttu-id="5d7fc-102">Vytváření datových proudů</span><span class="sxs-lookup"><span data-stu-id="5d7fc-102">Compose streams</span></span>
<span data-ttu-id="5d7fc-103">*Záložní úložiště* je úložné médium, například disk nebo paměť.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="5d7fc-104">Každé jiné záložní úložiště implementuje svůj vlastní Stream jako implementaci třídy <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span>

<span data-ttu-id="5d7fc-105">Každý typ datového proudu čte a zapisuje bajty z a do daného záložního úložiště.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="5d7fc-106">Streamy, které se připojují k záložním úložištím, se nazývají *základní proudy*</span><span class="sxs-lookup"><span data-stu-id="5d7fc-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="5d7fc-107">Základní datové proudy mají konstruktory s parametry nezbytnými pro připojení datového proudu k záložnímu úložišti.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="5d7fc-108">Například <xref:System.IO.FileStream> obsahuje konstruktory, které určují parametr cesty, který určuje, jak bude soubor sdílen procesy.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="5d7fc-109">Návrh tříd <xref:System.IO> poskytuje zjednodušené složení datových proudů.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="5d7fc-110">Základní datové proudy můžete připojit k jednomu nebo více průchozím proudům, které poskytují požadované funkce.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="5d7fc-111">Ke konci řetězce můžete připojit čtecí modul nebo zapisovač, takže preferované typy lze snadno číst nebo zapisovat.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="5d7fc-112">Následující příklady kódu vytvoří **FileStream** kolem stávajícího *soubor MyFile. txt* , aby bylo možné ukládat do vyrovnávací paměti *soubor MyFile. txt*.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="5d7fc-113">Všimněte si, že ve výchozím nastavení jsou **datové proudy** ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="5d7fc-114">V příkladech se předpokládá, že soubor s názvem *MyFile. txt* už existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="5d7fc-115">Příklad: Použití StreamReader</span><span class="sxs-lookup"><span data-stu-id="5d7fc-115">Example: Use StreamReader</span></span>
<span data-ttu-id="5d7fc-116">Následující příklad vytvoří <xref:System.IO.StreamReader> ke čtení znaků z **FileStream**, která je předána na **StreamReader** jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="5d7fc-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> pak přečte, dokud <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> nenajde žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="5d7fc-118">Příklad: použití BinaryReader</span><span class="sxs-lookup"><span data-stu-id="5d7fc-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="5d7fc-119">Následující příklad vytvoří <xref:System.IO.BinaryReader> pro čtení bajtů z **FileStream**, který je předán metodě **BinaryReader** jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="5d7fc-120"><xref:System.IO.BinaryReader.ReadByte%2A> pak přečte, dokud <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další bajty.</span><span class="sxs-lookup"><span data-stu-id="5d7fc-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="5d7fc-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d7fc-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
