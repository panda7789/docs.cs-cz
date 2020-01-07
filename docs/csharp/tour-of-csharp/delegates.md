---
title: C#Delegáti – prohlídka C# jazyka
description: Přečtěte si pozdní C# vazbu s delegáty
ms.date: 08/10/2016
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: 317d3ee6fb1350824fa9b3b4d0e3e851780ce4d4
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346868"
---
# <a name="delegates"></a><span data-ttu-id="00b1d-103">Delegáti</span><span class="sxs-lookup"><span data-stu-id="00b1d-103">Delegates</span></span>

<span data-ttu-id="00b1d-104">***Typ delegáta*** představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="00b1d-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="00b1d-105">Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry.</span><span class="sxs-lookup"><span data-stu-id="00b1d-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="00b1d-106">Delegáti jsou podobní pojmu ukazatelů na funkce nalezené v některých jiných jazycích, ale na rozdíl od ukazatelů na funkce jsou delegáti objektově orientované a typově bezpečné.</span><span class="sxs-lookup"><span data-stu-id="00b1d-106">Delegates are similar to the concept of function pointers found in some other languages, but unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="00b1d-107">Následující příklad deklaruje a používá typ delegáta s názvem `Function`.</span><span class="sxs-lookup"><span data-stu-id="00b1d-107">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="00b1d-108">Instance typu delegáta `Function` může odkazovat na jakoukoli metodu, která přebírá `double` argument a vrací hodnotu `double`.</span><span class="sxs-lookup"><span data-stu-id="00b1d-108">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="00b1d-109">Metoda `Apply` použije danou funkci na prvky `double[]`a vrátí `double[]` s výsledky.</span><span class="sxs-lookup"><span data-stu-id="00b1d-109">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="00b1d-110">V metodě `Main` se `Apply` používá k použití tří různých funkcí na `double[]`.</span><span class="sxs-lookup"><span data-stu-id="00b1d-110">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="00b1d-111">Delegát může odkazovat buď na statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu), nebo na metodu instance (například `m.Multiply` v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="00b1d-111">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="00b1d-112">Delegát, který odkazuje na metodu instance, také odkazuje na konkrétní objekt a když je metoda instance vyvolána prostřednictvím delegáta, objekt se ve vyvolání `this`.</span><span class="sxs-lookup"><span data-stu-id="00b1d-112">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="00b1d-113">Delegáty je také možné vytvořit pomocí anonymních funkcí, což jsou "vložené metody", které jsou vytvářeny průběžně.</span><span class="sxs-lookup"><span data-stu-id="00b1d-113">Delegates can also be created using anonymous functions, which are "inline methods" that are created on the fly.</span></span> <span data-ttu-id="00b1d-114">Anonymní funkce mohou zobrazit místní proměnné okolních metod.</span><span class="sxs-lookup"><span data-stu-id="00b1d-114">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="00b1d-115">Proto je příklad násobitele výše možné napsat snadněji bez použití třídy násobitele:</span><span class="sxs-lookup"><span data-stu-id="00b1d-115">Thus, the multiplier example above can be written more easily without using a Multiplier class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="00b1d-116">Zajímavou a užitečnou vlastností delegáta je, že neznají ani nezáleží na třídě metody, na kterou odkazuje; všechny tyto věci jsou, že odkazovaná metoda má stejné parametry a návratový typ jako delegát.</span><span class="sxs-lookup"><span data-stu-id="00b1d-116">An interesting and useful property of a delegate is that it does not know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="00b1d-117">[Předchozí](interfaces.md)
>[Další](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="00b1d-117">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
