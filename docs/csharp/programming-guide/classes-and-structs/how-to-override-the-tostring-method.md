---
title: "Postupy: Potlačení metody ToString (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b0f7bf35e5bd565e0bfa46fe91cf86aedcd2d8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="3dd47-102">Postupy: Potlačení metody ToString (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="3dd47-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="3dd47-103">Každé třídě nebo struktuře v jazyce C# implicitně dědí <xref:System.Object> třídy.</span><span class="sxs-lookup"><span data-stu-id="3dd47-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="3dd47-104">Proto získá každý objekt v jazyce C# <xref:System.Object.ToString%2A> metoda, která vrátí řetězcovou reprezentaci tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="3dd47-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="3dd47-105">Například všechny proměnné typu `int` mít `ToString` metoda, která umožňuje, aby vrátila jejich obsah jako řetězec:</span><span class="sxs-lookup"><span data-stu-id="3dd47-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_1.cs)]  
  
 <span data-ttu-id="3dd47-106">Když vytvoříte vlastní třídě nebo struktuře, by měly přepsat <xref:System.Object.ToString%2A> za účelem zadání informací o typu vašeho kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="3dd47-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="3dd47-107">Informace o tom, jak používat formát řetězci a ostatními typy vlastní formátování s `ToString` metodu, najdete v části [typy formátování](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="3dd47-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3dd47-108">Pokud se rozhodnete, jaké informace, které poskytují prostřednictvím této metody, zvažte, jestli třídě nebo struktuře někdy použije nedůvěryhodnému kódu.</span><span class="sxs-lookup"><span data-stu-id="3dd47-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="3dd47-109">Dávejte pozor, aby neposkytují veškeré informace, které může zneužít škodlivý kód.</span><span class="sxs-lookup"><span data-stu-id="3dd47-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="3dd47-110">K potlačení metody ToString ve třídě nebo struktuře</span><span class="sxs-lookup"><span data-stu-id="3dd47-110">To override the ToString method in your class or struct</span></span>  
  
1.  <span data-ttu-id="3dd47-111">Deklarace `ToString` metoda s následující parametry a návratový typ:</span><span class="sxs-lookup"><span data-stu-id="3dd47-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  <span data-ttu-id="3dd47-112">Implementujte metodu tak, že vrátí řetězec.</span><span class="sxs-lookup"><span data-stu-id="3dd47-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="3dd47-113">Následující příklad vrátí název třídy kromě dat podle konkrétní instance třídy.</span><span class="sxs-lookup"><span data-stu-id="3dd47-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     <span data-ttu-id="3dd47-114">Můžete otestovat `ToString` metoda, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="3dd47-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3dd47-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dd47-115">See Also</span></span>  
 <xref:System.IFormattable>  
 [<span data-ttu-id="3dd47-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="3dd47-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3dd47-117">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="3dd47-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="3dd47-118">Řetězce</span><span class="sxs-lookup"><span data-stu-id="3dd47-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="3dd47-119">řetězec</span><span class="sxs-lookup"><span data-stu-id="3dd47-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)  
 [<span data-ttu-id="3dd47-120">Nový</span><span class="sxs-lookup"><span data-stu-id="3dd47-120">new</span></span>](../../../csharp/language-reference/keywords/new.md)  
 [<span data-ttu-id="3dd47-121">přepsání</span><span class="sxs-lookup"><span data-stu-id="3dd47-121">override</span></span>](../../../csharp/language-reference/keywords/override.md)  
 [<span data-ttu-id="3dd47-122">virtuální</span><span class="sxs-lookup"><span data-stu-id="3dd47-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)  
 [<span data-ttu-id="3dd47-123">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="3dd47-123">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
