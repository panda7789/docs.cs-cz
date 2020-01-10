---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75344785"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="50e58-102">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="50e58-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="50e58-103">Pojem "LINQ to Objects" odkazuje na použití dotazů LINQ s jakoukoli <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> kolekcí přímo, bez použití zprostředkujícího poskytovatele LINQ nebo rozhraní API, jako je například [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="50e58-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="50e58-104">Pomocí LINQ můžete zadávat dotazy na všechny vyčíslitelné kolekce, například <xref:System.Collections.Generic.List%601>, <xref:System.Array>nebo <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="50e58-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="50e58-105">Kolekce může být definovaná uživatelem nebo může být vrácena rozhraním .NET Framework API.</span><span class="sxs-lookup"><span data-stu-id="50e58-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="50e58-106">V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="50e58-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="50e58-107">Starým způsobem museli napsat komplexní smyčky `foreach`, které určily, jak načíst data z kolekce.</span><span class="sxs-lookup"><span data-stu-id="50e58-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="50e58-108">V metodě LINQ můžete napsat deklarativní kód, který popisuje, co chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="50e58-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="50e58-109">Kromě toho dotazy LINQ nabízí tři hlavní výhody oproti tradičním `foreach` smyčkám:</span><span class="sxs-lookup"><span data-stu-id="50e58-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="50e58-110">Jsou stručnější a čitelné, zejména při filtrování více podmínek.</span><span class="sxs-lookup"><span data-stu-id="50e58-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="50e58-111">Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="50e58-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="50e58-112">Je možné je přenést do jiných zdrojů dat s minimální nebo žádnou úpravou.</span><span class="sxs-lookup"><span data-stu-id="50e58-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="50e58-113">Obecně komplexnější operace, kterou chcete provést na datech, je větší výhodou, kterou budete používat LINQ místo tradičních technik iterací.</span><span class="sxs-lookup"><span data-stu-id="50e58-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="50e58-114">Účelem této části je Ukázat přístup LINQ s některými příklady výběru.</span><span class="sxs-lookup"><span data-stu-id="50e58-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="50e58-115">Není určena k vyčerpávajícímu určení.</span><span class="sxs-lookup"><span data-stu-id="50e58-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50e58-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="50e58-116">In This Section</span></span>  
 [<span data-ttu-id="50e58-117">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="50e58-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="50e58-118">Vysvětluje, jak lze LINQ použít k dotazování a transformaci řetězců a kolekcí řetězců.</span><span class="sxs-lookup"><span data-stu-id="50e58-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="50e58-119">Obsahuje také odkazy na témata, která ukazují tyto principy.</span><span class="sxs-lookup"><span data-stu-id="50e58-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="50e58-120">LINQ a reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="50e58-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="50e58-121">Odkazuje na ukázku, která ukazuje, jak LINQ používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="50e58-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="50e58-122">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="50e58-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="50e58-123">Vysvětluje, jak lze pomocí technologie LINQ pracovat se systémy souborů.</span><span class="sxs-lookup"><span data-stu-id="50e58-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="50e58-124">Obsahuje také odkazy na témata, která ukazují tyto koncepty.</span><span class="sxs-lookup"><span data-stu-id="50e58-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="50e58-125">Postup dotazování objektu ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="50e58-125">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="50e58-126">Ukazuje, jak se dotázat na objekt C#ArrayList v.</span><span class="sxs-lookup"><span data-stu-id="50e58-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="50e58-127">Postup přidání vlastních metod pro dotazy LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="50e58-127">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="50e58-128">Vysvětluje, jak rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do rozhraní <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="50e58-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="50e58-129">Dotaz integrovaný na jazyku (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="50e58-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="50e58-130">Obsahuje odkazy na témata, která vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.</span><span class="sxs-lookup"><span data-stu-id="50e58-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
