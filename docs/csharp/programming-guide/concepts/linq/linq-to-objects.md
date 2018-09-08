---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 19dd15fdd7e818e0619647205f2369a55f3bc2b0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213949"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="891bf-102">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="891bf-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="891bf-103">Termín "LINQ na objekty" odkazuje na použití odkazu LINQ dotazy s žádným <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekce přímo, bez použití zprostředkující zprostředkovatele LINQ nebo rozhraní API, jako [technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="891bf-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="891bf-104">LINQ můžete použít k dotazování všechny vyčíslitelné kolekce, jako například <xref:System.Collections.Generic.List%601>, <xref:System.Array>, nebo <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="891bf-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="891bf-105">Kolekce může být uživatelem definované nebo mohou být vráceny rozhraní API .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="891bf-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="891bf-106">V základní smysl představuje LINQ to Objects nový přístup ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="891bf-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="891bf-107">Starý způsob jste museli psát složité `foreach` smyček, které zadaná jak načíst data z kolekce.</span><span class="sxs-lookup"><span data-stu-id="891bf-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="891bf-108">U přístupu s LINQ napíšete deklarativního kódu, který popisuje, co chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="891bf-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="891bf-109">Kromě toho dotazů LINQ nabízejí tři hlavní výhody oproti tradičním `foreach` smyček:</span><span class="sxs-lookup"><span data-stu-id="891bf-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1.  <span data-ttu-id="891bf-110">Jsou stručnějším a čitelnějším, zejména v případě, že filtrování více podmínek.</span><span class="sxs-lookup"><span data-stu-id="891bf-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2.  <span data-ttu-id="891bf-111">Poskytují efektivní filtrování, řazení a seskupování schopností minimální kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="891bf-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3.  <span data-ttu-id="891bf-112">Může být přenést k jiným zdrojům dat s téměř nebo vůbec žádné změny.</span><span class="sxs-lookup"><span data-stu-id="891bf-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="891bf-113">Obecně platí, tím složitější operace, které chcete provést na datech, další výhody značným s využitím jazyka LINQ místo iterace tradiční techniky.</span><span class="sxs-lookup"><span data-stu-id="891bf-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="891bf-114">Cílem této části je předvést přístup LINQ s příklady vyberte.</span><span class="sxs-lookup"><span data-stu-id="891bf-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="891bf-115">Není určena být vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="891bf-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="891bf-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="891bf-116">In This Section</span></span>  
 [<span data-ttu-id="891bf-117">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="891bf-117">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="891bf-118">Tento článek vysvětluje použití LINQ na dotazování a transformaci řetězce a kolekce řetězců.</span><span class="sxs-lookup"><span data-stu-id="891bf-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="891bf-119">Obsahuje také odkazy na témata, která ukazují tyto zásady.</span><span class="sxs-lookup"><span data-stu-id="891bf-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="891bf-120">LINQ a reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="891bf-120">LINQ and Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="891bf-121">Obsahuje odkazy na ukázky, která ukazuje, jak LINQ používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="891bf-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="891bf-122">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="891bf-122">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="891bf-123">Vysvětluje, jak lze pomocí LINQ komunikovat se systémy souborů.</span><span class="sxs-lookup"><span data-stu-id="891bf-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="891bf-124">Obsahuje také odkazy na témata, které předvádějí koncepce.</span><span class="sxs-lookup"><span data-stu-id="891bf-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="891bf-125">Postupy: vytvoření dotazu na ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="891bf-125">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="891bf-126">Demonstruje postup vytvoření dotazu na ArrayList v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="891bf-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="891bf-127">Postupy: přidávání vlastních metod do dotazů LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="891bf-127">How to: Add Custom Methods for LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="891bf-128">Vysvětluje, jak rozšířit sadu metod, které můžete použít pro LINQ dotazy přidáním rozšiřující metody, které <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="891bf-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="891bf-129">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="891bf-129">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="891bf-130">Obsahuje odkazy na témata, která vysvětlují LINQ a příklady kódu, které provádějí dotazy.</span><span class="sxs-lookup"><span data-stu-id="891bf-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
