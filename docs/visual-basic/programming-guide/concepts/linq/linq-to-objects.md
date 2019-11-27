---
title: LINQ na objekty
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: ef7d6fe232a788ab77661e9c5f313a80df4779b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354308"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="60249-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60249-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="60249-103">Pojem "LINQ to Objects" odkazuje na použití dotazů LINQ s jakoukoli <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekcí přímo, bez použití zprostředkujícího poskytovatele LINQ nebo rozhraní API, jako je například [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="60249-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="60249-104">Pomocí LINQ můžete zadávat dotazy na všechny vyčíslitelné kolekce, například <xref:System.Collections.Generic.List%601>, <xref:System.Array>nebo <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="60249-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="60249-105">Kolekce může být definovaná uživatelem nebo může být vrácena rozhraním .NET Framework API.</span><span class="sxs-lookup"><span data-stu-id="60249-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="60249-106">V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="60249-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="60249-107">Starým způsobem museli napsat komplexní smyčky `For Each`, které určily, jak načíst data z kolekce.</span><span class="sxs-lookup"><span data-stu-id="60249-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="60249-108">V metodě LINQ můžete napsat deklarativní kód, který popisuje, co chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="60249-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="60249-109">Kromě toho dotazy LINQ nabízí tři hlavní výhody oproti tradičním `For Each` smyčkám:</span><span class="sxs-lookup"><span data-stu-id="60249-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="60249-110">Jsou stručnější a čitelné, zejména při filtrování více podmínek.</span><span class="sxs-lookup"><span data-stu-id="60249-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="60249-111">Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="60249-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="60249-112">Je možné je přenést do jiných zdrojů dat s minimální nebo žádnou úpravou.</span><span class="sxs-lookup"><span data-stu-id="60249-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="60249-113">Obecně komplexnější operace, kterou chcete provést na datech, je větší výhodou, kterou budete používat LINQ místo tradičních technik iterací.</span><span class="sxs-lookup"><span data-stu-id="60249-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="60249-114">Účelem této části je Ukázat přístup LINQ s některými příklady výběru.</span><span class="sxs-lookup"><span data-stu-id="60249-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="60249-115">Není určena k vyčerpávajícímu určení.</span><span class="sxs-lookup"><span data-stu-id="60249-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60249-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="60249-116">In This Section</span></span>  
 [<span data-ttu-id="60249-117">LINQ a řetězce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60249-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="60249-118">Vysvětluje, jak lze LINQ použít k dotazování a transformaci řetězců a kolekcí řetězců.</span><span class="sxs-lookup"><span data-stu-id="60249-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="60249-119">Obsahuje také odkazy na témata, která ukazují tyto principy.</span><span class="sxs-lookup"><span data-stu-id="60249-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="60249-120">LINQ a reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60249-120">LINQ and Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="60249-121">Odkazuje na ukázku, která ukazuje, jak LINQ používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="60249-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="60249-122">LINQ a souborové adresáře (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60249-122">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="60249-123">Vysvětluje, jak lze pomocí technologie LINQ pracovat se systémy souborů.</span><span class="sxs-lookup"><span data-stu-id="60249-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="60249-124">Obsahuje také odkazy na témata, která ukazují tyto koncepty.</span><span class="sxs-lookup"><span data-stu-id="60249-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="60249-125">Postupy: dotazování objektu ArrayList pomocí LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60249-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="60249-126">Ukazuje, jak se dotázat na objekt C#ArrayList v.</span><span class="sxs-lookup"><span data-stu-id="60249-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="60249-127">Postupy: Přidání vlastních metod pro dotazy LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60249-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="60249-128">Vysvětluje, jak rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do rozhraní <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="60249-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="60249-129">LINQ (Language-Integrated Query) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60249-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="60249-130">Obsahuje odkazy na témata, která vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.</span><span class="sxs-lookup"><span data-stu-id="60249-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
