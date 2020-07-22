---
title: Jak přepsat metodu ToString – Průvodce programováním v C#
description: Přečtěte si, jak v jazyce C# přepsat metodu ToString. Každá třída nebo struktura dědí objekt a získá metodu ToString, která vrací řetězcovou reprezentaci tohoto objektu.
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 65b34b485d4b90173a4c956dd0ebaaa590a0c7c9
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865005"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a><span data-ttu-id="5cdc4-104">Jak přepsat metodu ToString (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5cdc4-104">How to override the ToString method (C# Programming Guide)</span></span>

<span data-ttu-id="5cdc4-105">Každá třída nebo struktura v jazyce C# implicitně dědí <xref:System.Object> třídu.</span><span class="sxs-lookup"><span data-stu-id="5cdc4-105">Every class or struct in C# implicitly inherits the <xref:System.Object> class.</span></span> <span data-ttu-id="5cdc4-106">Proto každý objekt v jazyce C# získá <xref:System.Object.ToString%2A> metodu, která vrátí řetězcovou reprezentaci tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="5cdc4-106">Therefore, every object in C# gets the <xref:System.Object.ToString%2A> method, which returns a string representation of that object.</span></span> <span data-ttu-id="5cdc4-107">Například všechny proměnné typu `int` mají `ToString` metodu, která umožňuje, aby vrátila svůj obsah jako řetězec:</span><span class="sxs-lookup"><span data-stu-id="5cdc4-107">For example, all variables of type `int` have a `ToString` method, which enables them to return their contents as a string:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 <span data-ttu-id="5cdc4-108">Při vytváření vlastní třídy nebo struktury byste měli přepsat <xref:System.Object.ToString%2A> metodu, aby poskytovala informace o typu pro klientský kód.</span><span class="sxs-lookup"><span data-stu-id="5cdc4-108">When you create a custom class or struct, you should override the <xref:System.Object.ToString%2A> method in order to provide information about your type to client code.</span></span>  
  
 <span data-ttu-id="5cdc4-109">Informace o tom, jak používat řetězce formátu a jiné typy vlastního formátování s `ToString` metodou, naleznete v tématu [Formatting Types](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="5cdc4-109">For information about how to use format strings and other types of custom formatting with the `ToString` method, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5cdc4-110">Pokud se rozhodnete, jaké informace chcete poskytnout prostřednictvím této metody, zvažte, zda bude vaše třída nebo struktura někdy používána nedůvěryhodným kódem.</span><span class="sxs-lookup"><span data-stu-id="5cdc4-110">When you decide what information to provide through this method, consider whether your class or struct will ever be used by untrusted code.</span></span> <span data-ttu-id="5cdc4-111">Buďte opatrní, abyste se ujistili, že neposkytnete žádné informace, které by mohly být zneužity škodlivým kódem.</span><span class="sxs-lookup"><span data-stu-id="5cdc4-111">Be careful to ensure that you do not provide any information that could be exploited by malicious code.</span></span>  
  
<span data-ttu-id="5cdc4-112">Přepsání `ToString` metody ve vaší třídě nebo struktuře:</span><span class="sxs-lookup"><span data-stu-id="5cdc4-112">To override the `ToString` method in your class or struct:</span></span>
  
1. <span data-ttu-id="5cdc4-113">Deklarujte `ToString` metodu s následujícími modifikátory a návratovým typem:</span><span class="sxs-lookup"><span data-stu-id="5cdc4-113">Declare a `ToString` method with the following modifiers and return type:</span></span>  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. <span data-ttu-id="5cdc4-114">Implementujte metodu tak, aby vracela řetězec.</span><span class="sxs-lookup"><span data-stu-id="5cdc4-114">Implement the method so that it returns a string.</span></span>  
  
     <span data-ttu-id="5cdc4-115">Následující příklad vrátí název třídy kromě dat specifických pro konkrétní instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="5cdc4-115">The following example returns the name of the class in addition to the data specific to a particular instance of the class.</span></span>  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     <span data-ttu-id="5cdc4-116">Můžete testovat `ToString` metodu, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="5cdc4-116">You can test the `ToString` method as shown in the following code example:</span></span>  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="5cdc4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="5cdc4-117">See also</span></span>

- <xref:System.IFormattable>
- [<span data-ttu-id="5cdc4-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5cdc4-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5cdc4-119">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="5cdc4-119">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="5cdc4-120">Řetězce</span><span class="sxs-lookup"><span data-stu-id="5cdc4-120">Strings</span></span>](../strings/index.md)
- [<span data-ttu-id="5cdc4-121">řetezce</span><span class="sxs-lookup"><span data-stu-id="5cdc4-121">string</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="5cdc4-122">override</span><span class="sxs-lookup"><span data-stu-id="5cdc4-122">override</span></span>](../../language-reference/keywords/override.md)
- [<span data-ttu-id="5cdc4-123">VM</span><span class="sxs-lookup"><span data-stu-id="5cdc4-123">virtual</span></span>](../../language-reference/keywords/virtual.md)
- [<span data-ttu-id="5cdc4-124">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="5cdc4-124">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
