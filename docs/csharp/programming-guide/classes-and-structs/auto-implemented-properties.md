---
title: Automaticky implementované vlastnosti – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
ms.openlocfilehash: 76f16a66fbc01a6a69d91136cfbfe5805b91aea3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705636"
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="89d1b-102">Automaticky implementované vlastnosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="89d1b-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="89d1b-103">V C# 3,0 a novějších se automaticky implementované vlastnosti přizpůsobují deklarace vlastnost, pokud se v přístupových parametrech vlastnosti nepožaduje žádná další logika.</span><span class="sxs-lookup"><span data-stu-id="89d1b-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="89d1b-104">Také umožňují, aby kód klienta vytvářel objekty.</span><span class="sxs-lookup"><span data-stu-id="89d1b-104">They also enable client code to create objects.</span></span> <span data-ttu-id="89d1b-105">Pokud deklarujete vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří soukromé, anonymní zálohovací pole, které je přístupné pouze prostřednictvím `get` vlastností a přístupových objektů `set`.</span><span class="sxs-lookup"><span data-stu-id="89d1b-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89d1b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="89d1b-106">Example</span></span>  
 <span data-ttu-id="89d1b-107">Následující příklad ukazuje jednoduchou třídu, která má některé automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="89d1b-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#28)]  
  
 <span data-ttu-id="89d1b-108">V C# 6 a novějších verzích můžete inicializovat automaticky implementované vlastnosti podobně jako pole:</span><span class="sxs-lookup"><span data-stu-id="89d1b-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="89d1b-109">Třída, která je zobrazena v předchozím příkladu, je proměnlivá.</span><span class="sxs-lookup"><span data-stu-id="89d1b-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="89d1b-110">Kód klienta může změnit hodnoty v objektech poté, co byly vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="89d1b-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="89d1b-111">V komplexních třídách, které obsahují významné chování (metody) a také data, je často nutné mít veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="89d1b-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="89d1b-112">Pro malé třídy nebo struktury, které pouze zapouzdřují sadu hodnot (data) a mají malé nebo žádné chování, byste však měli objekty nastavit jako neměnné deklarováním přístupového objektu set jako [soukromého](../../language-reference/keywords/private.md) (neproměnlivé pro příjemce) nebo deklarováním pouze přístupového objektu Get (neproměnlivé všude kromě konstruktoru).</span><span class="sxs-lookup"><span data-stu-id="89d1b-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="89d1b-113">Další informace naleznete v tématu [jak implementovat odlehčenou třídu s automaticky implementovanými vlastnostmi](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="89d1b-113">For more information, see [How to implement a lightweight class with auto-implemented properties](./how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89d1b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89d1b-114">See also</span></span>

- [<span data-ttu-id="89d1b-115">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="89d1b-115">Properties</span></span>](./properties.md)
- [<span data-ttu-id="89d1b-116">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="89d1b-116">Modifiers</span></span>](/dotnet/csharp/language-reference/keywords)
