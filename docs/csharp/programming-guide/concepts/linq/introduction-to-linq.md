---
title: Úvod do LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: 3c32c20efec55568a668c5dba55baf8f3ebbee7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33323313"
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="c1e86-102">Úvod do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="c1e86-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="c1e86-103">Language-Integrated Query (LINQ) je že novinka zavedená v rozhraní .NET Framework verze 3.5 obsahující mezery mezi world objektů a dat na světě.</span><span class="sxs-lookup"><span data-stu-id="c1e86-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="c1e86-104">Dotazy na data jsou tradičně, vyjádřené jako jednoduchý řetězce bez kontrolu typu v kompilaci čas nebo podporu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c1e86-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="c1e86-105">Kromě toho budete muset další různých dotazovací jazyk pro každý typ zdroje dat: SQL databáze, dokumentů XML, různé webové služby a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c1e86-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="c1e86-106">Díky LINQ *dotazu* prvotřídní jazyk konstrukce v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="c1e86-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="c1e86-107">Můžete psát dotazy proti silného typu kolekce objektů pomocí známých operátory a klíčová slova jazyka.</span><span class="sxs-lookup"><span data-stu-id="c1e86-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="c1e86-108">Můžete zápis dotazů LINQ v C# pro databáze systému SQL Server, dokumentů XML, datové sady ADO.NET a kolekci objektů, který podporuje <xref:System.Collections.IEnumerable> nebo obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c1e86-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="c1e86-109">Podpora LINQ jsou tu taky třetích stran pro mnoho webové služby a jiné implementace databáze.</span><span class="sxs-lookup"><span data-stu-id="c1e86-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="c1e86-110">Můžete dotazů LINQ v nové projekty nebo spolu s bez LINQ dotazů v existující projekty.</span><span class="sxs-lookup"><span data-stu-id="c1e86-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="c1e86-111">Jediným požadavkem je, že projekt cílí na rozhraní .NET Framework 3.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="c1e86-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="c1e86-112">Na následujícím obrázku ze sady Visual Studio ukazuje dotaz LINQ částečně dokončilo proti databázi systému SQL Server v jak C# a Visual Basic s Kontrola úplné typu a podporu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c1e86-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="c1e86-113">![Dotaz LINQ pomocí Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="c1e86-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c1e86-114">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c1e86-114">Next Steps</span></span>  
 <span data-ttu-id="c1e86-115">Další podrobnosti o LINQ, spusťte Seznamte se s některé základní pojmy v části Začínáme [Začínáme s dotazy LINQ v jazyku C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), a přečtěte si dokumentaci pro LINQ technologii, která vás zajímá:</span><span class="sxs-lookup"><span data-stu-id="c1e86-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="c1e86-116">Databáze systému SQL Server: [technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="c1e86-116">SQL Server databases: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="c1e86-117">Dokumenty XML: [technologie LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="c1e86-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="c1e86-118">Datové sady ADO.NET: [LINQ na DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="c1e86-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="c1e86-119">Kolekcí .NET, soubory, a tak dále řetězce: [LINQ na objekty (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="c1e86-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e86-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1e86-120">See Also</span></span>  
 [<span data-ttu-id="c1e86-121">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="c1e86-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
