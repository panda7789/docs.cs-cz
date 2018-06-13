---
title: Úvod do LINQ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: 371801e1730c578b039adb6a88bd0bcdfd186db7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644859"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="ab609-102">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab609-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="ab609-103">Language-Integrated Query (LINQ) je že novinka zavedená v rozhraní .NET Framework verze 3.5 obsahující mezery mezi world objektů a dat na světě.</span><span class="sxs-lookup"><span data-stu-id="ab609-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="ab609-104">Dotazy na data jsou tradičně, vyjádřené jako jednoduchý řetězce bez kontrolu typu v kompilaci čas nebo podporu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ab609-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="ab609-105">Kromě toho budete muset další různých dotazovací jazyk pro každý typ zdroje dat: SQL databáze, dokumentů XML, různé webové služby a tak dále.</span><span class="sxs-lookup"><span data-stu-id="ab609-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="ab609-106">Díky LINQ *dotazu* prvotřídní jazyk konstrukce v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ab609-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="ab609-107">Můžete psát dotazy proti silného typu kolekce objektů pomocí známých operátory a klíčová slova jazyka.</span><span class="sxs-lookup"><span data-stu-id="ab609-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="ab609-108">Můžete napsat dotazy LINQ v jazyku Visual Basic pro databáze systému SQL Server, dokumentů XML, datové sady ADO.NET a kolekci objektů, který podporuje <xref:System.Collections.IEnumerable> nebo obecná <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ab609-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="ab609-109">Podpora LINQ jsou tu taky třetích stran pro mnoho webové služby a jiné implementace databáze.</span><span class="sxs-lookup"><span data-stu-id="ab609-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="ab609-110">Můžete dotazů LINQ v nové projekty nebo spolu s bez LINQ dotazů v existující projekty.</span><span class="sxs-lookup"><span data-stu-id="ab609-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="ab609-111">Jediným požadavkem je, že projekt cílí na rozhraní .NET Framework 3.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="ab609-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="ab609-112">Na následujícím obrázku ze sady Visual Studio ukazuje dotaz LINQ částečně dokončilo proti databázi systému SQL Server v jak C# a Visual Basic s Kontrola úplné typu a podporu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ab609-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="ab609-113">![Dotaz LINQ pomocí Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="ab609-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ab609-114">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ab609-114">Next Steps</span></span>  
 <span data-ttu-id="ab609-115">Další podrobnosti o LINQ, spusťte Seznamte se s některé základní pojmy v části Začínáme [Začínáme s dotazy LINQ v jazyku Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), a potom si přečtěte dokumentace pro technologie LINQ, ve kterém jsou zájmu:</span><span class="sxs-lookup"><span data-stu-id="ab609-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="ab609-116">Databáze systému SQL Server: [technologie LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="ab609-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="ab609-117">Dokumenty XML: [technologie LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="ab609-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="ab609-118">Datové sady ADO.NET: [LINQ na DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="ab609-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="ab609-119">Kolekcí .NET, soubory, a tak dále řetězce: [LINQ na objekty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="ab609-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab609-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab609-120">See Also</span></span>  
 [<span data-ttu-id="ab609-121">Language-Integrated Query (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab609-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
