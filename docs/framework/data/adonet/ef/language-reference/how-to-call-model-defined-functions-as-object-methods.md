---
title: "Postupy: volání funkce Model definován jako objekt metody"
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
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 81b9f8099f98915ec0b0f83dbe0f90e506cb2a79
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a><span data-ttu-id="4b685-102">Postupy: volání funkce Model definován jako objekt metody</span><span class="sxs-lookup"><span data-stu-id="4b685-102">How to: Call Model-Defined Functions as Object Methods</span></span>
<span data-ttu-id="4b685-103">Toto téma popisuje, jak volat funkci definované model jako metodu <xref:System.Data.Objects.ObjectContext> objektu nebo jako statickou metodu vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="4b685-103">This topic describes how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object or as a static method on a custom class.</span></span> <span data-ttu-id="4b685-104">A *modelu definované funkce* je funkce, která je definována v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="4b685-104">A *model-defined function* is a function that is defined in the conceptual model.</span></span> <span data-ttu-id="4b685-105">Postupy v tomto tématu popisují, jak volat tyto funkce přímo namísto volání je z technologie LINQ dotazy entity.</span><span class="sxs-lookup"><span data-stu-id="4b685-105">The procedures in the topic describe how to call these functions directly instead of calling them from LINQ to Entities queries.</span></span> <span data-ttu-id="4b685-106">Informace o volání funkcí modelu definované v technologii LINQ na entity dotazy najdete v tématu [postupy: Call Model-Defined funkcí v dotazech](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).</span><span class="sxs-lookup"><span data-stu-id="4b685-106">For information about calling model-defined functions in LINQ to Entities queries, see [How to: Call Model-Defined Functions in Queries](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).</span></span>  
  
 <span data-ttu-id="4b685-107">Zda můžete volat funkci model definován jako <xref:System.Data.Objects.ObjectContext> metoda nebo jako statickou metodu vlastní třídy, je nutné nejprve mapovat metodu do modelu definované funkce se <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="4b685-107">Whether you call a model-defined function as an <xref:System.Data.Objects.ObjectContext> method or as a static method on a custom class, you must first map the method to the model-defined function with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="4b685-108">Ale když definujete metodu na <xref:System.Data.Objects.ObjectContext> třídy, je nutné použít <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> vlastnost vystavit LINQ poskytovatele, že když definujete vlastní třídy statickou metodu, je nutné použít <xref:System.Linq.IQueryable.Provider%2A> vlastnost vystavit LINQ zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="4b685-108">However, when you define a method on the <xref:System.Data.Objects.ObjectContext> class, you must use the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property to expose the LINQ provider, whereas when you define a static method on a custom class, you must use the <xref:System.Linq.IQueryable.Provider%2A> property to expose the LINQ provider.</span></span> <span data-ttu-id="4b685-109">Další informace najdete v tématu příklady, které postupujte podle pokynů níže.</span><span class="sxs-lookup"><span data-stu-id="4b685-109">For more information, see the examples that follow the procedures below.</span></span>  
  
 <span data-ttu-id="4b685-110">Zadejte níže uvedených postupech obsahuje podrobný přehled pro volání funkce modelu definované jako metodu na <xref:System.Data.Objects.ObjectContext> objektu a jako statickou metodu vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="4b685-110">The procedures below provide high-level outlines for calling a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object and as a static method on a custom class.</span></span> <span data-ttu-id="4b685-111">Příklady, které poskytují podrobnější informace o krocích v postupech.</span><span class="sxs-lookup"><span data-stu-id="4b685-111">The examples that follow provide more detail about the steps in the procedures.</span></span> <span data-ttu-id="4b685-112">V postupech se předpokládá, že jste definovali funkci v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="4b685-112">The procedures assume that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="4b685-113">Další informace najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span><span class="sxs-lookup"><span data-stu-id="4b685-113">For more information, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a><span data-ttu-id="4b685-114">K volání funkce model definován jako metodu objektu ObjectContext</span><span class="sxs-lookup"><span data-stu-id="4b685-114">To call a model-defined function as a method on an ObjectContext object</span></span>  
  
1.  <span data-ttu-id="4b685-115">Přidání zdrojového souboru rozšíření částečné třídy odvozené od <xref:System.Data.Objects.ObjectContext> třída, vygenerována automaticky prostřednictvím nástroje Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="4b685-115">Add a source file to extend the partial class derived from the <xref:System.Data.Objects.ObjectContext> class, auto-generated by the Entity Framework tools.</span></span> <span data-ttu-id="4b685-116">Definování se zakázaným inzerováním CLR samostatného zdrojového souboru bude zabránit ke ztrátě při znovu vygeneruje soubor změny.</span><span class="sxs-lookup"><span data-stu-id="4b685-116">Defining the CLR stub in a separate source file will prevent the changes from being lost when the file is regenerated.</span></span>  
  
