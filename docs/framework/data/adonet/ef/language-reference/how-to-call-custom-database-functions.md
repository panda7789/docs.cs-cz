---
title: "Postupy: volání funkce vlastní databáze"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2aab11481bb23228f9ad920c5d01ef7d345e05d3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="02bc0-102">Postupy: volání funkce vlastní databáze</span><span class="sxs-lookup"><span data-stu-id="02bc0-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="02bc0-103">Toto téma popisuje, jak volat vlastní funkce, které jsou definovány v databázi z v rámci LINQ dotazy entity.</span><span class="sxs-lookup"><span data-stu-id="02bc0-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="02bc0-104">Funkce databáze, které se nazývají z technologie LINQ na entity dotazy jsou spouštěny v databázi.</span><span class="sxs-lookup"><span data-stu-id="02bc0-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="02bc0-105">Provádění funkcí v databázi může zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="02bc0-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="02bc0-106">Následující postup obsahovala hrubý nástin pro volání funkce vlastní databázi.</span><span class="sxs-lookup"><span data-stu-id="02bc0-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="02bc0-107">Příklad, který následuje obsahuje více podrobností o kroků v postupu.</span><span class="sxs-lookup"><span data-stu-id="02bc0-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="02bc0-108">K volání vlastní funkce, které jsou definovány v databázi</span><span class="sxs-lookup"><span data-stu-id="02bc0-108">To call custom functions that are defined in the database</span></span>  
  
1.  <span data-ttu-id="02bc0-109">Vytvoření vlastní funkce ve vaší databázi.</span><span class="sxs-lookup"><span data-stu-id="02bc0-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="02bc0-110">Další informace o vytvoření vlastní funkce v systému SQL Server najdete v tématu [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="02bc0-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](http://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2.  <span data-ttu-id="02bc0-111">Funkce v jazyce definici schématu (SSDL) úložiště souboru .edmx deklarujte.</span><span class="sxs-lookup"><span data-stu-id="02bc0-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="02bc0-112">Název funkce musí být stejný jako název funkce deklarované v databázi.</span><span class="sxs-lookup"><span data-stu-id="02bc0-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="02bc0-113">Další informace najdete v tématu [funkce elementu (SSDL)](http://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).</span><span class="sxs-lookup"><span data-stu-id="02bc0-113">For more information, see [Function Element (SSDL)](http://msdn.microsoft.com/library/b60cfc3d-8b93-423e-8c99-b867256640a4).</span></span>  
  
3.  <span data-ttu-id="02bc0-114">Přidat odpovídající metodu do třídy v kódu aplikace a aplikovat <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metodě Všimněte si, že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu jsou název oboru názvů konceptuálního modelu a název funkce v konceptuálním model v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="02bc0-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="02bc0-115">Funkce překladu názvů u LINQ je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="02bc0-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4.  <span data-ttu-id="02bc0-116">Volání metody v dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="02bc0-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02bc0-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="02bc0-117">Example</span></span>  
 <span data-ttu-id="02bc0-118">Následující příklad ukazuje, jak volat funkci vlastní databázi z v rámci LINQ entity dotazu.</span><span class="sxs-lookup"><span data-stu-id="02bc0-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="02bc0-119">V příkladu školní modelu.</span><span class="sxs-lookup"><span data-stu-id="02bc0-119">The example uses the School model.</span></span> <span data-ttu-id="02bc0-120">Informace o modelu školní najdete v tématu [vytváření ukázkovou databázi školy](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) a [generování školní .edmx souboru](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="02bc0-120">For information about the School model, see [Creating the School Sample Database](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="02bc0-121">Následující kód přidá `AvgStudentGrade` funkce ukázkovou databázi školy.</span><span class="sxs-lookup"><span data-stu-id="02bc0-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02bc0-122">Postup pro volání funkce vlastní databáze je stejný bez ohledu na serveru databáze.</span><span class="sxs-lookup"><span data-stu-id="02bc0-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="02bc0-123">Následující kód je však specifické pro vytvoření funkce v databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="02bc0-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="02bc0-124">Kód pro vytvoření vlastní funkce v jiných databázových serverů se můžou lišit.</span><span class="sxs-lookup"><span data-stu-id="02bc0-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="02bc0-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="02bc0-125">Example</span></span>  
 <span data-ttu-id="02bc0-126">V dalším kroku deklarujte funkce v jazyce definici schématu (SSDL) úložiště souboru .edmx.</span><span class="sxs-lookup"><span data-stu-id="02bc0-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="02bc0-127">Následující kód deklaruje `AvgStudentGrade` funkce v SSDL:</span><span class="sxs-lookup"><span data-stu-id="02bc0-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="02bc0-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="02bc0-128">Example</span></span>  
 <span data-ttu-id="02bc0-129">Teď vytvořte metodu a namapovat je funkce deklarované v SSDL.</span><span class="sxs-lookup"><span data-stu-id="02bc0-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="02bc0-130">Metoda v následující třídy je namapovaná na funkci definovanou v SSDL (výše) pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="02bc0-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="02bc0-131">Pokud tato metoda je volána, je spustit odpovídající funkce v databázi.</span><span class="sxs-lookup"><span data-stu-id="02bc0-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="02bc0-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="02bc0-132">Example</span></span>  
 <span data-ttu-id="02bc0-133">Nakonec volejte metodu v dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="02bc0-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="02bc0-134">Následující kód zobrazí studentů příjmení a průměrná tříd do konzoly:</span><span class="sxs-lookup"><span data-stu-id="02bc0-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="02bc0-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="02bc0-135">See Also</span></span>  
 [<span data-ttu-id="02bc0-136">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="02bc0-136">.edmx File Overview</span></span>](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="02bc0-137">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="02bc0-137">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
