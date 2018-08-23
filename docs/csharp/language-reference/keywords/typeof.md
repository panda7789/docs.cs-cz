---
title: typeof (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 4203b597d7045a13ffed9e61ddbbde57e2113c23
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753983"
---
# <a name="typeof-c-reference"></a><span data-ttu-id="70b61-102">typeof (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="70b61-102">typeof (C# Reference)</span></span>
<span data-ttu-id="70b61-103">Používá k získání `System.Type` pro typ objektu.</span><span class="sxs-lookup"><span data-stu-id="70b61-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="70b61-104">A `typeof` výrazu má následující podobu:</span><span class="sxs-lookup"><span data-stu-id="70b61-104">A `typeof` expression takes the following form:</span></span>  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="70b61-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70b61-105">Remarks</span></span>  
 <span data-ttu-id="70b61-106">Pokud chcete získat run-time typu výrazu, můžete použít metodu rozhraní .NET Framework <xref:System.Object.GetType%2A>, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="70b61-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="70b61-107">`typeof` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="70b61-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="70b61-108">`typeof` Operátor můžete použít také u otevřených obecných typů.</span><span class="sxs-lookup"><span data-stu-id="70b61-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="70b61-109">Typy s více než jeden parametr typu musí mít odpovídající počet čárek ve specifikaci.</span><span class="sxs-lookup"><span data-stu-id="70b61-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="70b61-110">Následující příklad ukazuje, jak zjistit, jestli návratový typ metody je obecný <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="70b61-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="70b61-111">Předpokládejme, že je metoda instance MethodInfo typu:</span><span class="sxs-lookup"><span data-stu-id="70b61-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```csharp  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="70b61-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="70b61-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="70b61-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="70b61-113">Example</span></span>  
 <span data-ttu-id="70b61-114">Tento příklad používá <xref:System.Object.GetType%2A> metodu pro určení typu, který se používá pro jiné výsledek číselné výpočtu.</span><span class="sxs-lookup"><span data-stu-id="70b61-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="70b61-115">To závisí na požadavky na úložiště z výsledné číslo.</span><span class="sxs-lookup"><span data-stu-id="70b61-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="70b61-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70b61-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="70b61-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="70b61-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="70b61-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70b61-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="70b61-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="70b61-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="70b61-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70b61-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="70b61-121">is</span><span class="sxs-lookup"><span data-stu-id="70b61-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="70b61-122">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="70b61-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
