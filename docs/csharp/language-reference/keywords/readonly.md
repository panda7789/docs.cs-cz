---
title: readonly – modifikátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: d2f8a2f192dc319ad806aeef4bfbaeecc44b07a3
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172630"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="7f574-102">readonly – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7f574-102">readonly (C# Reference)</span></span>
<span data-ttu-id="7f574-103">`readonly` – Klíčové slovo je modifikátor, který můžete použít na pole.</span><span class="sxs-lookup"><span data-stu-id="7f574-103">The `readonly` keyword is a modifier that you can use on fields.</span></span> <span data-ttu-id="7f574-104">Pokud obsahuje deklaraci pole `readonly` modifikátor, přiřazení pole zaváděné deklaraci může dojít pouze v rámci deklarace nebo v konstruktoru ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="7f574-104">When a field declaration includes a `readonly` modifier, assignments to the fields introduced by the declaration can only occur as part of the declaration or in a constructor in the same class.</span></span>  
  
## <a name="readonly-field-example"></a><span data-ttu-id="7f574-105">Pole jen pro čtení, například</span><span class="sxs-lookup"><span data-stu-id="7f574-105">Readonly field example</span></span>  
 <span data-ttu-id="7f574-106">V tomto příkladu hodnota v poli `year` nelze změnit v metodě `ChangeYear`, i když je přiřazen hodnotu v konstruktoru třídy:</span><span class="sxs-lookup"><span data-stu-id="7f574-106">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 <span data-ttu-id="7f574-107">Můžete přiřadit hodnotu na `readonly` pouze v kontextech následující pole:</span><span class="sxs-lookup"><span data-stu-id="7f574-107">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
-   <span data-ttu-id="7f574-108">Pokud proměnná je inicializován v deklaraci, například:</span><span class="sxs-lookup"><span data-stu-id="7f574-108">When the variable is initialized in the declaration, for example:</span></span>  
  
    ```csharp  
    public readonly int y = 5;  
    ```  
  
-   <span data-ttu-id="7f574-109">V konstruktorech instance třídy pro pole instance, která obsahuje deklaraci pole nebo pro statické pole na statického konstruktoru třídy, která obsahuje deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="7f574-109">For an instance field, in the instance constructors of the class that contains the field declaration, or for a static field, in the static constructor of the class that contains the field declaration.</span></span> <span data-ttu-id="7f574-110">Existují i pouze kontexty, ve kterých je platná pro předávání `readonly` jako pole [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) nebo [ref](../../../csharp/language-reference/keywords/ref.md) parametr.</span><span class="sxs-lookup"><span data-stu-id="7f574-110">These are also the only contexts in which it is valid to pass a `readonly` field as an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) or [ref](../../../csharp/language-reference/keywords/ref.md) parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f574-111">`readonly` – Klíčové slovo se liší od [const](../../../csharp/language-reference/keywords/const.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7f574-111">The `readonly` keyword is different from the [const](../../../csharp/language-reference/keywords/const.md) keyword.</span></span> <span data-ttu-id="7f574-112">A `const` pole lze inicializovat pouze na deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="7f574-112">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="7f574-113">A `readonly` pole jde inicializovat na deklaraci nebo v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7f574-113">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="7f574-114">Proto `readonly` pole může mít různé hodnoty v závislosti na konstruktoru použít.</span><span class="sxs-lookup"><span data-stu-id="7f574-114">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="7f574-115">Navíc při `const` pole je argumentem konstanta kompilaci `readonly` pole lze použít pro modul runtime konstanty jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7f574-115">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  
  
```csharp  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="comparing-readonly-and-non-readonly-instance-fields"></a><span data-ttu-id="7f574-116">Porovnání instance pole jen pro čtení a jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7f574-116">Comparing readonly and non-readonly instance fields</span></span>  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 <span data-ttu-id="7f574-117">V předchozím příkladu, pokud použijete příkaz takto:</span><span class="sxs-lookup"><span data-stu-id="7f574-117">In the preceding example, if you use a statement like this:</span></span>  
  
 `p2.y = 66;        // Error`  
  
 <span data-ttu-id="7f574-118">Zobrazí se chybová zpráva kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="7f574-118">you will get the compiler error message:</span></span>  
  
 `The left-hand side of an assignment must be an l-value`  
  
 <span data-ttu-id="7f574-119">což je ke stejné chybě, kterou získáte, když se pokusí přiřadit hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="7f574-119">which is the same error you get when you attempt to assign a value to a constant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="7f574-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7f574-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f574-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f574-121">See Also</span></span>  
 [<span data-ttu-id="7f574-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7f574-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7f574-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7f574-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7f574-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7f574-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7f574-125">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="7f574-125">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="7f574-126">const</span><span class="sxs-lookup"><span data-stu-id="7f574-126">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="7f574-127">Pole</span><span class="sxs-lookup"><span data-stu-id="7f574-127">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)
