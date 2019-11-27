---
title: Úvod do LINQ
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: add442583bd81665533b704c0c9721b111cddd78
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74338907"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="c61e3-102">Úvod do LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c61e3-102">Introduction to LINQ (Visual Basic)</span></span>
<span data-ttu-id="c61e3-103">LINQ (Language-Integrated Query) je inovace představené ve verzi .NET Framework 3,5, která přemostěníuje mezeru mezi světem objektů a světem dat.</span><span class="sxs-lookup"><span data-stu-id="c61e3-103">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="c61e3-104">Tradičně se dotazy na data vyjadřují jako jednoduché řetězce bez kontroly typu v době kompilace nebo v podpoře technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c61e3-104">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="c61e3-105">Kromě toho se musíte naučit jiný dotazovací jazyk pro každý typ zdroje dat: databáze SQL, dokumenty XML, různé webové služby a tak dále.</span><span class="sxs-lookup"><span data-stu-id="c61e3-105">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="c61e3-106">LINQ vytvoří *dotaz* na konstrukci jazyka první třídy v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="c61e3-106">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="c61e3-107">Zapisujete dotazy na kolekce objektů se silnými typy pomocí klíčových slov jazyka a známých operátorů.</span><span class="sxs-lookup"><span data-stu-id="c61e3-107">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="c61e3-108">Dotazy LINQ můžete zapsat v Visual Basic pro databáze SQL Server, dokumenty XML, datové sady ADO.NET a všechny kolekce objektů, které podporují <xref:System.Collections.IEnumerable> nebo obecné rozhraní <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="c61e3-108">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="c61e3-109">Podporu LINQ poskytují i třetí strany pro mnoho webových služeb a dalších implementací databáze.</span><span class="sxs-lookup"><span data-stu-id="c61e3-109">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="c61e3-110">Dotazy LINQ můžete použít v nových projektech nebo společně s dotazy mimo LINQ v existujících projektech.</span><span class="sxs-lookup"><span data-stu-id="c61e3-110">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="c61e3-111">Jediným požadavkem je, že cíl projektu .NET Framework 3,5 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="c61e3-111">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="c61e3-112">Následující obrázek ze sady Visual Studio ukazuje částečně dokončený dotaz LINQ na SQL Server databázi v Visual Basic C# a s úplnou kontrolou typu a podporou technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="c61e3-112">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![Diagram, který zobrazuje dotaz LINQ pomocí technologie IntelliSense.](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="c61e3-114">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c61e3-114">Next Steps</span></span>  
 <span data-ttu-id="c61e3-115">Chcete-li získat další informace o LINQ, začněte tím, že se seznámíte s některými základními koncepty v sekci Začínáme [Začínáme pomocí LINQ v Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)a pak si přečtěte dokumentaci pro technologii LINQ, ve které máte zájem:</span><span class="sxs-lookup"><span data-stu-id="c61e3-115">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="c61e3-116">SQL Server databáze: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="c61e3-116">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="c61e3-117">Dokumenty XML: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="c61e3-117">XML documents: [LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)</span></span>  
  
- <span data-ttu-id="c61e3-118">ADO.NET datové sady: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="c61e3-118">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="c61e3-119">Kolekce .NET, soubory, řetězce a tak dále: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="c61e3-119">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c61e3-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c61e3-120">See also</span></span>

- [<span data-ttu-id="c61e3-121">LINQ (Language-Integrated Query) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c61e3-121">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)
