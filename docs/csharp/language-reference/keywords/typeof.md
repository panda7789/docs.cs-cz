---
title: "typeof (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords: typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: be24740ea7f6fbe8780dd9cac58b7dea9aaf6872
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-c-reference"></a><span data-ttu-id="4e2be-102">typeof (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4e2be-102">typeof (C# Reference)</span></span>
<span data-ttu-id="4e2be-103">Použít k získání `System.Type` objektu pro typ.</span><span class="sxs-lookup"><span data-stu-id="4e2be-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="4e2be-104">A `typeof` výraz má následující podobu:</span><span class="sxs-lookup"><span data-stu-id="4e2be-104">A `typeof` expression takes the following form:</span></span>  
  
```  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="4e2be-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e2be-105">Remarks</span></span>  
 <span data-ttu-id="4e2be-106">Pokud chcete získat běhového typu výrazu, můžete použít metodu rozhraní .NET Framework <xref:System.Object.GetType%2A>, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4e2be-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="4e2be-107">`typeof` Operátor nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="4e2be-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="4e2be-108">`typeof` Operátor můžete použít taky u otevřete obecné typy.</span><span class="sxs-lookup"><span data-stu-id="4e2be-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="4e2be-109">Typy s více než jeden parametr typu musí mít odpovídající počet čárky ve specifikaci.</span><span class="sxs-lookup"><span data-stu-id="4e2be-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="4e2be-110">Následující příklad ukazuje, jak určit, zda je návratový typ metody obecný <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="4e2be-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="4e2be-111">Předpokládejme, že metoda instance typu MethodInfo:</span><span class="sxs-lookup"><span data-stu-id="4e2be-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="4e2be-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e2be-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="4e2be-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e2be-113">Example</span></span>  
 <span data-ttu-id="4e2be-114">V tomto příkladu <xref:System.Object.GetType%2A> metoda určit typ, který se používá pro jiné výsledek číselný výpočet.</span><span class="sxs-lookup"><span data-stu-id="4e2be-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="4e2be-115">To závisí na požadavky na úložiště výsledné číslo.</span><span class="sxs-lookup"><span data-stu-id="4e2be-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="4e2be-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e2be-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4e2be-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e2be-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="4e2be-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e2be-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4e2be-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4e2be-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4e2be-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e2be-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4e2be-121">je</span><span class="sxs-lookup"><span data-stu-id="4e2be-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="4e2be-122">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="4e2be-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
