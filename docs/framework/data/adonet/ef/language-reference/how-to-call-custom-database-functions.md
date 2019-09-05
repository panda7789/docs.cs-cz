---
title: 'Postupy: Volání vlastních databázových funkcí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: b7f483d8dc7c6d0160ec211140726c9d732f0268
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250811"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="61b03-102">Postupy: Volání vlastních databázových funkcí</span><span class="sxs-lookup"><span data-stu-id="61b03-102">How to: Call Custom Database Functions</span></span>
<span data-ttu-id="61b03-103">Toto téma popisuje, jak volat vlastní funkce, které jsou definovány v databázi nástroje v rámci LINQ to Entities dotazů.</span><span class="sxs-lookup"><span data-stu-id="61b03-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="61b03-104">Databázové funkce, které jsou volány z LINQ to Entities dotazy, jsou spouštěny v databázi.</span><span class="sxs-lookup"><span data-stu-id="61b03-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="61b03-105">Spouštění funkcí v databázi může zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="61b03-105">Executing functions in the database can improve application performance.</span></span>  
  
 <span data-ttu-id="61b03-106">Následující postup poskytuje osnovu vysoké úrovně pro volání vlastní databázové funkce.</span><span class="sxs-lookup"><span data-stu-id="61b03-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="61b03-107">Následující příklad poskytuje další podrobnosti o krocích v postupu.</span><span class="sxs-lookup"><span data-stu-id="61b03-107">The example that follows provides more detail about the steps in the procedure.</span></span>  
  
### <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="61b03-108">Volání vlastních funkcí, které jsou definovány v databázi</span><span class="sxs-lookup"><span data-stu-id="61b03-108">To call custom functions that are defined in the database</span></span>  
  
1. <span data-ttu-id="61b03-109">Vytvořte vlastní funkci v databázi.</span><span class="sxs-lookup"><span data-stu-id="61b03-109">Create a custom function in your database.</span></span>  
  
     <span data-ttu-id="61b03-110">Další informace o vytváření vlastních funkcí v SQL Server naleznete v tématu [Create Function (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span><span class="sxs-lookup"><span data-stu-id="61b03-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkID=139871).</span></span>  
  
2. <span data-ttu-id="61b03-111">Deklarujte funkci v souboru SSDL (Store Schema Definition Language) souboru. edmx.</span><span class="sxs-lookup"><span data-stu-id="61b03-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="61b03-112">Název funkce musí být stejný jako název funkce deklarované v databázi.</span><span class="sxs-lookup"><span data-stu-id="61b03-112">The name of the function must be the same as the name of the function declared in the database.</span></span>  
  
     <span data-ttu-id="61b03-113">Další informace naleznete v tématu [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span><span class="sxs-lookup"><span data-stu-id="61b03-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>  
  
3. <span data-ttu-id="61b03-114">Přidejte odpovídající metodu do třídy v kódu aplikace a použijte <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> pro metodu Všimněte si <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> , že parametry a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> jsou v oboru názvů koncepčního modelu a názvu funkce v koncepčním rozhraní. model v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="61b03-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="61b03-115">Rozlišení názvu funkce pro LINQ rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="61b03-115">Function name resolution for LINQ is case sensitive.</span></span>  
  
4. <span data-ttu-id="61b03-116">Volání metody v dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="61b03-116">Call the method in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61b03-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="61b03-117">Example</span></span>  
 <span data-ttu-id="61b03-118">Následující příklad ukazuje, jak volat vlastní databázovou funkci v rámci LINQ to Entitiesho dotazu.</span><span class="sxs-lookup"><span data-stu-id="61b03-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="61b03-119">V příkladu se používá školní model.</span><span class="sxs-lookup"><span data-stu-id="61b03-119">The example uses the School model.</span></span> <span data-ttu-id="61b03-120">Informace o školním modelu najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) a [Vytvoření souboru School. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="61b03-120">For information about the School model, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="61b03-121">Následující kód přidá `AvgStudentGrade` funkci do ukázkové databáze School.</span><span class="sxs-lookup"><span data-stu-id="61b03-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="61b03-122">Postup volání vlastní databázové funkce je stejný bez ohledu na databázový server.</span><span class="sxs-lookup"><span data-stu-id="61b03-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="61b03-123">Níže uvedený kód je však specifický pro vytvoření funkce v databázi SQL Server.</span><span class="sxs-lookup"><span data-stu-id="61b03-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="61b03-124">Kód pro vytvoření vlastní funkce v jiných databázových serverech se může lišit.</span><span class="sxs-lookup"><span data-stu-id="61b03-124">The code for creating a custom function in other database servers might differ.</span></span>  
  
 [!code-sql[DP L2E MapToDBFunction#1](../../../../../../samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]  
  
## <a name="example"></a><span data-ttu-id="61b03-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="61b03-125">Example</span></span>  
 <span data-ttu-id="61b03-126">Dále Deklarujte funkci v souboru SSDL (Store Schema Definition Language) souboru. edmx.</span><span class="sxs-lookup"><span data-stu-id="61b03-126">Next, declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="61b03-127">Následující kód deklaruje `AvgStudentGrade` funkci ve SSDL:</span><span class="sxs-lookup"><span data-stu-id="61b03-127">the following code declares the `AvgStudentGrade` function in SSDL:</span></span>  
  
 [!code-xml[DP L2E MapToDBFunction#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]  
  
## <a name="example"></a><span data-ttu-id="61b03-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="61b03-128">Example</span></span>  
 <span data-ttu-id="61b03-129">Nyní vytvořte metodu a namapujte ji na funkci deklarovanou ve SSDL.</span><span class="sxs-lookup"><span data-stu-id="61b03-129">Now create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="61b03-130">Metoda v následující třídě je namapována na funkci definovanou v SSDL (výše) pomocí <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="61b03-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="61b03-131">Při volání této metody se spustí odpovídající funkce v databázi.</span><span class="sxs-lookup"><span data-stu-id="61b03-131">When this method is called, the corresponding function in the database is executed.</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
 [!code-vb[DP L2E MapToDBFunction#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="61b03-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="61b03-132">Example</span></span>  
 <span data-ttu-id="61b03-133">Nakonec zavolejte metodu v dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="61b03-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="61b03-134">Následující kód zobrazuje poslední názvy studentů a průměrné úrovně pro konzolu:</span><span class="sxs-lookup"><span data-stu-id="61b03-134">The following code displays students' last names and average grades to the console:</span></span>  
  
 [!code-csharp[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
 [!code-vb[DP L2E MapToDBFunction#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="61b03-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61b03-135">See also</span></span>

- <span data-ttu-id="61b03-136">[Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="61b03-136">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="61b03-137">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="61b03-137">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
