---
title: C# delegáti - přehled používání jazyka C#
description: Další informace pozdní vazba s C# delegáti
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 1dcd078b275d951b049b0c5bb6e084a4083d042d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360567"
---
# <a name="delegates"></a><span data-ttu-id="e3351-103">Delegáty</span><span class="sxs-lookup"><span data-stu-id="e3351-103">Delegates</span></span>

<span data-ttu-id="e3351-104">A ***delegovat typ*** seznamu představuje odkazy na metody s konkrétní parametr a návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="e3351-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="e3351-105">Delegáti umožňují považovat za entit, které může být přiřazena k proměnné a předány jako parametry metody.</span><span class="sxs-lookup"><span data-stu-id="e3351-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="e3351-106">Delegáti jsou podobná koncept ukazatelů na funkce najít v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce, jsou delegáti objektově orientované a bezpečnost typů.</span><span class="sxs-lookup"><span data-stu-id="e3351-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="e3351-107">Následující příklad deklaruje a používá typ delegáta s názvem `Function`.</span><span class="sxs-lookup"><span data-stu-id="e3351-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="e3351-108">Instance `Function` typ delegáta může odkazovat všechny metody, která přijímá `double` argument a vrátí `double` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e3351-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="e3351-109">`Apply` Metoda platí pro elementy danou funkci `double[]`, vracejících `double[]` s výsledky.</span><span class="sxs-lookup"><span data-stu-id="e3351-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="e3351-110">V `Main` metody `Apply` se používá k aplikování tři různé funkce `double[]`.</span><span class="sxs-lookup"><span data-stu-id="e3351-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="e3351-111">Delegáta může odkazovat buď statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu) nebo metodu instance (například `m.Multiply` v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="e3351-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="e3351-112">Delegát, který odkazuje na metodu instance také odkazuje na konkrétní objekt, a když prostřednictvím delegáta je volána metoda instance, stane se tento objekt `this` v volání.</span><span class="sxs-lookup"><span data-stu-id="e3351-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="e3351-113">Delegáti lze vytvořit také pomocí anonymní funkce, které jsou "vložené metody", které jsou vytvořené za chodu.</span><span class="sxs-lookup"><span data-stu-id="e3351-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="e3351-114">Anonymní funkce můžete zobrazit místní proměnné okolního metody.</span><span class="sxs-lookup"><span data-stu-id="e3351-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="e3351-115">Proto je možné v předchozím příkladu násobitel zapsat snadněji bez použití třídy násobitel:</span><span class="sxs-lookup"><span data-stu-id="e3351-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="e3351-116">Podle zajímavé a užitečné vlastnosti delegáta je, že ho není vědět, nebo jsou pro vás o třídě metody, na které odkazuje; všechno, co záleží je, že má metodu odkazované stejnými parametry a návratový typ jako delegát.</span><span class="sxs-lookup"><span data-stu-id="e3351-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e3351-117">[Předchozí](enums.md)
[další](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="e3351-117">[Previous](enums.md)
[Next](attributes.md)</span></span>
