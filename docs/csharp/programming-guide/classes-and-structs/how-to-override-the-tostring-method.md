---
title: Jak přepsat metodu ToString - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 7c7196df56821c134b31982d7956a75039e9f929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705571"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="b9c21-102">Jak přepsat metodu ToString (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b9c21-102">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="b9c21-103">Každá třída nebo struktura v jazyce <xref:System.Object> C# implicitně dědí třídu.</span><span class="sxs-lookup"><span data-stu-id="b9c21-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="b9c21-104">Proto každý objekt v C# získá metodu, <xref:System.Object.ToString%2A> která vrátí řetězcovou reprezentaci tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="b9c21-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="b9c21-105">Například všechny proměnné typu `int` mají `ToString` metodu, která jim umožňuje vrátit jejich obsah jako řetězec:</span><span class="sxs-lookup"><span data-stu-id="b9c21-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="b9c21-106">Při vytváření vlastní třídy nebo struktury, měli <xref:System.Object.ToString%2A> byste přepsat metodu za účelem poskytnutí informací o typu klientského kódu.</span><span class="sxs-lookup"><span data-stu-id="b9c21-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="b9c21-107">Informace o použití formátovacích řetězců a dalších typů `ToString` vlastního formátování s metodou naleznete v [tématu Typy formátování](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="b9c21-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b9c21-108">Při rozhodování o tom, jaké informace poskytnout prostřednictvím této metody, zvažte, zda vaše třída nebo struktura bude někdy použit nedůvěryhodný kód.</span><span class="sxs-lookup"><span data-stu-id="b9c21-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="b9c21-109">Dbejte na to, abyste neposkytovali žádné informace, které by mohly být zneužity škodlivým kódem.</span><span class="sxs-lookup"><span data-stu-id="b9c21-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="b9c21-110">Chcete-li `ToString` přepsat metodu ve třídě nebo struktuře:</span><span class="sxs-lookup"><span data-stu-id="b9c21-110">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="b9c21-111">Deklarujte metodu `ToString` s následujícími modifikátory a návratovým typem:</span><span class="sxs-lookup"><span data-stu-id="b9c21-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="b9c21-112">Implementujte metodu tak, aby vrátí řetězec.</span><span class="sxs-lookup"><span data-stu-id="b9c21-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="b9c21-113">Následující příklad vrátí název třídy kromě dat specifických pro konkrétní instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="b9c21-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="b9c21-114">Metodu můžete `ToString` otestovat, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="b9c21-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="b9c21-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9c21-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="b9c21-116">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b9c21-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b9c21-117">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="b9c21-117">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b9c21-118">Řetězce</span><span class="sxs-lookup"><span data-stu-id="b9c21-118">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="b9c21-119">Řetězec</span><span class="sxs-lookup"><span data-stu-id="b9c21-119">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="b9c21-120">override</span><span class="sxs-lookup"><span data-stu-id="b9c21-120">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="b9c21-121">virtual</span><span class="sxs-lookup"><span data-stu-id="b9c21-121">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="b9c21-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="b9c21-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
