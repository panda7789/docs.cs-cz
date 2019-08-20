---
title: Automaticky implementované vlastnosti – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 44f3beb9de8c9d339c42db26bb9c510998abc7d7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597132"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="b3e46-102">Automaticky implementované vlastnosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b3e46-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="b3e46-103">V C# 3,0 a novějších se automaticky implementované vlastnosti přizpůsobují deklarace vlastnost, pokud se v přístupových parametrech vlastnosti nepožaduje žádná další logika.</span><span class="sxs-lookup"><span data-stu-id="b3e46-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="b3e46-104">Také umožňují, aby kód klienta vytvářel objekty.</span><span class="sxs-lookup"><span data-stu-id="b3e46-104">They also enable client code to create objects.</span></span> <span data-ttu-id="b3e46-105">Pokud deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří soukromé, anonymní zálohovací pole, které je přístupné pouze prostřednictvím vlastností `get` a `set` přístupových objektů.</span><span class="sxs-lookup"><span data-stu-id="b3e46-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3e46-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3e46-106">Example</span></span>  
 <span data-ttu-id="b3e46-107">Následující příklad ukazuje jednoduchou třídu, která má některé automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b3e46-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 <span data-ttu-id="b3e46-108">V C# 6 a novějších verzích můžete inicializovat automaticky implementované vlastnosti podobně jako pole:</span><span class="sxs-lookup"><span data-stu-id="b3e46-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="b3e46-109">Třída, která je zobrazena v předchozím příkladu, je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="b3e46-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="b3e46-110">Kód klienta může změnit hodnoty v objektech poté, co byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="b3e46-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="b3e46-111">V komplexních třídách, které obsahují významné chování (metody) a také data, je často nutné mít veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b3e46-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="b3e46-112">Pro malé třídy nebo struktury, které pouze zapouzdřují sadu hodnot (data) a mají malé nebo žádné chování, byste však měli objekty nastavit jako neměnné deklarováním přístupového objektu set jako privátního [](../../language-reference/keywords/private.md) (neměnného pro uživatele) nebo deklarací pouze get přistupující objekt (neproměnlivý všude kromě konstruktoru).</span><span class="sxs-lookup"><span data-stu-id="b3e46-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="b3e46-113">Další informace najdete v tématu [jak: Implementujte odlehčenou třídu s automaticky implementovanými](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md)vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="b3e46-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e46-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3e46-114">See also</span></span>

- [<span data-ttu-id="b3e46-115">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b3e46-115">Properties</span></span>](./properties.md)
- [<span data-ttu-id="b3e46-116">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="b3e46-116">Modifiers</span></span>](../../language-reference/keywords/modifiers.md)
