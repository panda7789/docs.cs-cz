---
title: 'Postupy: Bezpečné přetypování z typu bool? na bool (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
ms.openlocfilehash: e04e34abd477730f9dd01486ec6bddcde4943edc
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457477"
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a><span data-ttu-id="7581f-102">Postupy: Bezpečné přetypování z typu bool? na bool (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="7581f-102">How to: Safely Cast from bool? to bool (C# Programming Guide)</span></span>
<span data-ttu-id="7581f-103">`bool?` Typ s možnou hodnotou Null může obsahovat tři různé hodnoty: `true`, `false`, a `null`.</span><span class="sxs-lookup"><span data-stu-id="7581f-103">The `bool?` nullable type can contain three different values: `true`, `false`, and `null`.</span></span> <span data-ttu-id="7581f-104">Proto `bool?` typ nelze použít v podmíněné příkazy, jako s `if`, `for`, nebo `while`.</span><span class="sxs-lookup"><span data-stu-id="7581f-104">Therefore, the `bool?` type cannot be used in conditionals such as with `if`, `for`, or `while`.</span></span> <span data-ttu-id="7581f-105">Chyba kompilátoru způsobí například následující kód.</span><span class="sxs-lookup"><span data-stu-id="7581f-105">For example, the following code causes a compiler error.</span></span>  
  
```csharp  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 <span data-ttu-id="7581f-106">To není povoleno, protože je při tom nejasné co `null` znamená v kontextu podmíněného.</span><span class="sxs-lookup"><span data-stu-id="7581f-106">This is not allowed because it is unclear what `null` means in the context of a conditional.</span></span> <span data-ttu-id="7581f-107">Použít `bool?` v podmíněného výrazu, nejprve zkontrolujte jeho <xref:System.Nullable%601.HasValue%2A> vlastnost zajistit, že její hodnota není `null`a pak vysílat `bool`.</span><span class="sxs-lookup"><span data-stu-id="7581f-107">To use a `bool?` in a conditional statement, first check its <xref:System.Nullable%601.HasValue%2A> property to ensure that its value is not `null`, and then cast it to `bool`.</span></span> <span data-ttu-id="7581f-108">Další informace najdete v tématu [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="7581f-108">For more information, see [bool](../../../csharp/language-reference/keywords/bool.md).</span></span> <span data-ttu-id="7581f-109">Pokud provádíte přetypování na `bool?` s hodnotou `null`, <xref:System.InvalidOperationException> bude vyvolána v podmíněného testu.</span><span class="sxs-lookup"><span data-stu-id="7581f-109">If you perform the cast on a `bool?` with a value of `null`, a <xref:System.InvalidOperationException> will be thrown in the conditional test.</span></span> <span data-ttu-id="7581f-110">Následující příklad ukazuje jeden ze způsobů bezpečné přetypování z `bool?` k `bool`:</span><span class="sxs-lookup"><span data-stu-id="7581f-110">The following example shows one way to safely cast from `bool?` to `bool`:</span></span>  
  
## <a name="example"></a><span data-ttu-id="7581f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="7581f-111">Example</span></span>  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7581f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7581f-112">See Also</span></span>  
 [<span data-ttu-id="7581f-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7581f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7581f-114">Literálová klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7581f-114">Literal Keywords</span></span>](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [<span data-ttu-id="7581f-115">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="7581f-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="7581f-116">?? – operátor</span><span class="sxs-lookup"><span data-stu-id="7581f-116">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