2.  <span data-ttu-id="4b685-117">Přidat běžnou metodu language runtime (CLR) do vaší <xref:System.Data.Objects.ObjectContext> třídu, která provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="4b685-117">Add a common language runtime (CLR) method to your <xref:System.Data.Objects.ObjectContext> class that does the following:</span></span>  
  
    -   <span data-ttu-id="4b685-118">Mapuje funkci definovanou v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="4b685-118">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="4b685-119">Chcete-li mapovat metodu, je nutné použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metodě.</span><span class="sxs-lookup"><span data-stu-id="4b685-119">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="4b685-120">Všimněte si, že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu jsou název oboru názvů konceptuálního modelu a název funkce v konceptuálním modelu, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4b685-120">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span> <span data-ttu-id="4b685-121">Funkce překladu názvů u LINQ je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="4b685-121">Function name resolution for LINQ is case sensitive.</span></span>  
  
    -   <span data-ttu-id="4b685-122">Vrátí výsledky <xref:System.Linq.IQueryProvider.Execute%2A> metoda, která je vrácena <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4b685-122">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property.</span></span>  
  
3.  <span data-ttu-id="4b685-123">Volejte metodu jako člena na instanci systému <xref:System.Data.Objects.ObjectContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="4b685-123">Call the method as a member on an instance of the <xref:System.Data.Objects.ObjectContext> class.</span></span>  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a><span data-ttu-id="4b685-124">K volání funkce model definován jako statickou metodu vlastní třídy</span><span class="sxs-lookup"><span data-stu-id="4b685-124">To call a model-defined function as static method on a custom class</span></span>  
  
1.  <span data-ttu-id="4b685-125">Přidejte třídu do vaší aplikace s statickou metodu, která provede následující akce:</span><span class="sxs-lookup"><span data-stu-id="4b685-125">Add a class to your application with a static method that does the following:</span></span>  
  
    -   <span data-ttu-id="4b685-126">Mapuje funkci definovanou v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="4b685-126">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="4b685-127">Chcete-li mapovat metodu, je nutné použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metodě.</span><span class="sxs-lookup"><span data-stu-id="4b685-127">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="4b685-128">Všimněte si, že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu jsou název oboru názvů konceptuálního modelu a název funkce v konceptuálním modelu, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4b685-128">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span>  
  
    -   <span data-ttu-id="4b685-129">Přijímá <xref:System.Linq.IQueryable> argument.</span><span class="sxs-lookup"><span data-stu-id="4b685-129">Accepts an <xref:System.Linq.IQueryable> argument.</span></span>  
  
    -   <span data-ttu-id="4b685-130">Vrátí výsledky <xref:System.Linq.IQueryProvider.Execute%2A> metoda, která je vrácena <xref:System.Linq.IQueryable.Provider%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4b685-130">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Linq.IQueryable.Provider%2A> property.</span></span>  
  
