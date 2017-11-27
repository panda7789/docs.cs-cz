---
title: "C# delegáti - přehled používání jazyka C#"
description: "Další informace pozdní vazba s C# delegáti"
keywords: "Rozhraní .NET, csharp, delegáta, lambda, pozdní vazba"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: bb304b2e5c762a44aab931b5e8f7fe9c99805eba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="delegates"></a><span data-ttu-id="2a319-104">Delegáty</span><span class="sxs-lookup"><span data-stu-id="2a319-104">Delegates</span></span>

<span data-ttu-id="2a319-105">A ***delegovat typ*** seznamu představuje odkazy na metody s konkrétní parametr a návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="2a319-105">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="2a319-106">Delegáti umožňují považovat za entit, které může být přiřazena k proměnné a předány jako parametry metody.</span><span class="sxs-lookup"><span data-stu-id="2a319-106">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="2a319-107">Delegáti jsou podobná koncept ukazatelů na funkce najít v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce, jsou delegáti objektově orientované a bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="2a319-107">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="2a319-108">Následující příklad deklaruje a používá typ delegáta s názvem `Function`.</span><span class="sxs-lookup"><span data-stu-id="2a319-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="2a319-109">Instance `Function` typ delegáta může odkazovat všechny metody, která přijímá `double` argument a vrátí `double` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2a319-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="2a319-110">`Apply` Metoda platí pro elementy danou funkci `double[]`, vracejících `double[]` s výsledky.</span><span class="sxs-lookup"><span data-stu-id="2a319-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="2a319-111">V `Main` metody `Apply` se používá k aplikování tři různé funkce `double[]`.</span><span class="sxs-lookup"><span data-stu-id="2a319-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="2a319-112">Delegáta může odkazovat buď statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu) nebo metodu instance (například `m.Multiply` v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="2a319-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="2a319-113">Delegát, který odkazuje na metodu instance také odkazuje na konkrétní objekt, a když prostřednictvím delegáta je volána metoda instance, stane se tento objekt `this` v volání.</span><span class="sxs-lookup"><span data-stu-id="2a319-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="2a319-114">Delegáti lze vytvořit také pomocí anonymní funkce, které jsou "vložené metody", které jsou vytvořené za chodu.</span><span class="sxs-lookup"><span data-stu-id="2a319-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="2a319-115">Anonymní funkce můžete zobrazit místní proměnné okolního metody.</span><span class="sxs-lookup"><span data-stu-id="2a319-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="2a319-116">Proto je možné v předchozím příkladu násobitel zapsat snadněji bez použití třídy násobitel:</span><span class="sxs-lookup"><span data-stu-id="2a319-116">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="2a319-117">Podle zajímavé a užitečné vlastnosti delegáta je, že ho není vědět, nebo jsou pro vás o třídě metody, na které odkazuje; všechno, co záleží je, že má metodu odkazované stejnými parametry a návratový typ jako delegát.</span><span class="sxs-lookup"><span data-stu-id="2a319-117">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="2a319-118">[Předchozí](enums.md)
[další](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="2a319-118">[Previous](enums.md)
[Next](attributes.md)</span></span>
