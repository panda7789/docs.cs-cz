---
title: "Automaticky implementované vlastnosti (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: aa55fa97-ccec-431f-b5e9-5ac789fd32b7
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1aa923c6d8208c2d5451957c4112493d0acd561d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="d7d5e-102">Automaticky implementované vlastnosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d7d5e-102">Auto-Implemented Properties (C# Programming Guide)</span></span>
<span data-ttu-id="d7d5e-103">V jazyce C# 3.0 nebo novější automaticky implementované vlastnosti deklarace vlastnosti přesnější při provést žádné další logiku navíc je nutné v přístupových objektech vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-103">In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.</span></span> <span data-ttu-id="d7d5e-104">Umožňují také kód klienta k vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-104">They also enable client code to create objects.</span></span> <span data-ttu-id="d7d5e-105">Když je deklarovat vlastnost, jak je znázorněno v následujícím příkladu, kompilátor vytvoří privátní, anonymní základní pole, které je přístupné pouze prostřednictvím vlastnosti `get` a `set` přistupující objekty.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-105">When you declare a property as shown in the following example, the compiler creates a private, anonymous backing field that can only be accessed through the property's `get` and `set` accessors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7d5e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7d5e-106">Example</span></span>  
 <span data-ttu-id="d7d5e-107">Následující příklad ukazuje jednoduchý třídy, která má některé automaticky implementované vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d7d5e-107">The following example shows a simple class that has some auto-implemented properties:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#28](../../../csharp/programming-guide/arrays/codesnippet/CSharp/auto-implemented-properties_1.cs)]  
  
 <span data-ttu-id="d7d5e-108">V jazyce C# 6 nebo novější bude možné inicializovat automaticky implementované vlastnosti podobně jako na pole:</span><span class="sxs-lookup"><span data-stu-id="d7d5e-108">In C# 6 and later, you can initialize auto-implemented properties similarly to fields:</span></span>  
  
```csharp  
public string FirstName { get; set; } = "Jane";  
```  
  
 <span data-ttu-id="d7d5e-109">Třída, která se zobrazí v předchozím příkladu je měnitelný.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-109">The class that is shown in the previous example is mutable.</span></span> <span data-ttu-id="d7d5e-110">Kód klienta můžete změnit hodnoty v objektech po jejich vytvoření.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-110">Client code can change the values in objects after they are created.</span></span> <span data-ttu-id="d7d5e-111">V komplexní tříd, které obsahují důležité chování (metody) a také data je často potřeba mít veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-111">In complex classes that contain significant behavior (methods) as well as data, it is often necessary to have public properties.</span></span> <span data-ttu-id="d7d5e-112">Ale pro malé třídy nebo struktury, které právě zapouzdření sadu hodnot (data) a nemají žádné nebo téměř žádné chování, buď měli objekty neměnné deklarováním přistupující objekt set jako [privátní](../../../csharp/language-reference/keywords/private.md) (neměnné k příjemce), nebo deklarování pouze přistupující (neměnné everywhere kromě konstruktoru).</span><span class="sxs-lookup"><span data-stu-id="d7d5e-112">However, for small classes or structs that just encapsulate a set of values (data) and have little or no behaviors, you should either make the objects immutable by declaring the set accessor as [private](../../../csharp/language-reference/keywords/private.md) (immutable to consumers) or by declaring only a get accessor (immutable everywhere except the constructor).</span></span>  <span data-ttu-id="d7d5e-113">Další informace najdete v tématu [postupy: implementace třídy Lightweight vlastnostmi Auto-Implemented](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d7d5e-113">For more information, see [How to: Implement a Lightweight Class with Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="d7d5e-114">Atributy jsou povoleny na automaticky implementované vlastnosti ale samozřejmě není na pole Základní od těch, které nejsou přístupné z vašeho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-114">Attributes are permitted on auto-implemented properties but obviously not on the backing fields since those are not accessible from your source code.</span></span> <span data-ttu-id="d7d5e-115">Pokud je třeba použít atribut na pole základní vlastnosti, stačí vytvořte regulární vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d7d5e-115">If you must use an attribute on the backing field of a property, just create a regular property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7d5e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7d5e-116">See Also</span></span>  
 [<span data-ttu-id="d7d5e-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d7d5e-117">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="d7d5e-118">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="d7d5e-118">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
