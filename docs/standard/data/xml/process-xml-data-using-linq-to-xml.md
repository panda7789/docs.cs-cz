---
title: Zpracování dat XML pomocí LINQ to XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1554c3e2b13dd0ea0d64ccd7e7caee0a1e0dd3f9
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835562"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="894d4-102">Zpracování dat XML pomocí LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="894d4-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="894d4-103">Technologie LINQ to XML je nový model v rozhraní .NET Framework verze 3.5 pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="894d4-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="894d4-104">Technologie LINQ to XML umožňuje vývojářům provádění všeho byste očekávali s daty XML: dotazování, úpravy, vytváření, ukládání a serializace XML dokumentů.</span><span class="sxs-lookup"><span data-stu-id="894d4-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="894d4-105">Skutečné výhody spadat do dotazu a vytvoření možnosti.</span><span class="sxs-lookup"><span data-stu-id="894d4-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="894d4-106">Dotazy v technologii LINQ to XML jsou stručné a expresivní pomocí syntaxe podobné SQL než XPath nebo výraz XQuery.</span><span class="sxs-lookup"><span data-stu-id="894d4-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="894d4-107">Vzhledem k tomu, že výsledky dotazu může být vrácen jako kolekce elementů nebo atributů a může sloužit jako parametry pro objekty XElement, stromů XML je možné snadno transformovat z jednoho obrazce na jiný.</span><span class="sxs-lookup"><span data-stu-id="894d4-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="894d4-108">Technologie LINQ to XML využívá technologii (LINQ) language-integrated query v rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="894d4-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="894d4-109">LINQ rozšiřuje syntaxi jazyka C# a Visual Basic a poskytuje výkonné funkce dotazů, které je možné rozšířit na potenciálně jakéhokoli datového úložiště.</span><span class="sxs-lookup"><span data-stu-id="894d4-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="894d4-110">Podrobnou diskuzi o jeho použití, naleznete v tématu [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) a [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="894d4-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="894d4-111">Přehled rozhraní LINQ, naleznete v tématu [Language-Integrated Query (LINQ) - C# ](../../../csharp/programming-guide/concepts/linq/index.md) nebo [Language-Integrated Query (LINQ) - jazyka Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="894d4-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="894d4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="894d4-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="894d4-113">Technologie LINQ to XML versus DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="894d4-113">LINQ to XML vs. DOM (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="894d4-114">Technologie LINQ to XML versus Modelu DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="894d4-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="894d4-115">Technologie LINQ to XML versus Jiné technologie XML (C#)</span><span class="sxs-lookup"><span data-stu-id="894d4-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- [<span data-ttu-id="894d4-116">Technologie LINQ to XML versus Jiné technologie XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="894d4-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
