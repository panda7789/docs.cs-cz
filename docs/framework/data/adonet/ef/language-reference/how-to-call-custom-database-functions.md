---
title: 'Postupy: Volání vlastních databázových funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: cc2e25183649f6a95e7862520ccc5719f201277a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774644"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="e10f9-102">Postupy: Volání vlastních databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="e10f9-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="e10f9-103">Toto téma popisuje, jak zavolat vlastní funkce, které jsou definovány v databázi z v rámci LINQ dotazy na entity.</span><span class="sxs-lookup"><span data-stu-id="e10f9-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="e10f9-104">Databázové funkce, které se volají z LINQ na dotazy na entity jsou provedeny v databázi.</span><span class="sxs-lookup"><span data-stu-id="e10f9-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="e10f9-105">Provádění funkcí v databázi může zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="e10f9-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="e10f9-106">Následující postup obsahovala hrubý nástin pro volání funkce vlastní databázi.</span><span class="sxs-lookup"><span data-stu-id="e10f9-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="e10f9-107">Následující příklad obsahuje více podrobností o kroků v postupu.</span><span class="sxs-lookup"><span data-stu-id="e10f9-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="e10f9-108">K volání vlastní funkce, které jsou definovány v databázi</span><span class="sxs-lookup"><span data-stu-id="e10f9-108">To call custom functions that are defined in the database</span></span>  
  
1. <span data-ttu-id="e10f9-109">Vytvoření vlastní funkce ve vaší databázi.</span><span class="sxs-lookup"><span data-stu-id="e10f9-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="e10f9-110">Další informace o vytváření vlastních funkcí v systému SQL Server najdete v tématu [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="e10f9-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2. <span data-ttu-id="e10f9-111">Deklarování funkce v úložiště schema definition language (SSDL) souboru .edmx.</span><span class="sxs-lookup"><span data-stu-id="e10f9-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="e10f9-112">Název funkce musí být stejný jako název funkce deklarovaná v databázi.</span><span class="sxs-lookup"><span data-stu-id="e10f9-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="e10f9-113">Další informace najdete v tématu [funkce – Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="e10f9-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>  
  
3. <span data-ttu-id="e10f9-114">Přidejte odpovídající metodu na třídu v kódu aplikace a použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metody Všimněte si, že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu se názvu oboru názvů Koncepční model a název funkce v konceptuálním model, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e10f9-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="e10f9-115">Funkce překlad názvů pro funkci LINQ je velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="e10f9-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4. <span data-ttu-id="e10f9-116">Volání metody v technologii LINQ to Entities dotazu.</span><span class="sxs-lookup"><span data-stu-id="e10f9-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e10f9-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e10f9-117">Example</span></span>  
 <span data-ttu-id="e10f9-118">Následující příklad ukazuje, jak volat funkci vlastní databázi z v rámci LINQ dotazu entity.</span><span class="sxs-lookup"><span data-stu-id="e10f9-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="e10f9-119">V příkladu používá model školy.</span><span class="sxs-lookup"><span data-stu-id="e10f9-119">The example uses the School model.</span></span> <span data-ttu-id="e10f9-120">Informace o School modelu najdete v tématu [vytvoření ukázkové databáze školy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) a [generování školní edmx soubor](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e10f9-120">For information about the School model, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="e10f9-121">Následující kód přidává `AvgStudentGrade` funkce k ukázkové databázi School.</span><span class="sxs-lookup"><span data-stu-id="e10f9-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e10f9-122">Kroky pro volání funkce vlastní databázi jsou stejné bez ohledu na databázovém serveru.</span><span class="sxs-lookup"><span data-stu-id="e10f9-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="e10f9-123">Následující kód je však specifické pro vytvoření funkce v databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e10f9-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="e10f9-124">Kód pro vytvoření vlastní funkce v jiné databázové servery se může lišit.</span><span class="sxs-lookup"><span data-stu-id="e10f9-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="e10f9-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="e10f9-125">Example</span></span>  
 <span data-ttu-id="e10f9-126">V dalším kroku deklarování funkce v úložiště schema definition language (SSDL) souboru .edmx.</span><span class="sxs-lookup"><span data-stu-id="e10f9-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="e10f9-127">Následující kód deklaruje `AvgStudentGrade` funkce v SSDL:</span><span class="sxs-lookup"><span data-stu-id="e10f9-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="e10f9-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="e10f9-128">Example</span></span>  
 <span data-ttu-id="e10f9-129">Teď vytvořte metodu a jejich mapování na funkce deklarovaná v SSDL.</span><span class="sxs-lookup"><span data-stu-id="e10f9-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="e10f9-130">Metoda následující třída je namapována na funkci definované v SSDL (viz výše) pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e10f9-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="e10f9-131">Když tato metoda je volána, je proveden odpovídající funkce v databázi.</span><span class="sxs-lookup"><span data-stu-id="e10f9-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="e10f9-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="e10f9-132">Example</span></span>  
 <span data-ttu-id="e10f9-133">Nakonec proveďte volání metody v technologii LINQ to Entities dotazu.</span><span class="sxs-lookup"><span data-stu-id="e10f9-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="e10f9-134">Následující kód zobrazí poslední jména studentů a průměrné známek do konzoly:</span><span class="sxs-lookup"><span data-stu-id="e10f9-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e10f9-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e10f9-135">See also</span></span>

- <span data-ttu-id="e10f9-136">[Přehled souboru EDMX](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e10f9-136">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="e10f9-137">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e10f9-137">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
