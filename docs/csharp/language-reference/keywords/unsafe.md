---
title: unsafe (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: c476bdcea4993b27c0e8f8148a985f18a43ba09b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171951"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="f4798-102">unsafe (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f4798-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="f4798-103">`unsafe` – Klíčové slovo označuje unsafe kontext, který je požadován pro všechny operace zahrnutí ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="f4798-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="f4798-104">Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4798-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="f4798-105">Můžete použít `unsafe` modifikátor v deklaraci typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="f4798-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="f4798-106">Textové celý rozsah typ nebo člen za nebezpečné kontextu.</span><span class="sxs-lookup"><span data-stu-id="f4798-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="f4798-107">Například následující je metoda deklarovat s `unsafe` modifikátor:</span><span class="sxs-lookup"><span data-stu-id="f4798-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```csharp  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="f4798-108">Rozsah kontext unsafe rozšiřuje ze seznamu parametrů na konec metody, takže ukazatele lze také použít v seznamu parametrů:</span><span class="sxs-lookup"><span data-stu-id="f4798-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```csharp  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="f4798-109">Nezabezpečený bloku můžete taky povolit používání nezabezpečený kód v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="f4798-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="f4798-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f4798-110">For example:</span></span>  
  
```csharp  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="f4798-111">Nezabezpečený kód zkompilovat, je nutné zadat [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f4798-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="f4798-112">Nezabezpečený kód není zkontrolovat, že modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="f4798-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4798-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4798-113">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f4798-114">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f4798-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f4798-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4798-115">See Also</span></span>  
 [<span data-ttu-id="f4798-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f4798-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f4798-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f4798-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f4798-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f4798-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f4798-119">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="f4798-119">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="f4798-120">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="f4798-120">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="f4798-121">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="f4798-121">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
