---
title: Soukromé konstruktory – Průvodce programováním v C#
description: Privátní konstruktor je speciální konstruktor instance v jazyce C#, který slouží k omezení toho, jak lze objekt vytvořit. Můžou se používat s výrobními metodami nebo jinými idiomy konstrukcemi.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: a6b86ccb870da0262bcbc516e176e00d17724f9f
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864056"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="55b44-104">Soukromé konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="55b44-104">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="55b44-105">Privátní konstruktor je speciální konstruktor instance.</span><span class="sxs-lookup"><span data-stu-id="55b44-105">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="55b44-106">Obvykle se používá ve třídách, které obsahují pouze statické členy.</span><span class="sxs-lookup"><span data-stu-id="55b44-106">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="55b44-107">Pokud třída má jeden nebo více privátních konstruktorů a žádné veřejné konstruktory, jiné třídy (s výjimkou vnořených tříd) nemohou vytvářet instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="55b44-107">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="55b44-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="55b44-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="55b44-109">Deklarace prázdného konstruktoru brání automatické generaci konstruktoru bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="55b44-109">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="55b44-110">Všimněte si, že pokud nepoužíváte modifikátor přístupu s konstruktorem, bude ve výchozím nastavení nadále privátní.</span><span class="sxs-lookup"><span data-stu-id="55b44-110">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="55b44-111">Nicméně [soukromý](../../language-reference/keywords/private.md) modifikátor se obvykle používá explicitně k tomu, aby bylo jasné, že třídu nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="55b44-111">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="55b44-112">Soukromé konstruktory se používají k zabránění vytváření instancí třídy, pokud nejsou k dispozici žádná pole nebo metody instance, jako je <xref:System.Math> třída nebo když je volána metoda pro získání instance třídy.</span><span class="sxs-lookup"><span data-stu-id="55b44-112">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="55b44-113">Pokud jsou všechny metody ve třídě statické, zvažte vytvoření celé třídy static.</span><span class="sxs-lookup"><span data-stu-id="55b44-113">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="55b44-114">Další informace naleznete v tématu [statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="55b44-114">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="55b44-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="55b44-115">Example</span></span>  
 <span data-ttu-id="55b44-116">Následující příklad třídy používá privátní konstruktor.</span><span class="sxs-lookup"><span data-stu-id="55b44-116">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="55b44-117">Všimněte si, že pokud zrušíte komentář k následujícímu příkazu z příkladu, vygeneruje se chyba, protože konstruktor je nepřístupný z důvodu úrovně ochrany:</span><span class="sxs-lookup"><span data-stu-id="55b44-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="55b44-118">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="55b44-118">C# Language Specification</span></span>  

<span data-ttu-id="55b44-119">Další informace naleznete v tématu [Soukromé konstruktory](~/_csharplang/spec/classes.md#private-constructors) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="55b44-119">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="55b44-120">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="55b44-120">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="55b44-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="55b44-121">See also</span></span>

- [<span data-ttu-id="55b44-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="55b44-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="55b44-123">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="55b44-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="55b44-124">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="55b44-124">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="55b44-125">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="55b44-125">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="55b44-126">hlášen</span><span class="sxs-lookup"><span data-stu-id="55b44-126">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="55b44-127">public</span><span class="sxs-lookup"><span data-stu-id="55b44-127">public</span></span>](../../language-reference/keywords/public.md)
