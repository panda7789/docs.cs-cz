---
title: Automaticky implementované vlastnosti – průvodce programováním jazyka C#
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 791455c1eaef752da2b551e20187d390ca6c65e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170322"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="5352b-102">Automaticky implementované vlastnosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5352b-102">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="5352b-103">V C# 3.0 a novější, automaticky implementované vlastnosti, aby deklarace vlastnosti stručnější, když není vyžadována žádná další logika v přístupové objekty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5352b-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="5352b-104">Umožňují také klientský kód k vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="5352b-104">They also enable client code to create objects.</span></span> <span data-ttu-id="5352b-105">Když deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří `get` soukromé `set` anonymní doprovodné pole, ke kterému lze přistupovat pouze prostřednictvím přístupových objektů vlastnosti a přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="5352b-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="5352b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5352b-106">Example</span></span>

<span data-ttu-id="5352b-107">Následující příklad ukazuje jednoduchou třídu, která má některé automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="5352b-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="5352b-108">V rozhraních nelze deklarovat automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5352b-108">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="5352b-109">Automaticky implementované vlastnosti deklarují pole pro zálohování privátní instance a rozhraní nesmí deklarovat pole instancí.</span><span class="sxs-lookup"><span data-stu-id="5352b-109">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="5352b-110">Deklarování vlastnost v rozhraní bez definování těla deklaruje vlastnost s přístupové objekty, které musí být implementovány každý typ, který implementuje toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5352b-110">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="5352b-111">V C# 6 a novějších můžete inicializovat automaticky implementované vlastnosti podobně jako pole:</span><span class="sxs-lookup"><span data-stu-id="5352b-111">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  

```csharp  
public string FirstName { get; set; } = "Jane";  
```  

<span data-ttu-id="5352b-112">Třída, která je zobrazena v předchozím příkladu je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="5352b-112">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="5352b-113">Kód klienta můžete změnit hodnoty v objektech po vytvoření.</span><span class="sxs-lookup"><span data-stu-id="5352b-113">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="5352b-114">Ve složitých třídách, které obsahují významné chování (metody) i data, je často nutné mít veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5352b-114">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="5352b-115">Však pro malé třídy nebo struktury, které právě zapouzdřují sadu hodnot (data) a mají malé nebo žádné chování, měli byste buď objekty neměnné deklarováním set přistupujícího objektu jako [soukromé](../../language-reference/keywords/private.md) (neměnné pro spotřebitele) nebo deklarováním pouze get přistupujícího objektu (neměnné všude kromě konstruktoru).</span><span class="sxs-lookup"><span data-stu-id="5352b-115">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="5352b-116">Další informace naleznete v [tématu Jak implementovat zjednodušenou třídu s automaticky implementovanými vlastnostmi](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5352b-116">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5352b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5352b-117">See also</span></span>

- [<span data-ttu-id="5352b-118">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5352b-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="5352b-119">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="5352b-119">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
