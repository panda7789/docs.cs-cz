---
title: "readonly – modifikátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords: readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b499f9fc5121afe6c2e92bcf8c5d2ac593b4c06c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-c-reference"></a><span data-ttu-id="9cbf5-102">readonly – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9cbf5-102">readonly (C# Reference)</span></span>
<span data-ttu-id="9cbf5-103">`readonly` – Klíčové slovo je modifikátor, který můžete použít na pole.</span><span class="sxs-lookup"><span data-stu-id="9cbf5-103">The `readonly` keyword is a modifier that you can use on fields.</span></span> <span data-ttu-id="9cbf5-104">Pokud obsahuje deklaraci pole `readonly` modifikátor, přiřazení pole zaváděné deklaraci může dojít pouze v rámci deklarace nebo v konstruktoru ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="9cbf5-104">When a field declaration includes a `readonly` modifier, assignments to the fields introduced by the declaration can only occur as part of the declaration or in a constructor in the same class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cbf5-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cbf5-105">Example</span></span>  
 <span data-ttu-id="9cbf5-106">V tomto příkladu hodnota v poli `year` nelze změnit v metodě `ChangeYear`, i když je přiřazen hodnotu v konstruktoru třídy:</span><span class="sxs-lookup"><span data-stu-id="9cbf5-106">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 <span data-ttu-id="9cbf5-107">Můžete přiřadit hodnotu na `readonly` pouze v kontextech následující pole:</span><span class="sxs-lookup"><span data-stu-id="9cbf5-107">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
-   <span data-ttu-id="9cbf5-108">Pokud proměnná je inicializován v deklaraci, například:</span><span class="sxs-lookup"><span data-stu-id="9cbf5-108">When the variable is initialized in the declaration, for example:</span></span>  
  
    ```  
    public readonly int y = 5;  
    ```  
  
-   <span data-ttu-id="9cbf5-109">V konstruktorech instance třídy pro pole instance, která obsahuje deklaraci pole nebo pro statické pole na statického konstruktoru třídy, která obsahuje deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="9cbf5-109">For an instance field, in the instance constructors of the class that contains the field declaration, or for a static field, in the static constructor of the class that contains the field declaration.</span></span> <span data-ttu-id="9cbf5-110">Existují i pouze kontexty, ve kterých je platná pro předávání `readonly` jako pole [out](../../../csharp/language-reference/keywords/out.md) nebo [ref](../../../csharp/language-reference/keywords/ref.md) parametr.</span><span class="sxs-lookup"><span data-stu-id="9cbf5-110">These are also the only contexts in which it is valid to pass a `readonly` field as an [out](../../../csharp/language-reference/keywords/out.md) or [ref](../../../csharp/language-reference/keywords/ref.md) parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cbf5-111">`readonly` – Klíčové slovo se liší od [const](../../../csharp/language-reference/keywords/const.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="9cbf5-111">The `readonly` keyword is different from the [const](../../../csharp/language-reference/keywords/const.md) keyword.</span></span> <span data-ttu-id="9cbf5-112">A `const` pole lze inicializovat pouze na deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="9cbf5-112">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="9cbf5-113">A `readonly` pole jde inicializovat na deklaraci nebo v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="9cbf5-113">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="9cbf5-114">Proto `readonly` pole může mít různé hodnoty v závislosti na konstruktoru použít.</span><span class="sxs-lookup"><span data-stu-id="9cbf5-114">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="9cbf5-115">Navíc při `const` pole je argumentem konstanta kompilaci `readonly` pole lze použít pro modul runtime konstanty jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9cbf5-115">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  
  
```  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="example"></a><span data-ttu-id="9cbf5-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cbf5-116">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 <span data-ttu-id="9cbf5-117">V předchozím příkladu, pokud použijete příkaz takto:</span><span class="sxs-lookup"><span data-stu-id="9cbf5-117">In the preceding example, if you use a statement like this:</span></span>  
  
 `p2.y = 66;        // Error`  
  
 <span data-ttu-id="9cbf5-118">Zobrazí se chybová zpráva kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="9cbf5-118">you will get the compiler error message:</span></span>  
  
 `The left-hand side of an assignment must be an l-value`  
  
 <span data-ttu-id="9cbf5-119">což je ke stejné chybě, kterou získáte, když se pokusí přiřadit hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="9cbf5-119">which is the same error you get when you attempt to assign a value to a constant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9cbf5-120">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9cbf5-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9cbf5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cbf5-121">See Also</span></span>  
 [<span data-ttu-id="9cbf5-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9cbf5-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9cbf5-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9cbf5-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9cbf5-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9cbf5-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9cbf5-125">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="9cbf5-125">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="9cbf5-126">Const</span><span class="sxs-lookup"><span data-stu-id="9cbf5-126">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="9cbf5-127">Pole</span><span class="sxs-lookup"><span data-stu-id="9cbf5-127">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)
