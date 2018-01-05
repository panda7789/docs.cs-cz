---
title: System.TimeSpan metody
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 257fff19d10c4b803ec6fc539087cc558bd07a0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemtimespan-methods"></a><span data-ttu-id="33160-102">System.TimeSpan metody</span><span class="sxs-lookup"><span data-stu-id="33160-102">System.TimeSpan Methods</span></span>
<span data-ttu-id="33160-103">Podpora člen <xref:System.TimeSpan?displayProperty=nameWithType> výrazně závisí na verze rozhraní .NET Framework a Microsoft SQL Server, který používáte.</span><span class="sxs-lookup"><span data-stu-id="33160-103">Member support for <xref:System.TimeSpan?displayProperty=nameWithType> greatly depends on the versions of the .NET Framework and Microsoft SQL Server that you are using.</span></span>  
  
 <span data-ttu-id="33160-104">Když metoda, operátor nebo vlastnost není podporována; znamená to, že technologie LINQ to SQL nemůže překládat člena pro spuštění systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="33160-104">When a method, operator, or property is unsupported; it means that LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="33160-105">Může být stále moct používat tyto členy ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="33160-105">You may still be able to use these members in your code.</span></span> <span data-ttu-id="33160-106">Ale že musí být vyhodnocena před dotaz převádějí do jazyka Transact-SQL nebo po výsledky byly získány z databáze.</span><span class="sxs-lookup"><span data-stu-id="33160-106">However, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="previous-limitations"></a><span data-ttu-id="33160-107">Předchozí omezení</span><span class="sxs-lookup"><span data-stu-id="33160-107">Previous Limitations</span></span>  
 <span data-ttu-id="33160-108">Při použití technologie LINQ to SQL s verze rozhraní .NET Framework před rozhraní .NET Framework 3.5 SP1, nelze mapovat pole databáze systému SQL Server k <xref:System.TimeSpan?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="33160-108">When using LINQ to SQL with versions of the .NET Framework prior to .NET Framework 3.5 SP1, you cannot map SQL Server database fields to <xref:System.TimeSpan?displayProperty=nameWithType>.</span></span> <span data-ttu-id="33160-109">Ale operací na <xref:System.TimeSpan> jsou podporována, protože <xref:System.TimeSpan> hodnoty lze vrátit ze <xref:System.DateTime> odčítání nebo zasaženo výraz jako literál nebo vázané proměnnou.</span><span class="sxs-lookup"><span data-stu-id="33160-109">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
## <a name="supported-systemtimespan-method-support"></a><span data-ttu-id="33160-110">Podporovanou metodou System.TimeSpan podpory</span><span class="sxs-lookup"><span data-stu-id="33160-110">Supported System.TimeSpan Method Support</span></span>  
 <span data-ttu-id="33160-111">Následující technologie LINQ to SQL podporované metody, operátory a vlastnosti jsou k dispozici pro použití v vaše dotazy LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="33160-111">The following LINQ to SQL-supported methods, operators, and properties are available for you to use in your LINQ to SQL queries.</span></span> <span data-ttu-id="33160-112">Jakmile namapovány v modelu objektu nebo externí mapování souboru, technologie LINQ to SQL umožňuje volat řadu <xref:System.TimeSpan?displayProperty=nameWithType> členy uvnitř vaší dotazy LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="33160-112">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call many of the <xref:System.TimeSpan?displayProperty=nameWithType> members inside your LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="33160-113">Podporované <xref:System.TimeSpan> metody</span><span class="sxs-lookup"><span data-stu-id="33160-113">Supported <xref:System.TimeSpan> Methods</span></span>|<span data-ttu-id="33160-114">Podporované <xref:System.TimeSpan> operátory</span><span class="sxs-lookup"><span data-stu-id="33160-114">Supported <xref:System.TimeSpan> Operators</span></span>|<span data-ttu-id="33160-115">Podporované <xref:System.TimeSpan> vlastnosti</span><span class="sxs-lookup"><span data-stu-id="33160-115">Supported <xref:System.TimeSpan> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<!--zz <xref:System.TimeSpan.MinValue%2A>-->|  
  
> [!NOTE]
>  <span data-ttu-id="33160-116">Možnost mapovat <xref:System.TimeSpan?displayProperty=nameWithType> SQL `TIME` sloupec s technologie LINQ to SQL vyžaduje rozhraní .NET Framework 3.5 SP1 a dále.</span><span class="sxs-lookup"><span data-stu-id="33160-116">The ability to map <xref:System.TimeSpan?displayProperty=nameWithType> to a SQL `TIME` column with LINQ to SQL requires the .NET Framework 3.5 SP1 and beyond.</span></span> <span data-ttu-id="33160-117">SQL `TIME` datový typ je k dispozici v systému Microsoft SQL Server 2008 a nad rámec.</span><span class="sxs-lookup"><span data-stu-id="33160-117">The SQL `TIME` data type is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
### <a name="addition-and-subtraction"></a><span data-ttu-id="33160-118">Sčítání a odečítání</span><span class="sxs-lookup"><span data-stu-id="33160-118">Addition and Subtraction</span></span>  
 <span data-ttu-id="33160-119">I když modulu CLR <xref:System.TimeSpan?displayProperty=nameWithType> typu podporuje sčítání a odečítání SQL `TIME` typ neexistuje.</span><span class="sxs-lookup"><span data-stu-id="33160-119">Although the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type does support addition and subtraction, the SQL `TIME` type does not.</span></span> <span data-ttu-id="33160-120">Z toho důvodu vaše dotazy LINQ to SQL vygeneruje chyby, pokud pokoušejí sčítání a odečítání, když jsou namapované na SQL `TIME` typu.</span><span class="sxs-lookup"><span data-stu-id="33160-120">Because of this, your LINQ to SQL queries will generate errors if they attempt addition and subtraction when they are mapped to the SQL `TIME` type.</span></span> <span data-ttu-id="33160-121">Můžete najít další důležité informace pro práci s typy SQL data a času v [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="33160-121">You can find other considerations for working with SQL date and time types in [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33160-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="33160-122">See Also</span></span>  
 [<span data-ttu-id="33160-123">Koncepty dotazů</span><span class="sxs-lookup"><span data-stu-id="33160-123">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="33160-124">Vytvoření objektového modelu</span><span class="sxs-lookup"><span data-stu-id="33160-124">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="33160-125">Mapování typů SQL a CLR</span><span class="sxs-lookup"><span data-stu-id="33160-125">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="33160-126">Datové typy a funkce</span><span class="sxs-lookup"><span data-stu-id="33160-126">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
