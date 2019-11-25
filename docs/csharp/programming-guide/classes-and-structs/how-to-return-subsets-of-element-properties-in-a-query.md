---
title: Jak vracet podmnožiny vlastností elementu v dotazu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 1266b866d671854c787d907b91f654c128681de9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970460"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="0b3d7-102">Vrácení podmnožiny vlastností elementu v dotazu (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="0b3d7-102">How to return subsets of element properties in a query (C# Programming Guide)</span></span>
<span data-ttu-id="0b3d7-103">Použít anonymní typ ve výrazu dotazu, když platí obě tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="0b3d7-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="0b3d7-104">Chcete vrátit pouze některé vlastnosti každého zdrojového elementu.</span><span class="sxs-lookup"><span data-stu-id="0b3d7-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="0b3d7-105">Výsledky dotazu není nutné ukládat mimo rozsah metody, ve které je dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="0b3d7-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="0b3d7-106">Pokud chcete pouze vrátit jednu vlastnost nebo pole z každého elementu zdroje, můžete pouze použít operátor tečka v klauzuli `select`.</span><span class="sxs-lookup"><span data-stu-id="0b3d7-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="0b3d7-107">Například chcete-li vrátit pouze `ID` každého `student`, napište klauzuli `select` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0b3d7-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="0b3d7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b3d7-108">Example</span></span>  
 <span data-ttu-id="0b3d7-109">Následující příklad ukazuje, jak použít anonymní typ pro vrácení pouze podmnožiny vlastností každého zdrojového prvku, který odpovídá zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="0b3d7-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="0b3d7-110">Všimněte si, že anonymní typ používá názvy zdrojového elementu pro jeho vlastnosti, pokud nejsou zadány žádné názvy.</span><span class="sxs-lookup"><span data-stu-id="0b3d7-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="0b3d7-111">Chcete-li zadat nové názvy vlastností v anonymním typu, zapište příkaz `select` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0b3d7-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="0b3d7-112">Pokud to zkusíte v předchozím příkladu, musí se také změnit příkaz `Console.WriteLine`:</span><span class="sxs-lookup"><span data-stu-id="0b3d7-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0b3d7-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0b3d7-113">Compiling the Code</span></span>  
  
<span data-ttu-id="0b3d7-114">Chcete-li spustit tento kód, zkopírujte a vložte třídu do C# konzolové aplikace s direktivou `using` pro třídu System. Linq.</span><span class="sxs-lookup"><span data-stu-id="0b3d7-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0b3d7-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b3d7-115">See also</span></span>

- [<span data-ttu-id="0b3d7-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0b3d7-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0b3d7-117">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="0b3d7-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="0b3d7-118">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0b3d7-118">LINQ in C#</span></span>](../../linq/index.md)
