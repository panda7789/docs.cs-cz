---
title: Soukromé konstruktory – programovací příručka Jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705441"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="5486a-102">Soukromé konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5486a-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="5486a-103">Soukromý konstruktor je konstruktor zvláštní instance.</span><span class="sxs-lookup"><span data-stu-id="5486a-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="5486a-104">Obecně se používá ve třídách, které obsahují pouze statické členy.</span><span class="sxs-lookup"><span data-stu-id="5486a-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="5486a-105">Pokud třída má jeden nebo více soukromých konstruktorů a žádné veřejné konstruktory, jiné třídy (s výjimkou vnořené třídy) nelze vytvořit instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="5486a-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="5486a-106">Například:</span><span class="sxs-lookup"><span data-stu-id="5486a-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="5486a-107">Deklarace prázdnékonstruktor zabraňuje automatické generování konstruktoru bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="5486a-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="5486a-108">Všimněte si, že pokud nepoužijete modifikátor přístupu s konstruktorem, bude ve výchozím nastavení stále soukromý.</span><span class="sxs-lookup"><span data-stu-id="5486a-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="5486a-109">[Privátní](../../language-reference/keywords/private.md) modifikátor se však obvykle používá explicitně, aby bylo jasné, že třídu nelze vytvořit instanci.</span><span class="sxs-lookup"><span data-stu-id="5486a-109">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="5486a-110">Soukromé konstruktory se používají k zabránění vytváření instancí třídy, pokud <xref:System.Math> neexistují žádná pole instance nebo metody, jako je například třída, nebo když je metoda volána k získání instance třídy.</span><span class="sxs-lookup"><span data-stu-id="5486a-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="5486a-111">Pokud jsou všechny metody ve třídě statické, zvažte vytvoření úplné třídy statické.</span><span class="sxs-lookup"><span data-stu-id="5486a-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="5486a-112">Další informace naleznete [v tématu Statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="5486a-112">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5486a-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="5486a-113">Example</span></span>  
 <span data-ttu-id="5486a-114">Následuje příklad třídy pomocí soukromého konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="5486a-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="5486a-115">Všimněte si, že pokud odkomentujete následující příkaz z příkladu, vygeneruje chybu, protože konstruktor je nepřístupný z důvodu úrovně ochrany:</span><span class="sxs-lookup"><span data-stu-id="5486a-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5486a-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5486a-116">C# Language Specification</span></span>  

<span data-ttu-id="5486a-117">Další informace naleznete [v tématu Private konstruktory](~/_csharplang/spec/classes.md#private-constructors) v [c# specifikace jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="5486a-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="5486a-118">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="5486a-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5486a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="5486a-119">See also</span></span>

- [<span data-ttu-id="5486a-120">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5486a-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5486a-121">Třídy a struky</span><span class="sxs-lookup"><span data-stu-id="5486a-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="5486a-122">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="5486a-122">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="5486a-123">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="5486a-123">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="5486a-124">Soukromé</span><span class="sxs-lookup"><span data-stu-id="5486a-124">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="5486a-125">Veřejné</span><span class="sxs-lookup"><span data-stu-id="5486a-125">public</span></span>](../../language-reference/keywords/public.md)
