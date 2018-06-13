---
title: const (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- const_CSharpKeyword
- const
helpviewer_keywords:
- const keyword [C#]
ms.assetid: 79eb447c-117b-4418-933f-97c50aa472db
ms.openlocfilehash: 0038c1472964e618ee52ded9731fcb3e1e3ca204
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216243"
---
# <a name="const-c-reference"></a><span data-ttu-id="8dac1-102">const (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8dac1-102">const (C# Reference)</span></span>
<span data-ttu-id="8dac1-103">Můžete použít `const` – klíčové slovo deklarace konstantní pole nebo konstantní místní.</span><span class="sxs-lookup"><span data-stu-id="8dac1-103">You use the `const` keyword to declare a constant field or a constant local.</span></span> <span data-ttu-id="8dac1-104">Konstantní pole a místní hodnoty nejsou proměnné a nejde ho upravit.</span><span class="sxs-lookup"><span data-stu-id="8dac1-104">Constant fields and locals aren't variables and may not be modified.</span></span> <span data-ttu-id="8dac1-105">Konstanty mohou obsahovat čísla, logické hodnoty, řetězce nebo odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="8dac1-105">Constants can be numbers, Boolean values, strings, or a null reference.</span></span> <span data-ttu-id="8dac1-106">Nevytvářejte konstanta představují informace, které byste měli kdykoli změnit.</span><span class="sxs-lookup"><span data-stu-id="8dac1-106">Don’t create a constant to represent information that you expect to change at any time.</span></span> <span data-ttu-id="8dac1-107">Například nepoužívejte konstantní pole k uložení ceny služby, číslo verze produktu nebo název značky společnosti.</span><span class="sxs-lookup"><span data-stu-id="8dac1-107">For example, don’t use a constant field to store the price of a service, a product version number, or the brand name of a company.</span></span> <span data-ttu-id="8dac1-108">Tyto hodnoty můžete změnit v čase, a protože kompilátory rozšířit konstanty, jiný kód, kompilovat s vaší knihovny bude muset být překompilovat, aby se změny projevily.</span><span class="sxs-lookup"><span data-stu-id="8dac1-108">These values can change over time, and because compilers propagate constants, other code compiled with your libraries will have to be recompiled to see the changes.</span></span> <span data-ttu-id="8dac1-109">Viz také [jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8dac1-109">See also the [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword.</span></span> <span data-ttu-id="8dac1-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8dac1-110">For example:</span></span>  
  
```csharp
const int x = 0;  
public const double gravitationalConstant = 6.673e-11;  
private const string productName = "Visual C#";  
```  
  
## <a name="remarks"></a><span data-ttu-id="8dac1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8dac1-111">Remarks</span></span>  
 <span data-ttu-id="8dac1-112">Typ deklarace konstanty Určuje typ členy, kteří zavádí deklaraci.</span><span class="sxs-lookup"><span data-stu-id="8dac1-112">The type of a constant declaration specifies the type of the members that the declaration introduces.</span></span> <span data-ttu-id="8dac1-113">Inicializátor konstanta místní nebo konstantní pole musí být konstantní výraz, který lze implicitně převést na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="8dac1-113">The initializer of a constant local or a constant field must be a constant expression that can be implicitly converted to the target type.</span></span>  
  
 <span data-ttu-id="8dac1-114">Konstantní výraz je výraz, který může být plně vyhodnocen v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="8dac1-114">A constant expression is an expression that can be fully evaluated at compile time.</span></span> <span data-ttu-id="8dac1-115">Proto možné pouze hodnoty pro konstanty odkazové typy jsou `string` a odkaz s hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="8dac1-115">Therefore, the only possible values for constants of reference types are `string` and a null reference.</span></span>  
  
 <span data-ttu-id="8dac1-116">Deklarace konstanty můžou deklarovat několik konstanty, jako například:</span><span class="sxs-lookup"><span data-stu-id="8dac1-116">The constant declaration can declare multiple constants, such as:</span></span>  
  
```csharp
public const double x = 1.0, y = 2.0, z = 3.0;  
```  
  
 <span data-ttu-id="8dac1-117">`static` Modifikátor není povolen v deklaraci konstantní.</span><span class="sxs-lookup"><span data-stu-id="8dac1-117">The `static` modifier is not allowed in a constant declaration.</span></span>  
  
 <span data-ttu-id="8dac1-118">Konstanta mohl účastnit konstantní výraz, následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8dac1-118">A constant can participate in a constant expression, as follows:</span></span>  
  
```csharp
public const int c1 = 5;  
public const int c2 = c1 + 100;  
```  
  
> [!NOTE]
>  <span data-ttu-id="8dac1-119">[Jen pro čtení](../../../csharp/language-reference/keywords/readonly.md) – klíčové slovo se liší od `const` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8dac1-119">The [readonly](../../../csharp/language-reference/keywords/readonly.md) keyword differs from the `const` keyword.</span></span> <span data-ttu-id="8dac1-120">A `const` pole lze inicializovat pouze na deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="8dac1-120">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="8dac1-121">A `readonly` pole jde inicializovat na deklaraci nebo v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8dac1-121">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="8dac1-122">Proto `readonly` pole může mít různé hodnoty v závislosti na konstruktoru použít.</span><span class="sxs-lookup"><span data-stu-id="8dac1-122">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="8dac1-123">Také i když `const` pole je argumentem konstanta kompilaci `readonly` pole lze použít pro spuštění konstanty, stejně jako tento řádek: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span><span class="sxs-lookup"><span data-stu-id="8dac1-123">Also, although a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants, as in this line: `public static readonly uint l1 = (uint)DateTime.Now.Ticks;`</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dac1-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="8dac1-124">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="8dac1-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="8dac1-125">Example</span></span>  
 <span data-ttu-id="8dac1-126">Tento příklad ukazuje, jak používat konstanty jako místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="8dac1-126">This example demonstrates how to use constants as local variables.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/const_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8dac1-127">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8dac1-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8dac1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8dac1-128">See Also</span></span>  
 [<span data-ttu-id="8dac1-129">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8dac1-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8dac1-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8dac1-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8dac1-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8dac1-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8dac1-132">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="8dac1-132">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="8dac1-133">readonly</span><span class="sxs-lookup"><span data-stu-id="8dac1-133">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)
