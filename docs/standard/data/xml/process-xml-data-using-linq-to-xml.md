---
title: Zpracování dat XML pomocí LINQ to XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
ms.openlocfilehash: f45c5c9dccd2c1e8bdd67000a8b2f22425822ac9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710463"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="9ab6c-102">Zpracování dat XML pomocí LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="9ab6c-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="9ab6c-103">LINQ to XML je nový model ve .NET Framework verze 3,5 pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="9ab6c-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="9ab6c-104">LINQ to XML umožňuje vývojářům dělat vše, co by očekávalo s daty XML: dotazování, úpravy, vytváření, ukládání a serializace dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="9ab6c-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="9ab6c-105">Skutečné výhody se nacházejí v dotazech a možnosti vytváření.</span><span class="sxs-lookup"><span data-stu-id="9ab6c-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="9ab6c-106">Dotazy v LINQ to XML jsou stručné a výrazné pomocí syntaxe, která se podobá jazyku SQL, než XPath nebo XQuery.</span><span class="sxs-lookup"><span data-stu-id="9ab6c-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="9ab6c-107">Vzhledem k tomu, že výsledky dotazu mohou být vráceny jako kolekce prvků nebo atributů a lze je použít jako parametry pro objekty XElement, mohou být stromy XML snadno transformované z jednoho obrazce na jiný.</span><span class="sxs-lookup"><span data-stu-id="9ab6c-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="9ab6c-108">LINQ to XML využívá technologii LINQ (Language-Integrated Query) v .NET Framework verze 3,5.</span><span class="sxs-lookup"><span data-stu-id="9ab6c-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="9ab6c-109">LINQ rozšiřuje jazykovou syntaxi C# a Visual Basic poskytuje výkonné možnosti dotazování, které lze rozšířit na potenciálně libovolné úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="9ab6c-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="9ab6c-110">Podrobné informace o jeho použití najdete v tématu [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9ab6c-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="9ab6c-111">Přehled rozhraní LINQ Framework naleznete v tématu [Language-Integrated Query (LINQ) C# ](../../../csharp/programming-guide/concepts/linq/index.md) nebo [LINQ (Language-Integrated Query)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="9ab6c-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab6c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ab6c-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="9ab6c-113">LINQ to XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab6c-113">LINQ to XML vs. DOM (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="9ab6c-114">LINQ to XML vs. DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ab6c-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="9ab6c-115">LINQ to XML vs. další technologie XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab6c-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- [<span data-ttu-id="9ab6c-116">LINQ to XML vs. další technologie XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ab6c-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
