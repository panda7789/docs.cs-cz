---
title: Automaticky implementované vlastnosti – C# Průvodce programováním
ms.date: 01/31/2020
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 989266bfc2de9bd5ce2948f09a2b9f19dd2c782e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628290"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="19ed1-102">Automaticky implementované vlastnosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="19ed1-102">Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="19ed1-103">V C# 3,0 a novějších se automaticky implementované vlastnosti přizpůsobují deklarace vlastnost, pokud se v přístupových parametrech vlastnosti nepožaduje žádná další logika.</span><span class="sxs-lookup"><span data-stu-id="19ed1-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="19ed1-104">Také umožňují, aby kód klienta vytvářel objekty.</span><span class="sxs-lookup"><span data-stu-id="19ed1-104">They also enable client code to create objects.</span></span> <span data-ttu-id="19ed1-105">Pokud deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří soukromé, anonymní zálohovací pole, které je přístupné pouze prostřednictvím `get` vlastností a přístupových objektů `set`.</span><span class="sxs-lookup"><span data-stu-id="19ed1-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>
  
## <a name="example"></a><span data-ttu-id="19ed1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="19ed1-106">Example</span></span>

<span data-ttu-id="19ed1-107">Následující příklad ukazuje jednoduchou třídu, která má některé automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="19ed1-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  

[!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  

<span data-ttu-id="19ed1-108">V rozhraních nemůžete deklarovat automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="19ed1-108">You can't declare auto-implemented properties in interfaces.</span></span> <span data-ttu-id="19ed1-109">Automaticky implementované vlastnosti deklarující pole pro zálohování privátní instance a rozhraní nedeklarují pole instance.</span><span class="sxs-lookup"><span data-stu-id="19ed1-109">Auto-implemented properties declare a private instance backing field, and interfaces may not declare instance fields.</span></span> <span data-ttu-id="19ed1-110">Deklarace vlastnosti v rozhraní bez definování těla deklaruje vlastnost s přístupovými objekty, které musí být implementovány pomocí každého typu, který toto rozhraní implementuje.</span><span class="sxs-lookup"><span data-stu-id="19ed1-110">Declaring a property in an interface without defining a body declares a property with accessors that must be implemented by each type that implements that interface.</span></span>

<span data-ttu-id="19ed1-111">V C# 6 a novějších verzích můžete inicializovat automaticky implementované vlastnosti podobně jako pole:</span><span class="sxs-lookup"><span data-stu-id="19ed1-111">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
 
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
 
<span data-ttu-id="19ed1-112">Třída, která je zobrazena v předchozím příkladu, je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="19ed1-112">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="19ed1-113">Kód klienta může po vytvoření změnit hodnoty v objektech.</span><span class="sxs-lookup"><span data-stu-id="19ed1-113">Client code can change the values in objects after creation.</span></span> <span data-ttu-id="19ed1-114">V komplexních třídách, které obsahují významné chování (metody) a také data, je často nutné mít veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="19ed1-114">In complex classes that contain significant behavior (methods) as well as data, it's often necessary to have public properties.</span></span> <span data-ttu-id="19ed1-115">Pro malé třídy nebo struktury, které pouze zapouzdřují sadu hodnot (data) a mají malé nebo žádné chování, byste však měli objekty nastavit jako neměnné deklarováním přístupového objektu set jako [soukromého](../../language-reference/keywords/private.md) (neproměnlivé pro příjemce) nebo deklarováním pouze přístupového objektu Get (neproměnlivé všude kromě konstruktoru).</span><span class="sxs-lookup"><span data-stu-id="19ed1-115">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="19ed1-116">Další informace naleznete v tématu [jak implementovat odlehčenou třídu s automaticky implementovanými vlastnostmi](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="19ed1-116">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19ed1-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="19ed1-117">See also</span></span>

- [<span data-ttu-id="19ed1-118">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="19ed1-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="19ed1-119">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="19ed1-119">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
