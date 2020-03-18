---
title: LINQ na objekty (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344785"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="adb1d-102">LINQ na objekty (C#)</span><span class="sxs-lookup"><span data-stu-id="adb1d-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="adb1d-103">Termín "LINQ na objekty" odkazuje na použití linq <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> dotazy s any nebo kolekce přímo, bez použití zprostředkovatele zprostředkující LINQ nebo rozhraní API, jako je [LINQ na SQL](../../../../framework/data/adonet/sql/linq/index.md) nebo [LINQ na XML](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="adb1d-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="adb1d-104">Linq můžete použít k dotazování libovolných <xref:System.Collections.Generic.List%601>nesčetných kolekcí, jako jsou , <xref:System.Array>nebo <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="adb1d-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="adb1d-105">Kolekce může být definována uživatelem nebo může být vrácena rozhraním .NET Framework API.</span><span class="sxs-lookup"><span data-stu-id="adb1d-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="adb1d-106">V základním smyslu LINQ to Objects představuje nový přístup ke kolekcím.</span><span class="sxs-lookup"><span data-stu-id="adb1d-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="adb1d-107">Starým způsobem jste museli napsat `foreach` složité smyčky, které specifikovaly, jak načíst data z kolekce.</span><span class="sxs-lookup"><span data-stu-id="adb1d-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="adb1d-108">V přístupu LINQ napíšete deklarativní kód, který popisuje, co chcete načíst.</span><span class="sxs-lookup"><span data-stu-id="adb1d-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="adb1d-109">Kromě toho linq dotazy nabízejí tři `foreach` hlavní výhody oproti tradičním smyčkám:</span><span class="sxs-lookup"><span data-stu-id="adb1d-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="adb1d-110">Jsou stručnější a čitelnější, zejména při filtrování více podmínek.</span><span class="sxs-lookup"><span data-stu-id="adb1d-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="adb1d-111">Poskytují výkonné možnosti filtrování, řazení a seskupování s minimem kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="adb1d-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="adb1d-112">Mohou být přeneseny do jiných zdrojů dat s malou nebo žádnou změnou.</span><span class="sxs-lookup"><span data-stu-id="adb1d-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="adb1d-113">Obecně platí, že složitější operace, kterou chcete provést s daty, tím větší výhodu získáte pomocí LINQ namísto tradičních iterace.</span><span class="sxs-lookup"><span data-stu-id="adb1d-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="adb1d-114">Účelem této části je demonstrovat přístup LINQ s některými vybranými příklady.</span><span class="sxs-lookup"><span data-stu-id="adb1d-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="adb1d-115">Nemá být vyčerpávající.</span><span class="sxs-lookup"><span data-stu-id="adb1d-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="adb1d-116">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="adb1d-116">In This Section</span></span>  
 [<span data-ttu-id="adb1d-117">LINQ a řetězce (C#)</span><span class="sxs-lookup"><span data-stu-id="adb1d-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="adb1d-118">Vysvětluje, jak LINQ lze použít k dotazování a transformaci řetězce a kolekce řetězců.</span><span class="sxs-lookup"><span data-stu-id="adb1d-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="adb1d-119">Obsahuje také odkazy na témata, která tyto zásady demonstrují.</span><span class="sxs-lookup"><span data-stu-id="adb1d-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="adb1d-120">LINQ a reflexe (C#)</span><span class="sxs-lookup"><span data-stu-id="adb1d-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="adb1d-121">Odkazy na ukázku, která ukazuje, jak LINQ používá reflexe.</span><span class="sxs-lookup"><span data-stu-id="adb1d-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="adb1d-122">Linq a souborové adresáře (C#)</span><span class="sxs-lookup"><span data-stu-id="adb1d-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="adb1d-123">Vysvětluje, jak linq lze použít k interakci se systémy souborů.</span><span class="sxs-lookup"><span data-stu-id="adb1d-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="adb1d-124">Obsahuje také odkazy na témata, která tyto koncepty demonstrují.</span><span class="sxs-lookup"><span data-stu-id="adb1d-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="adb1d-125">Jak dotaz ArrayList s LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="adb1d-125">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="adb1d-126">Ukazuje, jak dotaz ArrayList v C#.</span><span class="sxs-lookup"><span data-stu-id="adb1d-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="adb1d-127">Jak přidat vlastní metody pro dotazy LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="adb1d-127">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="adb1d-128">Vysvětluje, jak rozšířit sadu metod, které můžete použít pro dotazy LINQ <xref:System.Collections.Generic.IEnumerable%601> přidáním metody rozšíření do rozhraní.</span><span class="sxs-lookup"><span data-stu-id="adb1d-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="adb1d-129">Dotaz integrovaný jazykem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="adb1d-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="adb1d-130">Obsahuje odkazy na témata, která vysvětlují LINQ a poskytují příklady kódu, který provádí dotazy.</span><span class="sxs-lookup"><span data-stu-id="adb1d-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
