---
title: LINQ na objekty (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: dce90ce78668b3732db31dee6d0a233c4d39557f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323495"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="e21ad-102">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="e21ad-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="e21ad-103">Termín "LINQ na objekty" odkazuje na použití LINQ dotazy s žádným <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekce přímo, bez použití zprostředkující LINQ zprostředkovatele nebo rozhraní API jako třeba [technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) nebo [technologie LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="e21ad-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) or [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="e21ad-104">LINQ můžete použít k dotazování všechny vyčíslitelná kolekce, jako <xref:System.Collections.Generic.List%601>, <xref:System.Array>, nebo <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="e21ad-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="e21ad-105">Kolekce může být definovaný uživatelem, nebo mohou být vráceny rozhraní API rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e21ad-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="e21ad-106">LINQ na objekty v základní smysl, představuje nový přístup do kolekcí.</span><span class="sxs-lookup"><span data-stu-id="e21ad-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="e21ad-107">Původní způsobem, jste museli zápisu komplexní `foreach` smyčky zadaných postup načtení dat z kolekce.</span><span class="sxs-lookup"><span data-stu-id="e21ad-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="e21ad-108">V metodě LINQ zápisu deklarativní kód, který popisuje, co chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="e21ad-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="e21ad-109">Kromě toho dotazů LINQ nabízí tři hlavní výhody přes tradiční `foreach` smyčky:</span><span class="sxs-lookup"><span data-stu-id="e21ad-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1.  <span data-ttu-id="e21ad-110">Jsou více stručná a čitelná, zejména v případě, že filtrování více podmínek.</span><span class="sxs-lookup"><span data-stu-id="e21ad-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2.  <span data-ttu-id="e21ad-111">Poskytují výkonný filtrování, řazení a seskupování možnosti s minimální kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e21ad-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3.  <span data-ttu-id="e21ad-112">Může být přesně do jiné zdroje dat se žádné nebo téměř žádné změny.</span><span class="sxs-lookup"><span data-stu-id="e21ad-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="e21ad-113">Obecně platí, tím složitější operace, kterou chcete provést na datech, další výhody zjistíte pomocí LINQ místo tradiční iterace techniky.</span><span class="sxs-lookup"><span data-stu-id="e21ad-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="e21ad-114">Účelem této části je za účelem ukázky LINQ přístup s příklady vyberte.</span><span class="sxs-lookup"><span data-stu-id="e21ad-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="e21ad-115">Rozhraní není určeno jako vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="e21ad-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e21ad-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e21ad-116">In This Section</span></span>  
 [<span data-ttu-id="e21ad-117">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="e21ad-117">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="e21ad-118">Vysvětluje, jak lze pro dotazování a Transformace řetězců a kolekcí řetězců LINQ.</span><span class="sxs-lookup"><span data-stu-id="e21ad-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="e21ad-119">Taky obsahuje odkazy na témata, která ukazují tyto zásady.</span><span class="sxs-lookup"><span data-stu-id="e21ad-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="e21ad-120">LINQ a reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="e21ad-120">LINQ and Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="e21ad-121">Odkazy na vzorku, který ukazuje, jak LINQ používá reflexe.</span><span class="sxs-lookup"><span data-stu-id="e21ad-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="e21ad-122">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="e21ad-122">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="e21ad-123">Vysvětluje, jak lze pomocí LINQ komunikovat se systémy souborů.</span><span class="sxs-lookup"><span data-stu-id="e21ad-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="e21ad-124">Taky obsahuje odkazy na témata, která ukazují tyto koncepty.</span><span class="sxs-lookup"><span data-stu-id="e21ad-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="e21ad-125">Postupy: dotazu na ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="e21ad-125">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="e21ad-126">Ukazuje, jak dotazu na ArrayList v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="e21ad-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="e21ad-127">Postupy: Přidání vlastních metod pro dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="e21ad-127">How to: Add Custom Methods for LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="e21ad-128">Vysvětluje, jak rozšířit sadu metody, které můžete použít pro dotazy LINQ přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e21ad-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="e21ad-129">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e21ad-129">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="e21ad-130">Obsahuje odkazy na témata, která popisují LINQ a zadejte příklady kódu, které provádět dotazy.</span><span class="sxs-lookup"><span data-stu-id="e21ad-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
