---
title: "Zpracování dat XML pomocí LINQ to XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a6b7a3c452d6b29145b8a2e7b1d2a1e824aaf508
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="0cd36-102">Zpracování dat XML pomocí LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="0cd36-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="0cd36-103">Technologie LINQ to XML je nový model v rozhraní .NET Framework verze 3.5 pro zpracování dat XML.</span><span class="sxs-lookup"><span data-stu-id="0cd36-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="0cd36-104">Technologie LINQ to XML umožňuje vývojářům provádět všechno, co byste očekávali s daty XML: dotazování, úprava, vytváření, ukládání a serializaci dokumentů XML.</span><span class="sxs-lookup"><span data-stu-id="0cd36-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="0cd36-105">Skutečné výhody ležet v možnosti dotazu a vytvoření.</span><span class="sxs-lookup"><span data-stu-id="0cd36-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="0cd36-106">Dotazy v technologii LINQ to XML nejsou stručného a výrazové, pomocí syntaxe podobné SQL než XPath nebo XQuery.</span><span class="sxs-lookup"><span data-stu-id="0cd36-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="0cd36-107">Protože výsledky dotazu může být vrácen jako elementy nebo atributy kolekce a můžete použít jako parametry pro objekty XElement, stromy XML lze snadno transformovat z jednoho obrazce do jiného.</span><span class="sxs-lookup"><span data-stu-id="0cd36-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="0cd36-108">Technologie LINQ to XML využívá technologie (LINQ) language-integrated query v rozhraní .NET Framework verze 3.5.</span><span class="sxs-lookup"><span data-stu-id="0cd36-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="0cd36-109">LINQ rozšiřuje na syntaxi jazyka C# a Visual Basic zajistit účinný dotazovací funkce, které lze rozšířit o potenciálně jakékoli datového úložiště.</span><span class="sxs-lookup"><span data-stu-id="0cd36-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="0cd36-110">V tématu [technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) pro podrobnou diskuzi o jeho použití a zjistit, [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) přehled rozhraní LINQ.</span><span class="sxs-lookup"><span data-stu-id="0cd36-110">See [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) for a detailed discussion of its use, and see [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) for an overview of the LINQ framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd36-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cd36-111">See Also</span></span>  
 <xref:System.Xml.Linq>  
 <xref:System.Linq>  
 [<span data-ttu-id="0cd36-112">Technologie LINQ to XML vs. DOM</span><span class="sxs-lookup"><span data-stu-id="0cd36-112">LINQ to XML vs. DOM</span></span>](http://msdn.microsoft.com/library/19b5ed02-feb2-455a-8897-f7f0fd76aca3)  
 [<span data-ttu-id="0cd36-113">Technologie LINQ to XML vs. Další technologie XML</span><span class="sxs-lookup"><span data-stu-id="0cd36-113">LINQ to XML vs. Other XML Technologies</span></span>](http://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
