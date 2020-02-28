---
title: C#Delegáti – prohlídka C# jazyka
description: Přečtěte si pozdní C# vazbu s delegáty
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159166"
---
# <a name="delegates"></a><span data-ttu-id="34f86-103">Delegáty</span><span class="sxs-lookup"><span data-stu-id="34f86-103">Delegates</span></span>

<span data-ttu-id="34f86-104">***Typ delegáta*** představuje odkazy na metody s konkrétním seznamem parametrů a návratovým typem.</span><span class="sxs-lookup"><span data-stu-id="34f86-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="34f86-105">Delegáti umožňují zacházet s metodami jako s entitami, které lze přiřadit proměnným a předávat jako parametry.</span><span class="sxs-lookup"><span data-stu-id="34f86-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="34f86-106">Delegáti jsou podobní pojmu ukazatelů na funkce nalezených v některých jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="34f86-106">Delegates are similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="34f86-107">Na rozdíl od ukazatelů na funkce jsou delegáti objektově orientovaný a typově bezpečný.</span><span class="sxs-lookup"><span data-stu-id="34f86-107">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="34f86-108">Následující příklad deklaruje a používá typ delegáta s názvem `Function`.</span><span class="sxs-lookup"><span data-stu-id="34f86-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="34f86-109">Instance typu delegáta `Function` může odkazovat na jakoukoli metodu, která přebírá `double` argument a vrací hodnotu `double`.</span><span class="sxs-lookup"><span data-stu-id="34f86-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="34f86-110">Metoda `Apply` použije danou funkci na prvky `double[]`a vrátí `double[]` s výsledky.</span><span class="sxs-lookup"><span data-stu-id="34f86-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="34f86-111">V metodě `Main` se `Apply` používá k použití tří různých funkcí na `double[]`.</span><span class="sxs-lookup"><span data-stu-id="34f86-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="34f86-112">Delegát může odkazovat buď na statickou metodu (například `Square` nebo `Math.Sin` v předchozím příkladu), nebo na metodu instance (například `m.Multiply` v předchozím příkladu).</span><span class="sxs-lookup"><span data-stu-id="34f86-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="34f86-113">Delegát, který odkazuje na metodu instance, také odkazuje na konkrétní objekt a když je metoda instance vyvolána prostřednictvím delegáta, objekt se ve vyvolání `this`.</span><span class="sxs-lookup"><span data-stu-id="34f86-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="34f86-114">Delegáty lze také vytvořit pomocí anonymních funkcí, což jsou "vložené metody", které jsou vytvořeny při deklaraci.</span><span class="sxs-lookup"><span data-stu-id="34f86-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created when declared.</span></span> <span data-ttu-id="34f86-115">Anonymní funkce mohou zobrazit místní proměnné okolních metod.</span><span class="sxs-lookup"><span data-stu-id="34f86-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="34f86-116">Následující příklad nevytvoří třídu:</span><span class="sxs-lookup"><span data-stu-id="34f86-116">The following example doesn't create a class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="34f86-117">Delegát neví ani nezáleží na třídě metody, na kterou odkazuje; všechny tyto věci jsou, že odkazovaná metoda má stejné parametry a návratový typ jako delegát.</span><span class="sxs-lookup"><span data-stu-id="34f86-117">A delegate doesn't know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="34f86-118">[Předchozí](interfaces.md)
>[Další](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="34f86-118">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
