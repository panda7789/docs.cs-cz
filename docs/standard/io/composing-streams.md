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
# <a name="compose-streams"></a><span data-ttu-id="0237d-102">Skládat proudy</span><span class="sxs-lookup"><span data-stu-id="0237d-102">Compose streams</span></span>
<span data-ttu-id="0237d-103">*Záložní úložiště* je paměťové médium, například disk nebo paměť.</span><span class="sxs-lookup"><span data-stu-id="0237d-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="0237d-104">Každý jiný záložní úložiště implementuje vlastní <xref:System.IO.Stream> datový proud jako implementace třídy.</span><span class="sxs-lookup"><span data-stu-id="0237d-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span>

<span data-ttu-id="0237d-105">Každý typ datového proudu čte a zapisuje bajty z a do jeho daného úložiště zálohování.</span><span class="sxs-lookup"><span data-stu-id="0237d-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="0237d-106">Datové proudy, které se připojují k zálohování úložišť se nazývají *základní datové proudy*.</span><span class="sxs-lookup"><span data-stu-id="0237d-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="0237d-107">Základní datové proudy mají konstruktory s parametry potřebné k připojení datového proudu k záložnímu úložišti.</span><span class="sxs-lookup"><span data-stu-id="0237d-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="0237d-108">Například <xref:System.IO.FileStream> má konstruktory, které určují parametr cesty, který určuje, jak bude soubor sdílen procesy.</span><span class="sxs-lookup"><span data-stu-id="0237d-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="0237d-109">Návrh <xref:System.IO> tříd poskytuje zjednodušenou kompozici datového proudu.</span><span class="sxs-lookup"><span data-stu-id="0237d-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="0237d-110">Základní datové proudy můžete připojit k jednomu nebo více předávacím datovým proudům, které poskytují požadované funkce.</span><span class="sxs-lookup"><span data-stu-id="0237d-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="0237d-111">Můžete připojit čtečku nebo zapisovač na konec řetězce, takže upřednostňované typy lze snadno číst nebo zapisovat.</span><span class="sxs-lookup"><span data-stu-id="0237d-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="0237d-112">Následující příklady kódu vytvářejí **soubor FileStream** kolem existujícího *souboru MyFile.txt* za účelem ukládání *souboru MyFile.txt do vyrovnávací*paměti .</span><span class="sxs-lookup"><span data-stu-id="0237d-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="0237d-113">Všimněte si, že **FileStreams** jsou ve výchozím nastavení do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0237d-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="0237d-114">Příklady předpokládají, že soubor s názvem *MyFile.txt* již existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="0237d-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="0237d-115">Příklad: Použití streamreaderu</span><span class="sxs-lookup"><span data-stu-id="0237d-115">Example: Use StreamReader</span></span>
<span data-ttu-id="0237d-116">Následující příklad vytvoří <xref:System.IO.StreamReader> číst znaky z **FileStream**, který je předán **StreamReader** jako jeho argument konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0237d-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="0237d-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>pak čte, dokud <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> nenajde žádné další znaky.</span><span class="sxs-lookup"><span data-stu-id="0237d-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="0237d-118">Příklad: Použití binaryreaderu</span><span class="sxs-lookup"><span data-stu-id="0237d-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="0237d-119">Následující příklad vytvoří <xref:System.IO.BinaryReader> číst bajty z **FileStream**, který je předán **BinaryReader** jako jeho konstruktor argument.</span><span class="sxs-lookup"><span data-stu-id="0237d-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="0237d-120"><xref:System.IO.BinaryReader.ReadByte%2A>pak čte, dokud <xref:System.IO.BinaryReader.PeekChar%2A> nenajde žádné další bajty.</span><span class="sxs-lookup"><span data-stu-id="0237d-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="0237d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0237d-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