2.  <span data-ttu-id="4b685-131">Volat metodu jako člen statickou metodu pro vlastní třídu</span><span class="sxs-lookup"><span data-stu-id="4b685-131">Call the method as a member a static method on the custom class</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b685-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b685-132">Example</span></span>  
 <span data-ttu-id="4b685-133">**Volání funkce modelu definované jako metodu objektu ObjectContext**</span><span class="sxs-lookup"><span data-stu-id="4b685-133">**Calling a Model-Defined Function as a Method on an ObjectContext Object**</span></span>  
  
 <span data-ttu-id="4b685-134">Následující příklad ukazuje, jak volat funkci definované model jako metodu <xref:System.Data.Objects.ObjectContext> objektu.</span><span class="sxs-lookup"><span data-stu-id="4b685-134">The following example demonstrates how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object.</span></span> <span data-ttu-id="4b685-135">V příkladu se používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="4b685-135">The example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span>  
  
 <span data-ttu-id="4b685-136">Zvažte funkce konceptuálního modelu nižší, než je vrací výnosy produktu pro určitý produkt.</span><span class="sxs-lookup"><span data-stu-id="4b685-136">Consider the conceptual model function below that returns product revenue for a specified product.</span></span> <span data-ttu-id="4b685-137">(Informace o přidání funkce do konceptuálního modelu najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span><span class="sxs-lookup"><span data-stu-id="4b685-137">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a><span data-ttu-id="4b685-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b685-138">Example</span></span>  
 <span data-ttu-id="4b685-139">Následující kód přidá metodu pro `AdventureWorksEntities` třídu, která se mapuje na výše uvedené funkce konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="4b685-139">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="4b685-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b685-140">Example</span></span>  
 <span data-ttu-id="4b685-141">Následující kód volá metodu výše a zobrazte výnosy produktu pro zadaný produkt:</span><span class="sxs-lookup"><span data-stu-id="4b685-141">The following code calls the method above to display the product revenue for a specified product:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="4b685-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b685-142">Example</span></span>  
 <span data-ttu-id="4b685-143">Následující příklad ukazuje, jak volat funkci definované modelu, která vrátí kolekci (jako <xref:System.Linq.IQueryable%601> objekt).</span><span class="sxs-lookup"><span data-stu-id="4b685-143">The following example demonstrates how to call a model-defined function that returns a collection (as an <xref:System.Linq.IQueryable%601> object).</span></span> <span data-ttu-id="4b685-144">Vezměte v úvahu následující konceptuálního modelu funkce, která vrátí všechny `SalesOrderDetails` pro ID daného produktu.</span><span class="sxs-lookup"><span data-stu-id="4b685-144">Consider the conceptual model function below that returns all the `SalesOrderDetails` for a given product ID.</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a><span data-ttu-id="4b685-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b685-145">Example</span></span>  
 <span data-ttu-id="4b685-146">Následující kód přidá metodu pro `AdventureWorksEntities` třídu, která se mapuje na výše uvedené funkce konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="4b685-146">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="4b685-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b685-147">Example</span></span>  
 <span data-ttu-id="4b685-148">Následující kód volá metodu.</span><span class="sxs-lookup"><span data-stu-id="4b685-148">The following code calls the method.</span></span> <span data-ttu-id="4b685-149">Všimněte si, že vrácený <xref:System.Linq.IQueryable%601> dotazu je další vylepšení vrátit součty řádek pro každou `SalesOrderDetail`.</span><span class="sxs-lookup"><span data-stu-id="4b685-149">Note that the returned <xref:System.Linq.IQueryable%601> query is further refined to return line totals for each `SalesOrderDetail`.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="4b685-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b685-150">Example</span></span>  
 <span data-ttu-id="4b685-151">**Volání funkce modelu definované jako statickou metodu vlastní třídy**</span><span class="sxs-lookup"><span data-stu-id="4b685-151">**Calling a Model-Defined Function as a Static Method on a Custom Class**</span></span>  
  
 <span data-ttu-id="4b685-152">Další příklad ukazuje, jak volat funkci model definován jako statickou metodu vlastní třídy.</span><span class="sxs-lookup"><span data-stu-id="4b685-152">The next example demonstrates how to call a model-defined function as a static method on a custom class.</span></span> <span data-ttu-id="4b685-153">V příkladu se používá [Model prodeje společnosti AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="4b685-153">The example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b685-154">Při volání funkce modelu definované jako statickou metodu na vlastní třídu, model definované funkce, musíte přijmout kolekce a vrátí agregace hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="4b685-154">When you call a model-defined function as a static method on a custom class, the model-defined function must accept a collection and return an aggregation of values in the collection.</span></span>  
  
 <span data-ttu-id="4b685-155">Zvažte funkce konceptuálního modelu nižší, než je vrací výnosy produktu pro kolekci podrobnosti prodejní objednávky.</span><span class="sxs-lookup"><span data-stu-id="4b685-155">Consider the conceptual model function below that returns product revenue for a SalesOrderDetail collection.</span></span> <span data-ttu-id="4b685-156">(Informace o přidání funkce do konceptuálního modelu najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).).</span><span class="sxs-lookup"><span data-stu-id="4b685-156">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).).</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="4b685-157">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b685-157">Example</span></span>  
 <span data-ttu-id="4b685-158">Následující kód přidá třídu do vaší aplikace, který obsahuje statickou metodu, která se mapuje na výše uvedené funkce konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="4b685-158">The following code adds a class to your application that contains a static method that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="4b685-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b685-159">Example</span></span>  
 <span data-ttu-id="4b685-160">Následující kód volá metodu výše a zobrazte výnosy produktu pro kolekci podrobnosti prodejní objednávky:</span><span class="sxs-lookup"><span data-stu-id="4b685-160">The following code calls the method above to display the product revenue for a SalesOrderDetail collection:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="4b685-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b685-161">See Also</span></span>  
 [<span data-ttu-id="4b685-162">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="4b685-162">.edmx File Overview</span></span>](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="4b685-163">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4b685-163">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="4b685-164">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="4b685-164">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
