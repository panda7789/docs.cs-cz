---
title: Zpracování dat XML pomocí LINQ to XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 634c76c3510d594584f06ea14bed84b1b0423c31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502170"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="2ea60-102">Zpracování dat XML pomocí LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="2ea60-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="2ea60-103">Technologie LINQ to XML je nový model v rozhraní .NET Framework verze 3.5 pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="2ea60-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="2ea60-104">Technologie LINQ to XML umožňuje vývojářům provádění všeho byste očekávali s daty XML: dotazování, úpravy, vytváření, ukládání a serializace XML dokumentů.</span><span class="sxs-lookup"><span data-stu-id="2ea60-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="2ea60-105">Skutečné výhody spadat do dotazu a vytvoření možnosti.</span><span class="sxs-lookup"><span data-stu-id="2ea60-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="2ea60-106">Dotazy v technologii LINQ to XML jsou stručné a expresivní pomocí syntaxe podobné SQL než XPath nebo výraz XQuery.</span><span class="sxs-lookup"><span data-stu-id="2ea60-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="2ea60-107">Vzhledem k tomu, že výsledky dotazu může být vrácen jako kolekce elementů nebo atributů a může sloužit jako parametry pro objekty XElement, stromů XML je možné snadno transformovat z jednoho obrazce na jiný.</span><span class="sxs-lookup"><span data-stu-id="2ea60-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="2ea60-108">Technologie LINQ to XML využívá technologii (LINQ) language-integrated query v rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="2ea60-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="2ea60-109">LINQ rozšiřuje syntaxi jazyka C# a Visual Basic a poskytuje výkonné funkce dotazů, které je možné rozšířit na potenciálně jakéhokoli datového úložiště.</span><span class="sxs-lookup"><span data-stu-id="2ea60-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="2ea60-110">Zobrazit [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) podrobnou diskuzi o používání a najdete v tématu [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) přehledné informace o rozhraní LINQ.</span><span class="sxs-lookup"><span data-stu-id="2ea60-110">See [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) for a detailed discussion of its use, and see [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) for an overview of the LINQ framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea60-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ea60-111">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="2ea60-112">Technologie LINQ to XML versus model DOM</span><span class="sxs-lookup"><span data-stu-id="2ea60-112">LINQ to XML vs. DOM</span></span>](https://msdn.microsoft.com/library/19b5ed02-feb2-455a-8897-f7f0fd76aca3)
- [<span data-ttu-id="2ea60-113">Technologie LINQ to XML versus jiné technologie XML</span><span class="sxs-lookup"><span data-stu-id="2ea60-113">LINQ to XML vs. Other XML Technologies</span></span>](https://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
