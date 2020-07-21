---
title: Automaticky implementované vlastnosti – Průvodce programováním v C#
description: Pro automaticky implementované vlastnosti v jazyce C# vytvoří complier soukromé, anonymní zálohovací pole přístupné pouze prostřednictvím přístupových objektů Get a set vlastnosti.
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: f58f9a23f26bde7e80d834528d94e38af1231e7b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474472"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="5a8c5-103">Automaticky implementované vlastnosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5a8c5-103">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="5a8c5-104">V C# 3,0 a novějších, automaticky implementované vlastnosti umožňují deklarace vlastností výstižnější, pokud v přístupových parametrech vlastností není žádná další logika.</span><span class="sxs-lookup"><span data-stu-id="5a8c5-104">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="5a8c5-105">Také umožňují, aby kód klienta vytvářel objekty.</span><span class="sxs-lookup"><span data-stu-id="5a8c5-105">They also enable client code to create objects.</span></span> <span data-ttu-id="5a8c5-106">Pokud deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří soukromé, anonymní zálohovací pole, které je přístupné pouze prostřednictvím vlastností `get` a `set` přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="5a8c5-106">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="5a8c5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a8c5-107">Example</span></span>

<span data-ttu-id="5a8c5-108">Následující příklad ukazuje jednoduchou třídu, která má některé automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="5a8c5-108">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="5a8c5-109">V rozhraních nemůžete deklarovat automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a8c5-109">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="5a8c5-110">Automaticky implementované vlastnosti deklarující pole pro zálohování privátní instance a rozhraní nedeklarují pole instance.</span><span class="sxs-lookup"><span data-stu-id="5a8c5-110">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="5a8c5-111">Deklarace vlastnosti v rozhraní bez definování těla deklaruje vlastnost s přístupovými objekty, které musí být implementovány pomocí každého typu, který toto rozhraní implementuje.</span><span class="sxs-lookup"><span data-stu-id="5a8c5-111">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="5a8c5-112">V C# 6 a novějších můžete inicializovat automaticky implementované vlastnosti podobně jako pole:</span><span class="sxs-lookup"><span data-stu-id="5a8c5-112">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="5a8c5-113">Třída, která je zobrazena v předchozím příkladu, je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="5a8c5-113">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="5a8c5-114">Kód klienta může po vytvoření změnit hodnoty v objektech.</span><span class="sxs-lookup"><span data-stu-id="5a8c5-114">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="5a8c5-115">V komplexních třídách, které obsahují významné chování (metody) a také data, je často nutné mít veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5a8c5-115">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="5a8c5-116">Pro malé třídy nebo struktury, které pouze zapouzdřují sadu hodnot (data) a mají malé nebo žádné chování, byste však měli objekty nastavit jako neměnné deklarováním přístupového objektu set jako [soukromého](../../language-reference/keywords/private.md) (neproměnlivé pro příjemce) nebo deklarováním pouze přístupového objektu Get (neproměnlivé všude kromě konstruktoru).</span><span class="sxs-lookup"><span data-stu-id="5a8c5-116">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="5a8c5-117">Další informace naleznete v tématu [jak implementovat odlehčenou třídu s automaticky implementovanými vlastnostmi](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5a8c5-117">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5a8c5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a8c5-118">See also</span></span>

- [<span data-ttu-id="5a8c5-119">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5a8c5-119">Properties</span></span>](./properties.md)
- [<span data-ttu-id="5a8c5-120">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="5a8c5-120">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
