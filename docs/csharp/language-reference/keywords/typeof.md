---
title: typeof (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 2493e78fd0782eebee17afd979e1c429339d0a3f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486802"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="c76bb-102">typeof (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c76bb-102">typeof (C# Reference)</span></span>
<span data-ttu-id="c76bb-103">Používá k získání `System.Type` pro typ objektu.</span><span class="sxs-lookup"><span data-stu-id="c76bb-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="c76bb-104">A `typeof` výrazu má následující podobu:</span><span class="sxs-lookup"><span data-stu-id="c76bb-104">A `typeof` expression takes the following form:</span></span>  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c76bb-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c76bb-105">Remarks</span></span>  
 <span data-ttu-id="c76bb-106">Pokud chcete získat run-time typu výrazu, můžete použít metodu rozhraní .NET Framework <xref:System.Object.GetType%2A>, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c76bb-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="c76bb-107">`typeof` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="c76bb-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="c76bb-108">`typeof` Operátor můžete použít také u otevřených obecných typů.</span><span class="sxs-lookup"><span data-stu-id="c76bb-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="c76bb-109">Typy s více než jeden parametr typu musí mít odpovídající počet čárek ve specifikaci.</span><span class="sxs-lookup"><span data-stu-id="c76bb-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="c76bb-110">Následující příklad ukazuje, jak zjistit, jestli návratový typ metody je obecný <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="c76bb-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="c76bb-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> Vrátí `null` návratový typ není-li <xref:System.Collections.Generic.IEnumerable%601> obecného typu.</span><span class="sxs-lookup"><span data-stu-id="c76bb-111"><xref:System.Type.GetInterface%2A?displayProperty=nameWithType> will return `null` if the return type is not an <xref:System.Collections.Generic.IEnumerable%601> generic type.</span></span>
  
 [!code-csharp[typeof_3.cs](~/samples/snippets/csharp/keywords/typeof/typeof_3.cs)]   
  
## <a name="example"></a><span data-ttu-id="c76bb-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="c76bb-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="c76bb-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="c76bb-113">Example</span></span>  
 <span data-ttu-id="c76bb-114">Tento příklad používá <xref:System.Object.GetType%2A> metodu pro určení typu, který se používá pro jiné výsledek číselné výpočtu.</span><span class="sxs-lookup"><span data-stu-id="c76bb-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="c76bb-115">To závisí na požadavky na úložiště z výsledné číslo.</span><span class="sxs-lookup"><span data-stu-id="c76bb-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c76bb-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c76bb-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c76bb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c76bb-117">See Also</span></span>

- <xref:System.Type?displayProperty=nameWithType>  
- [<span data-ttu-id="c76bb-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c76bb-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c76bb-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c76bb-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c76bb-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c76bb-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="c76bb-121">is</span><span class="sxs-lookup"><span data-stu-id="c76bb-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
- [<span data-ttu-id="c76bb-122">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="c76bb-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
