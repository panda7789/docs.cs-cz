---
title: "Postupy: Vrácení podmnožin vlastností elementu v dotazu (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6654b162fbdeb59ed2a135d7d8cf58c8b3406c13
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="23049-102">Postupy: Vrácení podmnožin vlastností elementu v dotazu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="23049-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="23049-103">Použijte anonymní typ ve výrazu dotazu, pokud obě tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="23049-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
-   <span data-ttu-id="23049-104">Chcete vrátit jenom některé z vlastností jednotlivých prvků zdroje.</span><span class="sxs-lookup"><span data-stu-id="23049-104">You want to return only some of the properties of each source element.</span></span>  
  
-   <span data-ttu-id="23049-105">Nemáte, můžete ukládat výsledky dotazu mimo obor metody, ve kterém se spustí dotaz.</span><span class="sxs-lookup"><span data-stu-id="23049-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="23049-106">Pokud chcete z každý element source vrátit jednu vlastnost nebo pole, pak použijete na operátor tečky v `select` klauzule.</span><span class="sxs-lookup"><span data-stu-id="23049-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="23049-107">Například vrátit pouze `ID` jednotlivých `student`, zapisovat `select` klauzule následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="23049-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="23049-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="23049-108">Example</span></span>  
 <span data-ttu-id="23049-109">Následující příklad ukazuje, jak použít anonymní typ, který vrátí pouze podmnožinu vlastností každý element source, který odpovídá zadanou podmínku.</span><span class="sxs-lookup"><span data-stu-id="23049-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-return-subsets-of-element-properties-in-a-query_1.cs)]  
  
 <span data-ttu-id="23049-110">Všimněte si, že anonymního typu používá source element názvy vlastností, pokud nejsou zadány žádné názvy.</span><span class="sxs-lookup"><span data-stu-id="23049-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="23049-111">Umožnit nové názvy pro vlastnosti v anonymní typ zapisovat `select` příkaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="23049-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="23049-112">Pokud to zkusíte v předchozím příkladu, pak se `Console.WriteLine` příkaz musíte změnit taky:</span><span class="sxs-lookup"><span data-stu-id="23049-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23049-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="23049-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="23049-114">Pokud chcete spustit tento kód, zkopírujte a vložte třídy do Visual C# projektu konzolové aplikace vytvořené v [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23049-114">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="23049-115">Ve výchozím nastavení, tento projekt zaměřen na verzi 3.5 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], a bude mít odkaz na System.Core.dll a `using` direktivy pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="23049-115">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it will have a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="23049-116">Pokud z projektu chybí jeden nebo více z těchto požadavků, můžete je přidat ručně.</span><span class="sxs-lookup"><span data-stu-id="23049-116">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="23049-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="23049-117">See Also</span></span>  
 [<span data-ttu-id="23049-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="23049-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="23049-119">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="23049-119">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="23049-120">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="23049-120">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
