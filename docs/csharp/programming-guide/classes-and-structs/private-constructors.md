---
title: Soukromé konstruktory (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 1338a6efbe03522093899009178b6f31e558d8dd
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646993"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="8cb52-102">Soukromé konstruktory (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8cb52-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="8cb52-103">Soukromý konstruktor je speciální instanci konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8cb52-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="8cb52-104">Obecně se používá ve třídách, které obsahují pouze statické členy.</span><span class="sxs-lookup"><span data-stu-id="8cb52-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="8cb52-105">Pokud třída obsahuje jeden nebo více privátních konstruktorů a žádné veřejné konstruktory, jiné třídy (s výjimkou vnořené třídy) nelze vytvořit instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="8cb52-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="8cb52-106">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8cb52-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 <span data-ttu-id="8cb52-107">Deklaraci prázdného konstruktoru brání automatické generování výchozího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8cb52-107">The declaration of the empty constructor prevents the automatic generation of a default constructor.</span></span> <span data-ttu-id="8cb52-108">Všimněte si, že pokud použijete modifikátor přístupu pomocí konstruktoru dál ho budete mít ve výchozím nastavení privátní.</span><span class="sxs-lookup"><span data-stu-id="8cb52-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="8cb52-109">Ale [privátní](../../../csharp/language-reference/keywords/private.md) modifikátor se obvykle používá k němu explicitně vymazat, že nelze vytvořit instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="8cb52-109">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="8cb52-110">Soukromé konstruktory se používají k zabránění vytváření instancí třídy, pokud neexistují žádné pole instance nebo metod, jako <xref:System.Math> třídy, nebo když je metoda volána k získání instance třídy.</span><span class="sxs-lookup"><span data-stu-id="8cb52-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="8cb52-111">Pokud jsou všechny metody ve třídě statické, zvažte úplnou třídu statické.</span><span class="sxs-lookup"><span data-stu-id="8cb52-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="8cb52-112">Další informace najdete v části [statické třídy a statické členy třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="8cb52-112">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cb52-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="8cb52-113">Example</span></span>  
 <span data-ttu-id="8cb52-114">Následuje příklad používání soukromý konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="8cb52-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 <span data-ttu-id="8cb52-115">Všimněte si, že pokud zrušte komentář u následujícího příkazu z příkladu, vygeneruje chybu protože konstruktoru je nepřístupný z důvodu úrovně ochrany:</span><span class="sxs-lookup"><span data-stu-id="8cb52-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8cb52-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8cb52-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8cb52-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8cb52-117">See Also</span></span>

- [<span data-ttu-id="8cb52-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8cb52-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8cb52-119">Třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="8cb52-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="8cb52-120">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="8cb52-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="8cb52-121">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="8cb52-121">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [<span data-ttu-id="8cb52-122">private</span><span class="sxs-lookup"><span data-stu-id="8cb52-122">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="8cb52-123">public</span><span class="sxs-lookup"><span data-stu-id="8cb52-123">public</span></span>](../../../csharp/language-reference/keywords/public.md)
