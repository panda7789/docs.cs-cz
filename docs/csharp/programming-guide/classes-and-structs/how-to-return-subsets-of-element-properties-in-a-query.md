---
title: 'Postupy: Vrácení podmnožin vlastností elementu v dotazu (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 22b6cc8fc8c8d9ffd1c2cf4063994ce94cea8e45
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520840"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="4fba4-102">Postupy: Vrácení podmnožin vlastností elementu v dotazu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4fba4-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="4fba4-103">Použijte anonymního typu ve výrazu dotazu, pokud obě tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="4fba4-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="4fba4-104">Chcete vrátit jenom některé vlastnosti jednotlivých zdrojových elementů.</span><span class="sxs-lookup"><span data-stu-id="4fba4-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="4fba4-105">Není nutné pro ukládání výsledků dotazu nad rámec metoda spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="4fba4-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="4fba4-106">Pokud chcete vrátit jednu vlastnost nebo pole z jednotlivých zdrojových elementů, pak tečka v můžete použít jenom `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4fba4-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="4fba4-107">Například vrátit pouze `ID` jednotlivých `student`, zapisovat `select` klauzule následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4fba4-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="4fba4-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fba4-108">Example</span></span>  
 <span data-ttu-id="4fba4-109">Následující příklad ukazuje, jak použít anonymní typ, který vrátí pouze podmnožinu vlastností jednotlivých zdrojových elementů, který odpovídá zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="4fba4-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 <span data-ttu-id="4fba4-110">Všimněte si, že používá anonymní typ zdrojového prvku názvy vlastností Pokud nejsou zadány žádné názvy.</span><span class="sxs-lookup"><span data-stu-id="4fba4-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="4fba4-111">Chcete-li pojmenovat nové vlastnosti v anonymním typu, napište `select` příkaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4fba4-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="4fba4-112">Pokud se to pokusíte v předchozím příkladu, pak bude `Console.WriteLine` musí také změňte příkaz:</span><span class="sxs-lookup"><span data-stu-id="4fba4-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4fba4-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4fba4-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="4fba4-114">Tento kód spustit, zkopírujte a vložte třídy v jazyce Visual C# projekt konzolové aplikace, který nebyl vytvořen v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4fba4-114">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="4fba4-115">Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a bude mít odkaz na System.Core.dll a `using` směrnice pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="4fba4-115">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="4fba4-116">Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="4fba4-116">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="4fba4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fba4-117">See Also</span></span>

- [<span data-ttu-id="4fba4-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4fba4-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4fba4-119">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="4fba4-119">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [<span data-ttu-id="4fba4-120">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="4fba4-120">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
