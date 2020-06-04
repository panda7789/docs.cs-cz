---
title: LINQ na objekty
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: 1dca449f12c312fd395be56ebcb426c3a63b64d0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369060"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="e2c87-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c87-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="e2c87-103">Pojem "LINQ to Objects" odkazuje na použití dotazů LINQ s libovolnou <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> kolekcí nebo přímo, bez použití zprostředkujícího poskytovatele LINQ nebo rozhraní API, jako je například [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e2c87-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](linq-to-xml.md).</span></span> <span data-ttu-id="e2c87-104">LINQ můžete použít k dotazování na všechny vyčíslitelné kolekce, jako například <xref:System.Collections.Generic.List%601> , <xref:System.Array> nebo <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="e2c87-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="e2c87-105">Kolekce může být definovaná uživatelem nebo může být vrácena rozhraním .NET Framework API.</span><span class="sxs-lookup"><span data-stu-id="e2c87-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="e2c87-106">V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="e2c87-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="e2c87-107">Starým způsobem museli napsat složitou `For Each` smyčku, která určuje, jak načíst data z kolekce.</span><span class="sxs-lookup"><span data-stu-id="e2c87-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="e2c87-108">V metodě LINQ můžete napsat deklarativní kód, který popisuje, co chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="e2c87-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="e2c87-109">Kromě toho dotazy LINQ nabízí tři hlavní výhody oproti tradičním `For Each` smyčkám:</span><span class="sxs-lookup"><span data-stu-id="e2c87-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="e2c87-110">Jsou stručnější a čitelné, zejména při filtrování více podmínek.</span><span class="sxs-lookup"><span data-stu-id="e2c87-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="e2c87-111">Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e2c87-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="e2c87-112">Je možné je přenést do jiných zdrojů dat s minimální nebo žádnou úpravou.</span><span class="sxs-lookup"><span data-stu-id="e2c87-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="e2c87-113">Obecně komplexnější operace, kterou chcete provést na datech, je větší výhodou, kterou budete používat LINQ místo tradičních technik iterací.</span><span class="sxs-lookup"><span data-stu-id="e2c87-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="e2c87-114">Účelem této části je Ukázat přístup LINQ s některými příklady výběru.</span><span class="sxs-lookup"><span data-stu-id="e2c87-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="e2c87-115">Není určena k vyčerpávajícímu určení.</span><span class="sxs-lookup"><span data-stu-id="e2c87-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2c87-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e2c87-116">In This Section</span></span>  
 [<span data-ttu-id="e2c87-117">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c87-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)  
 <span data-ttu-id="e2c87-118">Vysvětluje, jak lze LINQ použít k dotazování a transformaci řetězců a kolekcí řetězců.</span><span class="sxs-lookup"><span data-stu-id="e2c87-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="e2c87-119">Obsahuje také odkazy na témata, která ukazují tyto principy.</span><span class="sxs-lookup"><span data-stu-id="e2c87-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="e2c87-120">LINQ a reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c87-120">LINQ and Reflection (Visual Basic)</span></span>](linq-and-reflection.md)  
 <span data-ttu-id="e2c87-121">Odkazuje na ukázku, která ukazuje, jak LINQ používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="e2c87-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="e2c87-122">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c87-122">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)  
 <span data-ttu-id="e2c87-123">Vysvětluje, jak lze pomocí technologie LINQ pracovat se systémy souborů.</span><span class="sxs-lookup"><span data-stu-id="e2c87-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="e2c87-124">Obsahuje také odkazy na témata, která ukazují tyto koncepty.</span><span class="sxs-lookup"><span data-stu-id="e2c87-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="e2c87-125">Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c87-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="e2c87-126">Ukazuje, jak se dotázat na objekt ArrayList v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="e2c87-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="e2c87-127">Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c87-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="e2c87-128">Vysvětluje, jak rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e2c87-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="e2c87-129">LINQ (Language-Integrated Query) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2c87-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 <span data-ttu-id="e2c87-130">Obsahuje odkazy na témata, která vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.</span><span class="sxs-lookup"><span data-stu-id="e2c87-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
