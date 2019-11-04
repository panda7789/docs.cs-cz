---
title: 'Postupy: potlačení metody ToString – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 9dd567e537768ceb8b9f61ce58dccd443db38ec7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419345"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="d085d-102">Postupy: Potlačení metody ToString (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d085d-102">How to: Override the ToString Method (C# Programming Guide)</span></span>

<span data-ttu-id="d085d-103">Každá třída nebo struktura v C# implicitně dědí třídu <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="d085d-103">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="d085d-104">Proto každý objekt v C# získá metodu <xref:System.Object.ToString%2A>, která vrátí řetězcovou reprezentaci tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="d085d-104">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="d085d-105">Například všechny proměnné typu `int` mají metodu `ToString`, která umožňuje, aby vrátila svůj obsah jako řetězec:</span><span class="sxs-lookup"><span data-stu-id="d085d-105">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="d085d-106">Při vytváření vlastní třídy nebo struktury byste měli přepsat metodu <xref:System.Object.ToString%2A>, aby poskytovala informace o typu pro klientský kód.</span><span class="sxs-lookup"><span data-stu-id="d085d-106">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="d085d-107">Informace o tom, jak používat formátovací řetězce a jiné typy vlastního formátování s metodou `ToString`, naleznete v tématu [typy formátování](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="d085d-107">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d085d-108">Pokud se rozhodnete, jaké informace chcete poskytnout prostřednictvím této metody, zvažte, zda bude vaše třída nebo struktura někdy používána nedůvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="d085d-108">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="d085d-109">Buďte opatrní, abyste se ujistili, že neposkytnete žádné informace, které by mohly být zneužity škodlivým kódem.</span><span class="sxs-lookup"><span data-stu-id="d085d-109">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="d085d-110">Chcete-li přepsat metodu `ToString` ve vaší třídě nebo struktuře:</span><span class="sxs-lookup"><span data-stu-id="d085d-110">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="d085d-111">Deklarujte metodu `ToString` s následujícími modifikátory a návratovým typem:</span><span class="sxs-lookup"><span data-stu-id="d085d-111">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="d085d-112">Implementujte metodu tak, aby vracela řetězec.</span><span class="sxs-lookup"><span data-stu-id="d085d-112">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="d085d-113">Následující příklad vrátí název třídy kromě dat specifických pro konkrétní instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="d085d-113">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="d085d-114">Můžete testovat metodu `ToString`, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="d085d-114">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="d085d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d085d-115">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="d085d-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d085d-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d085d-117">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="d085d-117">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="d085d-118">Řetězce</span><span class="sxs-lookup"><span data-stu-id="d085d-118">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="d085d-119">string</span><span class="sxs-lookup"><span data-stu-id="d085d-119">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="d085d-120">override</span><span class="sxs-lookup"><span data-stu-id="d085d-120">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="d085d-121">virtual</span><span class="sxs-lookup"><span data-stu-id="d085d-121">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="d085d-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="d085d-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
