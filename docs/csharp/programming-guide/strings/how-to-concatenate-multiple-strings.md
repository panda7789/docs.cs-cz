---
title: "Postupy: Řetězení více řetězců (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a><span data-ttu-id="e0b8d-102">Postupy: Řetězení více řetězců (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e0b8d-102">How to: Concatenate Multiple Strings (C# Programming Guide)</span></span>
<span data-ttu-id="e0b8d-103">*Zřetězení* je proces připojování jeden řetězec na konec jiným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-103">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="e0b8d-104">Když pomocí zřetězení textové literály nebo řetězcové konstanty `+` operátor, kompilátor vytvoří jeden řetězec.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-104">When you concatenate string literals or string constants by using the `+` operator, the compiler creates a single string.</span></span> <span data-ttu-id="e0b8d-105">Ne spustit, když dojde k zřetězení.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-105">No run time concatenation occurs.</span></span> <span data-ttu-id="e0b8d-106">Řetězec proměnné však může být zřetězen pouze za běhu.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-106">However, string variables can be concatenated only at run time.</span></span> <span data-ttu-id="e0b8d-107">V takovém případě byste měli porozumět vliv na výkon různých přístupů.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-107">In this case, you should understand the performance implications of the various approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0b8d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0b8d-108">Example</span></span>  
 <span data-ttu-id="e0b8d-109">Následující příklad ukazuje, jak rozdělit literálu dlouhý řetězec na menší řetězců za účelem zlepšení čitelnosti ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-109">The following example shows how to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="e0b8d-110">Tyto části bude zřetězen do jednoho řetězce v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="e0b8d-111">Už běží čas výkon, bez ohledu na počet řetězce související se situací.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-111">There is no run time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="e0b8d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0b8d-112">Example</span></span>  
 <span data-ttu-id="e0b8d-113">Ke zřetězení proměnné řetězce, můžete použít `+` nebo `+=` operátory, nebo <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-113">To concatenate string variables, you can use the `+` or `+=` operators, or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="e0b8d-114">`+` Operátor se snadno používá a zajišťuje intuitivní kódu.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-114">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="e0b8d-115">I když používáte několik + operátory v jednom příkazu, obsah řetězce zkopírován pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-115">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="e0b8d-116">Pokud tuto operaci opakovat několikrát, například ve smyčce, může ale způsobit efektivitu problémy.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-116">But if you repeat this operation multiple times, for example in a loop, it might cause efficiency problems.</span></span> <span data-ttu-id="e0b8d-117">Například vezměte na vědomí následující kód:</span><span class="sxs-lookup"><span data-stu-id="e0b8d-117">For example, note the following code:</span></span>  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="e0b8d-118">V operace s řetězci zřetězení kompilátor jazyka C# zpracovává řetězec null stejné jako prázdný řetězec, ale nepřevede hodnota řetězce původní hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-118">In string concatenation operations, the C# compiler treats a null string the same as an empty string, but it does not convert the value of the original null string.</span></span>  
  
 <span data-ttu-id="e0b8d-119">Pokud nejsou zřetězení velkého počtu řetězce (například ve smyčce), náklady na výkon tohoto kódu je pravděpodobně není důležité.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-119">If you are not concatenating large numbers of strings (for example, in a loop), the performance cost of this code is probably not significant.</span></span> <span data-ttu-id="e0b8d-120">Totéž platí pro <xref:System.String.Concat%2A?displayProperty=nameWithType> a <xref:System.String.Format%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-120">The same is true for the <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType> methods.</span></span>  
  
 <span data-ttu-id="e0b8d-121">Ale pokud výkonu je důležité, byste měli vždycky používat <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-121">However, when performance is important, you should always use the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span> <span data-ttu-id="e0b8d-122">Následující kód používá <xref:System.Text.StringBuilder.Append%2A> metodu <xref:System.Text.StringBuilder> třídy ke zřetězení řetězců bez řetězení účinku `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="e0b8d-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings without the chaining effect of the `+` operator.</span></span>  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e0b8d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0b8d-123">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="e0b8d-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e0b8d-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e0b8d-125">Řetězce</span><span class="sxs-lookup"><span data-stu-id="e0b8d-125">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
