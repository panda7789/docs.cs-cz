---
title: Úvod do LINQ (C#)
ms.date: 07/20/2015
ms.assetid: 54874feb-55e5-4ca8-a9d6-1c1127fd7fb1
ms.openlocfilehash: 990a47d6ecfe38d9efa7d505eb3c23a28c05f58c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740244"
---
# <a name="introduction-to-linq-c"></a><span data-ttu-id="5893a-102">Úvod do LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="5893a-102">Introduction to LINQ (C#)</span></span>
<span data-ttu-id="5893a-103">Language Integrated Query (LINQ) je že novinka zavedena v rozhraní .NET Framework verze 3.5 této přemostění mezery mezi řadě objekty a světě orientovaném na data.</span><span class="sxs-lookup"><span data-stu-id="5893a-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="5893a-104">Tradičně dotazů na data jsou vyjádřené jako jednoduchý řetězce bez kontrolu typu v kompilaci čas nebo podporu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5893a-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="5893a-105">Kromě toho budete muset učit jazyk dotazu pro každý typ zdroje dat: SQL databáze, dokumenty XML, různé webové služby a tak dále.</span><span class="sxs-lookup"><span data-stu-id="5893a-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="5893a-106">Díky LINQ *dotazu* typů prvotřídní jazykové konstrukce v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="5893a-106">LINQ makes a *query* a first-class language construct in C#.</span></span> <span data-ttu-id="5893a-107">Psát dotazy proti silně typované kolekce objektů s použitím známých operátory a klíčová slova jazyka.</span><span class="sxs-lookup"><span data-stu-id="5893a-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="5893a-108">Můžete zápis dotazů LINQ v jazyce C# pro databáze serveru SQL Server, dokumenty XML, datovými sadami ADO.NET a kolekce objektů, který podporuje <xref:System.Collections.IEnumerable> nebo Obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5893a-108">You can write LINQ queries in C# for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="5893a-109">Podpora LINQ se také poskytuje třetími stranami pro mnoho webových služeb a jiné implementace databáze.</span><span class="sxs-lookup"><span data-stu-id="5893a-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="5893a-110">V nových projektech, nebo spolu s jiný než LINQ dotazy v existujících projektů můžete použít dotazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="5893a-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="5893a-111">Jediným požadavkem je, že projekt cílit na rozhraní .NET Framework 3.5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="5893a-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="5893a-112">Na následujícím obrázku ze sady Visual Studio zobrazuje částečně dokončeno LINQ dotaz na databázi systému SQL Server v jazyce C# a Visual Basic s úplným typem kontrolu a podporu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5893a-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 <span data-ttu-id="5893a-113">![Dotaz LINQ s podporou technologie Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span><span class="sxs-lookup"><span data-stu-id="5893a-113">![LINQ query with Intellisense](../../../../csharp/programming-guide/concepts/linq/media/query_intell.png "Query_Intell")</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5893a-114">Další kroky</span><span class="sxs-lookup"><span data-stu-id="5893a-114">Next Steps</span></span>  
 <span data-ttu-id="5893a-115">Další informace o dotazech technologie LINQ, začněte tím, že se seznamovat s některé základní pojmy v části Začínáme [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), a pak si můžete přečíst dokumentaci k technologie LINQ, který vás zajímá:</span><span class="sxs-lookup"><span data-stu-id="5893a-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
-   <span data-ttu-id="5893a-116">Databáze systému SQL Server: [technologie LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="5893a-116">SQL Server databases: [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)</span></span>  
  
-   <span data-ttu-id="5893a-117">Dokumenty XML: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="5893a-117">XML documents: [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
-   <span data-ttu-id="5893a-118">Datové sady ADO.NET: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="5893a-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
-   <span data-ttu-id="5893a-119">Kolekce .NET, soubory, řetězce a tak dále: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="5893a-119">.NET collections, files, strings and so on: [LINQ to Objects (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5893a-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5893a-120">See Also</span></span>

- [<span data-ttu-id="5893a-121">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5893a-121">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
