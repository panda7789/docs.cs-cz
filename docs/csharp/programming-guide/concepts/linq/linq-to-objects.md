---
title: LINQ to Objects (C#)
description: Přečtěte si o LINQ to Objects v jazyce C#, která používá dotazy LINQ s libovolnou kolekcí IEnumerable nebo IEnumerable <T> bez zprostředkujícího poskytovatele LINQ nebo rozhraní API.
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 7b67690ee13f207441bc94155acd91047b63b3df
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165551"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="38ed6-103">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="38ed6-103">LINQ to Objects (C#)</span></span>

<span data-ttu-id="38ed6-104">Pojem "LINQ to Objects" odkazuje na použití dotazů LINQ s libovolnou <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> kolekcí nebo přímo, bez použití zprostředkujícího poskytovatele LINQ nebo rozhraní API, jako je například [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ to XML](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="38ed6-104">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="38ed6-105">LINQ můžete použít k dotazování na všechny vyčíslitelné kolekce, jako například <xref:System.Collections.Generic.List%601> , <xref:System.Array> nebo <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="38ed6-105">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="38ed6-106">Kolekce může být definovaná uživatelem nebo může být vrácena rozhraním .NET API.</span><span class="sxs-lookup"><span data-stu-id="38ed6-106">The collection may be user-defined or may be returned by a .NET API.</span></span>  
  
 <span data-ttu-id="38ed6-107">V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="38ed6-107">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="38ed6-108">Starým způsobem museli napsat složitou `foreach` smyčku, která určuje, jak načíst data z kolekce.</span><span class="sxs-lookup"><span data-stu-id="38ed6-108">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="38ed6-109">V metodě LINQ můžete napsat deklarativní kód, který popisuje, co chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="38ed6-109">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="38ed6-110">Kromě toho dotazy LINQ nabízí tři hlavní výhody oproti tradičním `foreach` smyčkám:</span><span class="sxs-lookup"><span data-stu-id="38ed6-110">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
- <span data-ttu-id="38ed6-111">Jsou stručnější a čitelné, zejména při filtrování více podmínek.</span><span class="sxs-lookup"><span data-stu-id="38ed6-111">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
- <span data-ttu-id="38ed6-112">Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="38ed6-112">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
- <span data-ttu-id="38ed6-113">Je možné je přenést do jiných zdrojů dat s minimální nebo žádnou úpravou.</span><span class="sxs-lookup"><span data-stu-id="38ed6-113">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="38ed6-114">Obecně komplexnější operace, kterou chcete provést na datech, je větší výhodou použití LINQ namísto tradičních technik iterací.</span><span class="sxs-lookup"><span data-stu-id="38ed6-114">In general, the more complex the operation you want to perform on the data, the more benefit you'll realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="38ed6-115">Účelem této části je Ukázat přístup LINQ s některými příklady výběru.</span><span class="sxs-lookup"><span data-stu-id="38ed6-115">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="38ed6-116">Není určeno jako vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="38ed6-116">It's not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38ed6-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="38ed6-117">In This Section</span></span>  
 [<span data-ttu-id="38ed6-118">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="38ed6-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="38ed6-119">Vysvětluje, jak lze LINQ použít k dotazování a transformaci řetězců a kolekcí řetězců.</span><span class="sxs-lookup"><span data-stu-id="38ed6-119">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="38ed6-120">Obsahuje také odkazy na články, které ukazují tyto principy.</span><span class="sxs-lookup"><span data-stu-id="38ed6-120">Also includes links to articles that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="38ed6-121">LINQ a reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="38ed6-121">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="38ed6-122">Odkazuje na ukázku, která ukazuje, jak LINQ používá reflexi.</span><span class="sxs-lookup"><span data-stu-id="38ed6-122">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="38ed6-123">LINQ a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="38ed6-123">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="38ed6-124">Vysvětluje, jak lze pomocí technologie LINQ pracovat se systémy souborů.</span><span class="sxs-lookup"><span data-stu-id="38ed6-124">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="38ed6-125">Obsahuje také odkazy na články, které ukazují tyto koncepty.</span><span class="sxs-lookup"><span data-stu-id="38ed6-125">Also includes links to articles that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="38ed6-126">Postup dotazování objektu ArrayList pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="38ed6-126">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="38ed6-127">Ukazuje, jak se dotázat na objekt ArrayList v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="38ed6-127">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="38ed6-128">Postup přidání vlastních metod pro dotazy LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="38ed6-128">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="38ed6-129">Vysvětluje, jak rozšířit sadu metod, které lze použít pro dotazy LINQ přidáním rozšiřujících metod do <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38ed6-129">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="38ed6-130">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="38ed6-130">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="38ed6-131">Obsahuje odkazy na články, které vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.</span><span class="sxs-lookup"><span data-stu-id="38ed6-131">Provides links to articles that explain LINQ and provide examples of code that perform queries.</span></span>
