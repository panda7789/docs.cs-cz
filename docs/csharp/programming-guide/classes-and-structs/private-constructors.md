---
title: Soukromé konstruktory - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 0bd15b29f5e86b802eb48d96fde5be4b387261eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703345"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="f9508-102">Soukromé konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f9508-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="f9508-103">Soukromý konstruktor je speciální instanci konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f9508-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="f9508-104">Obecně se používá ve třídách, které obsahují pouze statické členy.</span><span class="sxs-lookup"><span data-stu-id="f9508-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="f9508-105">Pokud třída obsahuje jeden nebo více privátních konstruktorů a žádné veřejné konstruktory, jiné třídy (s výjimkou vnořené třídy) nelze vytvořit instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="f9508-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="f9508-106">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f9508-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="f9508-107">Deklaraci prázdného konstruktoru brání automatické generování konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="f9508-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="f9508-108">Všimněte si, že pokud použijete modifikátor přístupu pomocí konstruktoru dál ho budete mít ve výchozím nastavení privátní.</span><span class="sxs-lookup"><span data-stu-id="f9508-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="f9508-109">Ale [privátní](../../../csharp/language-reference/keywords/private.md) modifikátor se obvykle používá k němu explicitně vymazat, že nelze vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="f9508-109">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="f9508-110">Soukromé konstruktory se používají k zabránění vytváření instancí třídy, pokud neexistují žádné pole instance nebo metod, jako <xref:System.Math> třídy, nebo když je metoda volána k získání instance třídy.</span><span class="sxs-lookup"><span data-stu-id="f9508-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="f9508-111">Pokud jsou všechny metody ve třídě statické, zvažte úplnou třídu statické.</span><span class="sxs-lookup"><span data-stu-id="f9508-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="f9508-112">Další informace najdete v části [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="f9508-112">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9508-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9508-113">Example</span></span>  
 <span data-ttu-id="f9508-114">Následuje příklad používání soukromý konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="f9508-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="f9508-115">Všimněte si, že pokud zrušte komentář u následujícího příkazu z příkladu, vygeneruje chybu protože konstruktoru je nepřístupný z důvodu úrovně ochrany:</span><span class="sxs-lookup"><span data-stu-id="f9508-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f9508-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f9508-116">C# Language Specification</span></span>  

<span data-ttu-id="f9508-117">Další informace najdete v tématu [soukromé konstruktory](~/_csharplang/spec/classes.md#private-constructors) v [ C# specifikace jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f9508-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="f9508-118">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="f9508-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f9508-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9508-119">See also</span></span>

- [<span data-ttu-id="f9508-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f9508-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f9508-121">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="f9508-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="f9508-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="f9508-122">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="f9508-123">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="f9508-123">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="f9508-124">private</span><span class="sxs-lookup"><span data-stu-id="f9508-124">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="f9508-125">public</span><span class="sxs-lookup"><span data-stu-id="f9508-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)
