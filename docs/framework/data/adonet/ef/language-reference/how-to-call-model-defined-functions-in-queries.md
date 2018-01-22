---
title: "Postupy: volání modelu definované funkce v dotazech."
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
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ec20542ad452bcefbe2b6d286e68ad8bbfb5adb9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="e35db-102">Postupy: volání modelu definované funkce v dotazech.</span><span class="sxs-lookup"><span data-stu-id="e35db-102">How to: Call Model-Defined Functions in Queries</span></span>
<span data-ttu-id="e35db-103">Toto téma popisuje, jak volat funkce, které jsou definované v konceptuálním modelu uvnitř [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazy.</span><span class="sxs-lookup"><span data-stu-id="e35db-103">This topic describes how to call functions that are defined in the conceptual model from within [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="e35db-104">Následující postup obsahovala hrubý nástin pro volání funkce modelu definované v nástroji [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="e35db-104">The procedure below provides a high-level outline for calling a model-defined function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="e35db-105">Příklad, který následuje obsahuje více podrobností o kroků v postupu.</span><span class="sxs-lookup"><span data-stu-id="e35db-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="e35db-106">Postupu se předpokládá, že jste definovali funkci v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="e35db-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="e35db-107">Další informace najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span><span class="sxs-lookup"><span data-stu-id="e35db-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="e35db-108">Volat funkci definovanou v konceptuálním modelu</span><span class="sxs-lookup"><span data-stu-id="e35db-108">To call a function defined in the conceptual model</span></span>  
  
1.  <span data-ttu-id="e35db-109">Přidejte běžnou metodu language runtime (CLR) do vaší aplikace, která se mapuje na funkci definovanou v konceptuálním modelu.</span><span class="sxs-lookup"><span data-stu-id="e35db-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="e35db-110">Chcete-li mapovat metodu, je nutné použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> metodě.</span><span class="sxs-lookup"><span data-stu-id="e35db-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="e35db-111">Všimněte si, že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry atributu jsou název oboru názvů konceptuálního modelu a název funkce v konceptuálním modelu v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e35db-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="e35db-112">Funkce překladu názvů u LINQ je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e35db-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2.  <span data-ttu-id="e35db-113">Volání funkce v [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="e35db-113">Call the function in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e35db-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="e35db-114">Example</span></span>  
 <span data-ttu-id="e35db-115">Následující příklad ukazuje, jak zavolat funkci, která je definována v konceptuálním modelu uvnitř [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="e35db-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="e35db-116">V příkladu školní modelu.</span><span class="sxs-lookup"><span data-stu-id="e35db-116">The example uses the School model.</span></span> <span data-ttu-id="e35db-117">Informace o modelu školní najdete v tématu [vytváření ukázkovou databázi školy](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) a [generování školní .edmx souboru](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="e35db-117">For information about the School model, see [Creating the School Sample Database](http://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](http://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="e35db-118">Následující funkce konceptuálního modelu vrátí počet roků, vzhledem k tomu, že lektorem byl přijat.</span><span class="sxs-lookup"><span data-stu-id="e35db-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="e35db-119">Informace o přidání funkce do konceptuálního modelu najdete v tématu [postupy: definování vlastní funkce v konceptuálním modelu](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span><span class="sxs-lookup"><span data-stu-id="e35db-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="e35db-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="e35db-120">Example</span></span>  
 <span data-ttu-id="e35db-121">V dalším kroku přidejte následující metodu pro vaše aplikace a použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> k mapování na funkci konceptuálního modelu:</span><span class="sxs-lookup"><span data-stu-id="e35db-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="e35db-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="e35db-122">Example</span></span>  
 <span data-ttu-id="e35db-123">Teď můžete volat funkci konceptuálního modelu z uvnitř [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] dotazu.</span><span class="sxs-lookup"><span data-stu-id="e35db-123">Now you can call the conceptual model function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="e35db-124">Následující kód zavolá metodu pro zobrazení všech vyučující, které byly přijaty před více než deset let:</span><span class="sxs-lookup"><span data-stu-id="e35db-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e35db-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e35db-125">See Also</span></span>  
 [<span data-ttu-id="e35db-126">Přehled souboru EDMX</span><span class="sxs-lookup"><span data-stu-id="e35db-126">.edmx File Overview</span></span>](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="e35db-127">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e35db-127">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="e35db-128">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e35db-128">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="e35db-129">Postupy: Volání modelově definovaných funkcí jako objektových metod</span><span class="sxs-lookup"><span data-stu-id="e35db-129">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
