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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61950368"
---
# <a name="compose-streams"></a><span data-ttu-id="1d738-102">Vytvoření datových proudů</span><span class="sxs-lookup"><span data-stu-id="1d738-102">Compose streams</span></span>
<span data-ttu-id="1d738-103">A *záložní úložiště* je paměťové médium, například disku nebo paměti.</span><span class="sxs-lookup"><span data-stu-id="1d738-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="1d738-104">Každý záložní úložiště implementuje vlastní datový proud jako implementace <xref:System.IO.Stream> třídy.</span><span class="sxs-lookup"><span data-stu-id="1d738-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> 

<span data-ttu-id="1d738-105">Každý typ datového proudu čte a zapisuje bajtů z a do jeho dané záložního úložiště.</span><span class="sxs-lookup"><span data-stu-id="1d738-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="1d738-106">Datové proudy, které se připojují k zálohování úložišť se nazývají *základní datové proudy*.</span><span class="sxs-lookup"><span data-stu-id="1d738-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="1d738-107">Základní datové proudy mít konstruktory s parametry, které jsou potřebné k připojení datový proud záložního úložiště.</span><span class="sxs-lookup"><span data-stu-id="1d738-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="1d738-108">Například <xref:System.IO.FileStream> konstruktory, které určují parametr cesty, která určuje, jak budou sdílet soubor procesy.</span><span class="sxs-lookup"><span data-stu-id="1d738-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="1d738-109">Návrh <xref:System.IO> třídy poskytuje zjednodušené stream složení.</span><span class="sxs-lookup"><span data-stu-id="1d738-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="1d738-110">Základní datové proudy můžete na jeden nebo více průchozích datové proudy, které poskytují funkce, které chcete připojit.</span><span class="sxs-lookup"><span data-stu-id="1d738-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="1d738-111">Čtečky nebo zapisovače může připojit na konec řetězce, takže upřednostňované typy může číst nebo zapisovat snadno.</span><span class="sxs-lookup"><span data-stu-id="1d738-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="1d738-112">Vytvořte následující příklady kódu **FileStream** kolem stávající *MyFile.txt* v pořadí do vyrovnávací paměti *MyFile.txt*.</span><span class="sxs-lookup"><span data-stu-id="1d738-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="1d738-113">Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1d738-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1d738-114">V příkladech se předpokládá, že soubor s názvem *MyFile.txt* již existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="1d738-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="1d738-115">Příklad: Pomocí třídy StreamReader</span><span class="sxs-lookup"><span data-stu-id="1d738-115">Example: Use StreamReader</span></span>
<span data-ttu-id="1d738-116">Následující příklad vytvoří <xref:System.IO.StreamReader> ke čtení znaků z **FileStream**, které se předává **StreamReader** jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1d738-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="1d738-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> pak načte do <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> nenajde žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="1d738-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="1d738-118">Příklad: Použití BinaryReader</span><span class="sxs-lookup"><span data-stu-id="1d738-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="1d738-119">Následující příklad vytvoří <xref:System.IO.BinaryReader> čtení bajtů z **FileStream**, které se předává **BinaryReader** jako argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1d738-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="1d738-120"><xref:System.IO.BinaryReader.ReadByte%2A> pak načte do <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="1d738-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="1d738-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d738-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
