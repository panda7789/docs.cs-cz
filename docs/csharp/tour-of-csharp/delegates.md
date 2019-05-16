---
title: C#Delegáti – připravuje C# jazyka
description: Přečtěte si pozdní vazbu s C# delegátů
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 35a1e212b50e77eb43271a657c8abb21eb6cfb4a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634637"
---
# <a name="delegates"></a><span data-ttu-id="a10b8-103">Delegáty</span><span class="sxs-lookup"><span data-stu-id="a10b8-103">Delegates</span></span>

<span data-ttu-id="a10b8-104">A ***typ delegáta*** seznamu představuje odkazy na metody pomocí konkrétních parametrů a návratový typ.</span><span class="sxs-lookup"><span data-stu-id="a10b8-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="a10b8-105">Delegáty umožňují považovat za entity, které může být přiřazena k proměnné a předány jako parametry metod.</span><span class="sxs-lookup"><span data-stu-id="a10b8-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="a10b8-106">Delegáti jsou podobný koncept ukazatelů na funkce v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce, Delegáti jsou objektově orientované a typově bezpečné.</span><span class="sxs-lookup"><span data-stu-id="a10b8-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="a10b8-107">Následující příklad deklaruje a používá typ delegáta s názvem `Function`.</span><span class="sxs-lookup"><span data-stu-id="a10b8-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="a10b8-108">Instance `Function` typ delegáta může odkazovat na jakoukoli metodu, která přijímá `double` argument a vrátí `double` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a10b8-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="a10b8-109">`Apply` Metoda použije danou funkci na elementy `double[]`, vrácení `double[]` s výsledky.</span><span class="sxs-lookup"><span data-stu-id="a10b8-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="a10b8-110">V `Main` metody `Apply` slouží k použití tří různých funkcí `double[]`.</span><span class="sxs-lookup"><span data-stu-id="a10b8-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="a10b8-111">Delegát může odkazovat na statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu) nebo metodu instance (například `m.Multiply` v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="a10b8-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="a10b8-112">Delegát, který odkazuje na metodu instance také odkazuje na konkrétní objekt, a když uživatel vyvolá metodu instance prostřednictvím delegáta, tento objekt se stane `this` ve volání.</span><span class="sxs-lookup"><span data-stu-id="a10b8-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="a10b8-113">Delegáty lze vytvořit také pomocí anonymní funkce, které jsou "inline metod", které jsou vytvořeny v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="a10b8-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="a10b8-114">Anonymní funkce můžete zobrazit místní proměnné okolního metody.</span><span class="sxs-lookup"><span data-stu-id="a10b8-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="a10b8-115">Díky tomu se výše uvedený příklad multiplikátor může být zapsán snadněji bez použití multiplikátor třídy:</span><span class="sxs-lookup"><span data-stu-id="a10b8-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="a10b8-116">Zajímavé a užitečné vlastnictví delegáta je, že ho neznáte nebo postaral o třídě, na které odkazuje; metody vše, co je důležité je, že odkazované metody má stejné parametry a návratový typ jako delegát.</span><span class="sxs-lookup"><span data-stu-id="a10b8-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a10b8-117">[Předchozí](enums.md)
>[další](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="a10b8-117">[Previous](enums.md)
[Next](attributes.md)</span></span>
