---
title: 'Postupy: Potlačení metody ToString - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: fd73deb4682ec12b982740f6e9e9c1e38a5688a3
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57202428"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="0fd10-102">Postupy: Potlačení metody ToString (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="0fd10-102">How to: Override the ToString Method (C# Programming Guide)</span></span>
<span data-ttu-id="0fd10-103">Implicitně dědí všechny třídy nebo struktury v jazyce C# <xref:System.Object> třídy.</span><span class="sxs-lookup"><span data-stu-id="0fd10-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="0fd10-104">Proto, získá každý objekt v jazyce C# <xref:System.Object.ToString%2A> metodu, která vrátí řetězcovou reprezentaci tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="0fd10-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="0fd10-105">Například všechny proměnné typu `int` mít `ToString` metodu, která umožňuje k návratu jejich obsah jako řetězec:</span><span class="sxs-lookup"><span data-stu-id="0fd10-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="0fd10-106">Když vytvoříte vlastní třídy nebo struktury, kterou byste měli přepsat <xref:System.Object.ToString%2A> metodu za účelem poskytnutí informací o typu pro klientský kód.</span><span class="sxs-lookup"><span data-stu-id="0fd10-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="0fd10-107">Informace o tom, jak používat formátovacích řetězců a dalších typů vlastní formátování pomocí `ToString` metodu, najdete v článku [Formatting Types](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="0fd10-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0fd10-108">Při rozhodování, jaké informace, které poskytují prostřednictvím této metody, zvažte, zda třídy nebo struktury se někdy použije nedůvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="0fd10-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="0fd10-109">Pečlivě zkontrolujte neposkytují žádné informace, které by se dala zneužít škodlivým kódem.</span><span class="sxs-lookup"><span data-stu-id="0fd10-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a><span data-ttu-id="0fd10-110">Přepsání metody ToString ve třídě nebo struktuře</span><span class="sxs-lookup"><span data-stu-id="0fd10-110">To override the ToString method in your class or struct</span></span>  
  
1.  <span data-ttu-id="0fd10-111">Deklarace `ToString` pomocí následujících parametrů a návratový typ metody:</span><span class="sxs-lookup"><span data-stu-id="0fd10-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  <span data-ttu-id="0fd10-112">Implementujte metodu tak, aby vrátil řetězec.</span><span class="sxs-lookup"><span data-stu-id="0fd10-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="0fd10-113">Následující příklad vrátí název třídy, kromě dat podle konkrétní instance třídy.</span><span class="sxs-lookup"><span data-stu-id="0fd10-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="0fd10-114">Můžete testovat `ToString` způsob, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="0fd10-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="0fd10-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0fd10-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="0fd10-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0fd10-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0fd10-117">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="0fd10-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="0fd10-118">Řetězce</span><span class="sxs-lookup"><span data-stu-id="0fd10-118">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
- [<span data-ttu-id="0fd10-119">string</span><span class="sxs-lookup"><span data-stu-id="0fd10-119">string</span></span>](../../../csharp/language-reference/keywords/string.md)
- [<span data-ttu-id="0fd10-120">new</span><span class="sxs-lookup"><span data-stu-id="0fd10-120">new</span></span>](../../../csharp/language-reference/keywords/new.md)
- [<span data-ttu-id="0fd10-121">override</span><span class="sxs-lookup"><span data-stu-id="0fd10-121">override</span></span>](../../../csharp/language-reference/keywords/override.md)
- [<span data-ttu-id="0fd10-122">virtual</span><span class="sxs-lookup"><span data-stu-id="0fd10-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)
- [<span data-ttu-id="0fd10-123">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="0fd10-123">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
