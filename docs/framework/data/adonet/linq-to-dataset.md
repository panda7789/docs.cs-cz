---
title: LINQ na DataSet
ms.date: 03/30/2017
ms.assetid: 743e3755-3ecb-45a2-8d9b-9ed41f0dcf17
ms.openlocfilehash: 4995512336ee9eb6e33df011757ed533db57e76e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783785"
---
# <a name="linq-to-dataset"></a><span data-ttu-id="2b2ad-102">LINQ na DataSet</span><span class="sxs-lookup"><span data-stu-id="2b2ad-102">LINQ to DataSet</span></span>
<span data-ttu-id="2b2ad-103">LINQ to DataSet usnadňuje a urychlují dotazování na data uložená v <xref:System.Data.DataSet> objektu.</span><span class="sxs-lookup"><span data-stu-id="2b2ad-103">LINQ to DataSet makes it easier and faster to query over data cached in a <xref:System.Data.DataSet> object.</span></span> <span data-ttu-id="2b2ad-104">Konkrétně LINQ to DataSet zjednodušuje dotazování tím, že vývojářům umožňuje psát dotazy z samotného programovacího jazyka namísto použití samostatného dotazovacího jazyka.</span><span class="sxs-lookup"><span data-stu-id="2b2ad-104">Specifically, LINQ to DataSet simplifies querying by enabling developers to write queries from the programming language itself, instead of by using a separate query language.</span></span> <span data-ttu-id="2b2ad-105">To je užitečné hlavně pro vývojáře v aplikaci Visual Studio, kteří nyní mohou využít kontrolu syntaxe při kompilaci, statického typování a podporu technologie IntelliSense, kterou poskytuje Visual Studio ve svých dotazech.</span><span class="sxs-lookup"><span data-stu-id="2b2ad-105">This is especially useful for Visual Studio developers, who can now take advantage of the compile-time syntax checking, static typing, and IntelliSense support provided by the Visual Studio in their queries.</span></span>  
  
 <span data-ttu-id="2b2ad-106">LINQ to DataSet lze také použít k dotazování na data, která byla konsolidována z jednoho nebo více zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="2b2ad-106">LINQ to DataSet can also be used to query over data that has been consolidated from one or more data sources.</span></span> <span data-ttu-id="2b2ad-107">Díky tomu je možné mnoha scénářů, které vyžadují flexibilitu při reprezentaci a zpracování dat, jako je dotazování na místně agregovaná data a ukládání do střední vrstvy ve webových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="2b2ad-107">This enables many scenarios that require flexibility in how data is represented and handled, such as querying locally aggregated data and middle-tier caching in Web applications.</span></span> <span data-ttu-id="2b2ad-108">Tato metoda manipulace vyžaduje zejména obecné vytváření sestav, analýzy a business intelligence aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b2ad-108">In particular, generic reporting, analysis, and business intelligence applications require this method of manipulation.</span></span>  
  
 <span data-ttu-id="2b2ad-109">Funkce LINQ to DataSet je vystavena hlavně prostřednictvím rozšiřujících metod v <xref:System.Data.DataRowExtensions> třídách a. <xref:System.Data.DataTableExtensions></span><span class="sxs-lookup"><span data-stu-id="2b2ad-109">The LINQ to DataSet functionality is exposed primarily through the extension methods in the <xref:System.Data.DataRowExtensions> and <xref:System.Data.DataTableExtensions> classes.</span></span> <span data-ttu-id="2b2ad-110">LINQ to DataSet vytváří a používá stávající architekturu ADO.NET a není určena k nahrazení ADO.NET v kódu aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b2ad-110">LINQ to DataSet builds on and uses the existing ADO.NET architecture, and is not meant to replace ADO.NET in application code.</span></span> <span data-ttu-id="2b2ad-111">Existující kód ADO.NET bude nadále fungovat v aplikaci LINQ to DataSet.</span><span class="sxs-lookup"><span data-stu-id="2b2ad-111">Existing ADO.NET code will continue to function in a LINQ to DataSet application.</span></span> <span data-ttu-id="2b2ad-112">V následujícím diagramu je znázorněn vztah LINQ to DataSet k ADO.NET a úložiště dat.</span><span class="sxs-lookup"><span data-stu-id="2b2ad-112">The relationship of LINQ to DataSet to ADO.NET and the data store is illustrated in the following diagram.</span></span>  
  
 ![Diagram znázorňující, že LINQ to DataSet je založen na poskytovateli ADO.NET.](./media/linq-to-dataset/linq-dataset-ado-dotnet-provider.gif)  
  
## <a name="in-this-section"></a><span data-ttu-id="2b2ad-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2b2ad-114">In This Section</span></span>  
 [<span data-ttu-id="2b2ad-115">Začínáme</span><span class="sxs-lookup"><span data-stu-id="2b2ad-115">Getting Started</span></span>](getting-started-linq-to-dataset.md)  
  
 [<span data-ttu-id="2b2ad-116">Průvodce programováním</span><span class="sxs-lookup"><span data-stu-id="2b2ad-116">Programming Guide</span></span>](programming-guide-linq-to-dataset.md)  
  
## <a name="reference"></a><span data-ttu-id="2b2ad-117">Reference</span><span class="sxs-lookup"><span data-stu-id="2b2ad-117">Reference</span></span>  
 <xref:System.Data.DataTableExtensions>  
  
 <xref:System.Data.DataRowExtensions>  
  
 <xref:System.Data.DataRowComparer>  
  
## <a name="see-also"></a><span data-ttu-id="2b2ad-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b2ad-118">See also</span></span>

- [<span data-ttu-id="2b2ad-119">LINQ (Language-Integrated Query) –C#</span><span class="sxs-lookup"><span data-stu-id="2b2ad-119">Language-Integrated Query (LINQ) - C#</span></span>](../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="2b2ad-120">LINQ (Language-Integrated Query) – Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b2ad-120">Language-Integrated Query (LINQ) - Visual Basic</span></span>](../../../visual-basic/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="2b2ad-121">LINQ a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2b2ad-121">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)
- [<span data-ttu-id="2b2ad-122">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2b2ad-122">ADO.NET</span></span>](index.md)
