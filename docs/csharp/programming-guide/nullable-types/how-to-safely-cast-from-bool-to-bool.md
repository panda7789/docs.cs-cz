---
title: "Postupy: Bezpečné přetypování z typu bool? na bool (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a6fa65c15bb5f1da9960dbc17bd25b4087ab862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a><span data-ttu-id="4770b-102">Postupy: Bezpečné přetypování z typu bool? na bool (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4770b-102">How to: Safely Cast from bool? to bool (C# Programming Guide)</span></span>
<span data-ttu-id="4770b-103">`bool?` Typ s možnou hodnotou Null může obsahovat tři různé hodnoty: `true`, `false`, a `null`.</span><span class="sxs-lookup"><span data-stu-id="4770b-103">The `bool?` nullable type can contain three different values: `true`, `false`, and `null`.</span></span> <span data-ttu-id="4770b-104">Proto `bool?` typ nelze použít v podmíněné příkazy, jako s `if`, `for`, nebo `while`.</span><span class="sxs-lookup"><span data-stu-id="4770b-104">Therefore, the `bool?` type cannot be used in conditionals such as with `if`, `for`, or `while`.</span></span> <span data-ttu-id="4770b-105">Chyba kompilátoru způsobí například následující kód.</span><span class="sxs-lookup"><span data-stu-id="4770b-105">For example, the following code causes a compiler error.</span></span>  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 <span data-ttu-id="4770b-106">To není povoleno, protože je při tom nejasné co `null` znamená v kontextu podmíněného.</span><span class="sxs-lookup"><span data-stu-id="4770b-106">This is not allowed because it is unclear what `null` means in the context of a conditional.</span></span> <span data-ttu-id="4770b-107">Použít `bool?` v podmíněného výrazu, nejprve zkontrolujte jeho <xref:System.Nullable%601.HasValue%2A> vlastnost zajistit, že její hodnota není `null`a pak vysílat `bool`.</span><span class="sxs-lookup"><span data-stu-id="4770b-107">To use a `bool?` in a conditional statement, first check its <xref:System.Nullable%601.HasValue%2A> property to ensure that its value is not `null`, and then cast it to `bool`.</span></span> <span data-ttu-id="4770b-108">Další informace najdete v tématu [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="4770b-108">For more information, see [bool](../../../csharp/language-reference/keywords/bool.md).</span></span> <span data-ttu-id="4770b-109">Pokud provádíte přetypování na `bool?` s hodnotou `null`, <xref:System.InvalidOperationException> bude vyvolána v podmíněného testu.</span><span class="sxs-lookup"><span data-stu-id="4770b-109">If you perform the cast on a `bool?` with a value of `null`, a <xref:System.InvalidOperationException> will be thrown in the conditional test.</span></span> <span data-ttu-id="4770b-110">Následující příklad ukazuje jeden ze způsobů bezpečné přetypování z `bool?` k `bool`:</span><span class="sxs-lookup"><span data-stu-id="4770b-110">The following example shows one way to safely cast from `bool?` to `bool`:</span></span>  
  
## <a name="example"></a><span data-ttu-id="4770b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4770b-111">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4770b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4770b-112">See Also</span></span>  
 [<span data-ttu-id="4770b-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4770b-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4770b-114">Literálová klíčová slova</span><span class="sxs-lookup"><span data-stu-id="4770b-114">Literal Keywords</span></span>](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [<span data-ttu-id="4770b-115">Typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="4770b-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="4770b-116">?? Operátor</span><span class="sxs-lookup"><span data-stu-id="4770b-116">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)
