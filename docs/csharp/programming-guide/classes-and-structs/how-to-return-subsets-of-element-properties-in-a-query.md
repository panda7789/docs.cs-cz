---
title: 'Postupy: Vrácení podmnožin vlastností elementu v dotazu - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 80f13250576957b252d6d83bfbcf70346b49b5a7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980719"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="17be1-102">Postupy: Vrácení podmnožin vlastností elementu v dotazu (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="17be1-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="17be1-103">Použijte anonymního typu ve výrazu dotazu, pokud obě tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="17be1-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="17be1-104">Chcete vrátit jenom některé vlastnosti jednotlivých zdrojových elementů.</span><span class="sxs-lookup"><span data-stu-id="17be1-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="17be1-105">Není nutné pro ukládání výsledků dotazu nad rámec metoda spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="17be1-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="17be1-106">Pokud chcete vrátit jednu vlastnost nebo pole z jednotlivých zdrojových elementů, pak tečka v můžete použít jenom `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="17be1-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="17be1-107">Například vrátit pouze `ID` jednotlivých `student`, zapisovat `select` klauzule následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="17be1-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="17be1-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="17be1-108">Example</span></span>  
 <span data-ttu-id="17be1-109">Následující příklad ukazuje, jak použít anonymní typ, který vrátí pouze podmnožinu vlastností jednotlivých zdrojových elementů, který odpovídá zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="17be1-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="17be1-110">Všimněte si, že používá anonymní typ zdrojového prvku názvy vlastností Pokud nejsou zadány žádné názvy.</span><span class="sxs-lookup"><span data-stu-id="17be1-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="17be1-111">Chcete-li pojmenovat nové vlastnosti v anonymním typu, napište `select` příkaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="17be1-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="17be1-112">Pokud se to pokusíte v předchozím příkladu, pak bude `Console.WriteLine` musí také změňte příkaz:</span><span class="sxs-lookup"><span data-stu-id="17be1-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17be1-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="17be1-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="17be1-114">Tento kód spustit, zkopírujte a vložte třídy v jazyce Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17be1-114">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="17be1-115">Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a bude mít odkaz na System.Core.dll a `using` směrnice pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="17be1-115">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="17be1-116">Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="17be1-116">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="17be1-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17be1-117">See also</span></span>

- [<span data-ttu-id="17be1-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="17be1-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="17be1-119">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="17be1-119">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="17be1-120">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="17be1-120">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
