---
title: 'Postupy: Volání modelově definovaných funkcí v dotazech'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 33f26896dd0d4ff08beb4a011fa6bd468cba7207
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250759"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="9de24-102">Postupy: Volání modelově definovaných funkcí v dotazech</span><span class="sxs-lookup"><span data-stu-id="9de24-102">How to: Call Model-Defined Functions in Queries</span></span>
<span data-ttu-id="9de24-103">Toto téma popisuje, jak volat funkce, které jsou definovány v koncepčním modelu v rámci LINQ to Entities dotazů.</span><span class="sxs-lookup"><span data-stu-id="9de24-103">This topic describes how to call functions that are defined in the conceptual model from within LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="9de24-104">Následující postup poskytuje osnovu vysoké úrovně pro volání funkce definované modelem v rámci dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9de24-104">The procedure below provides a high-level outline for calling a model-defined function from within a LINQ to Entities query.</span></span> <span data-ttu-id="9de24-105">Následující příklad poskytuje další podrobnosti o krocích v postupu.</span><span class="sxs-lookup"><span data-stu-id="9de24-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="9de24-106">Procedura předpokládá, že jste definovali funkci v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="9de24-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="9de24-107">Další informace najdete v tématu [jak: Definujte vlastní funkce v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9de24-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="9de24-108">Volání funkce definované v koncepčním modelu</span><span class="sxs-lookup"><span data-stu-id="9de24-108">To call a function defined in the conceptual model</span></span>  
  
1. <span data-ttu-id="9de24-109">Přidejte do aplikace metodu modulu CLR (Common Language Runtime), která se mapuje na funkci definovanou v koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="9de24-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="9de24-110">Chcete-li namapovat metodu, musíte použít <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> na metodu.</span><span class="sxs-lookup"><span data-stu-id="9de24-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="9de24-111">Všimněte si, <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> že <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parametry a atributu jsou název oboru názvů koncepčního modelu a název funkce v uvedeném koncepčním modelu.</span><span class="sxs-lookup"><span data-stu-id="9de24-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="9de24-112">Rozlišení názvu funkce pro LINQ rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="9de24-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2. <span data-ttu-id="9de24-113">Volání funkce v dotazu LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="9de24-113">Call the function in a LINQ to Entities query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9de24-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9de24-114">Example</span></span>  
 <span data-ttu-id="9de24-115">Následující příklad ukazuje, jak volat funkci, která je definována v koncepčním modelu v rámci LINQ to Entitiesho dotazu.</span><span class="sxs-lookup"><span data-stu-id="9de24-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a LINQ to Entities query.</span></span> <span data-ttu-id="9de24-116">V příkladu se používá školní model.</span><span class="sxs-lookup"><span data-stu-id="9de24-116">The example uses the School model.</span></span> <span data-ttu-id="9de24-117">Informace o školním modelu najdete v tématu [vytvoření ukázkové školní databáze](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) a [Vytvoření souboru School. edmx](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9de24-117">For information about the School model, see [Creating the School Sample Database](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>  
  
 <span data-ttu-id="9de24-118">Následující funkce koncepčního modelu vrátí počet roků od přijetí instruktora.</span><span class="sxs-lookup"><span data-stu-id="9de24-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="9de24-119">Informace o přidání funkce do koncepčního modelu naleznete v tématu [How to: Definujte vlastní funkce v koncepčním modelu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span><span class="sxs-lookup"><span data-stu-id="9de24-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100)).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="9de24-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="9de24-120">Example</span></span>  
 <span data-ttu-id="9de24-121">Dále do aplikace přidejte následující metodu a použijte <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> ji k namapování na funkci koncepčního modelu:</span><span class="sxs-lookup"><span data-stu-id="9de24-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="9de24-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="9de24-122">Example</span></span>  
 <span data-ttu-id="9de24-123">Nyní můžete volat funkci koncepčního modelu v rámci LINQ to Entitiesho dotazu.</span><span class="sxs-lookup"><span data-stu-id="9de24-123">Now you can call the conceptual model function from within a LINQ to Entities query.</span></span> <span data-ttu-id="9de24-124">Následující kód volá metodu pro zobrazení všech instruktorů, které byly přijaty před více než deseti lety:</span><span class="sxs-lookup"><span data-stu-id="9de24-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="9de24-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9de24-125">See also</span></span>

- <span data-ttu-id="9de24-126">[Soubor. edmx – přehled](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9de24-126">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="9de24-127">Dotazy v technologii LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9de24-127">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
- [<span data-ttu-id="9de24-128">Volání funkcí v dotazech LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="9de24-128">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="9de24-129">Postupy: Volání funkcí definovaných modelem jako metod objektů</span><span class="sxs-lookup"><span data-stu-id="9de24-129">How to: Call Model-Defined Functions as Object Methods</span></span>](how-to-call-model-defined-functions-as-object-methods.md)
