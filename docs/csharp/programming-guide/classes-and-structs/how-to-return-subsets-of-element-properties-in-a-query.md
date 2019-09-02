---
title: 'Postupy: Vrácení podmnožiny vlastností elementu v dotazu – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 2c9fea2189819058187020c2e67b8826659fbed4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205443"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="712a5-102">Postupy: Vrácení podmnožiny vlastností elementu v dotazu (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="712a5-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="712a5-103">Použít anonymní typ ve výrazu dotazu, když platí obě tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="712a5-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="712a5-104">Chcete vrátit pouze některé vlastnosti každého zdrojového elementu.</span><span class="sxs-lookup"><span data-stu-id="712a5-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="712a5-105">Výsledky dotazu není nutné ukládat mimo rozsah metody, ve které je dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="712a5-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="712a5-106">Pokud chcete pouze vrátit jednu vlastnost nebo pole z každého elementu zdroje, můžete pouze použít operátor tečka v `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="712a5-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="712a5-107">Například pro vrácení pouze `ID` každého z nich `student`zapište `select` klauzuli následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="712a5-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="712a5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="712a5-108">Example</span></span>  
 <span data-ttu-id="712a5-109">Následující příklad ukazuje, jak použít anonymní typ pro vrácení pouze podmnožiny vlastností každého zdrojového prvku, který odpovídá zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="712a5-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="712a5-110">Všimněte si, že anonymní typ používá názvy zdrojového elementu pro jeho vlastnosti, pokud nejsou zadány žádné názvy.</span><span class="sxs-lookup"><span data-stu-id="712a5-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="712a5-111">Chcete-li zadat nové názvy vlastností v anonymním typu, zapište `select` příkaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="712a5-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="712a5-112">Pokud to zkusíte v předchozím příkladu, `Console.WriteLine` příkaz se musí také změnit:</span><span class="sxs-lookup"><span data-stu-id="712a5-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="712a5-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="712a5-113">Compiling the Code</span></span>  
  
<span data-ttu-id="712a5-114">Chcete-li spustit tento kód, zkopírujte a vložte třídu do C# konzolové aplikace s `using` direktivou pro System. Linq.</span><span class="sxs-lookup"><span data-stu-id="712a5-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="712a5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="712a5-115">See also</span></span>

- [<span data-ttu-id="712a5-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="712a5-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="712a5-117">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="712a5-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="712a5-118">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="712a5-118">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
