---
title: Postup implementace a volání vlastní metody rozšíření – Průvodce programováním v C#
description: Naučte se implementovat metody rozšíření pro libovolný typ .NET. Kód klienta může používat vaše metody přidáním odkazu na knihovnu DLL a přidáním direktivy using.
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7856e78713648a42d1c961f50f7e83f2f7ef05b7
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865057"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="f15f4-104">Postup implementace a volání vlastní metody rozšíření (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f15f4-104">How to implement and call a custom extension method (C# Programming Guide)</span></span>
<span data-ttu-id="f15f4-105">Toto téma ukazuje, jak implementovat vlastní metody rozšíření pro libovolný typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="f15f4-105">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="f15f4-106">Kód klienta může použít vaše metody rozšíření přidáním odkazu na knihovnu DLL, který obsahuje, a přidáním direktivy [using](../../language-reference/keywords/using-directive.md) , která určuje obor názvů, ve kterém jsou definovány metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f15f4-106">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="f15f4-107">Definování a volání metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="f15f4-107">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="f15f4-108">Definujte statickou [třídu](./static-classes-and-static-class-members.md) , která bude obsahovat metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f15f4-108">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="f15f4-109">Třída musí být viditelná pro klientský kód.</span><span class="sxs-lookup"><span data-stu-id="f15f4-109">The class must be visible to client code.</span></span> <span data-ttu-id="f15f4-110">Další informace o pravidlech přístupnosti najdete v tématu [modifikátory přístupu](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f15f4-110">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="f15f4-111">Implementujte metodu rozšíření jako statickou metodu s alespoň stejnou viditelností jako obsahující třídu.</span><span class="sxs-lookup"><span data-stu-id="f15f4-111">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="f15f4-112">První parametr metody určuje typ, na kterém metoda funguje; před ním musí být uveden [Tento](../../language-reference/keywords/this.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="f15f4-112">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="f15f4-113">V kódu volání přidejte `using` direktivu pro určení [oboru názvů](../../language-reference/keywords/namespace.md) , který obsahuje třídu metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="f15f4-113">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="f15f4-114">Zavolejte metody, jako by šlo o metody instance pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="f15f4-114">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="f15f4-115">Všimněte si, že první parametr není specifikován voláním kódu, protože představuje typ, na kterém je operátor použit, a kompilátor již zná typ objektu.</span><span class="sxs-lookup"><span data-stu-id="f15f4-115">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="f15f4-116">Stačí zadat argumenty pro parametry 2 až `n` .</span><span class="sxs-lookup"><span data-stu-id="f15f4-116">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f15f4-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="f15f4-117">Example</span></span>  
 <span data-ttu-id="f15f4-118">Následující příklad implementuje metodu rozšíření s názvem `WordCount` ve `CustomExtensions.StringExtension` třídě.</span><span class="sxs-lookup"><span data-stu-id="f15f4-118">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="f15f4-119">Metoda pracuje na <xref:System.String> třídě, která je zadána jako první parametr metody.</span><span class="sxs-lookup"><span data-stu-id="f15f4-119">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="f15f4-120">`CustomExtensions`Obor názvů je importován do oboru názvů aplikace a metoda je volána uvnitř `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="f15f4-120">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-security"></a><span data-ttu-id="f15f4-121">Zabezpečení .NET</span><span class="sxs-lookup"><span data-stu-id="f15f4-121">.NET Security</span></span>  
 <span data-ttu-id="f15f4-122">Metody rozšíření nepředstavují žádné konkrétní chyby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f15f4-122">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="f15f4-123">Nemohou být nikdy použity k zosobnění existujících metod pro typ, protože všechny kolize názvů jsou vyřešeny ve prospěch instance nebo statické metody definované samotným typem.</span><span class="sxs-lookup"><span data-stu-id="f15f4-123">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="f15f4-124">Metody rozšíření nemají přístup k žádným soukromým datům v rozšířené třídě.</span><span class="sxs-lookup"><span data-stu-id="f15f4-124">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15f4-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="f15f4-125">See also</span></span>

- [<span data-ttu-id="f15f4-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f15f4-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f15f4-127">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="f15f4-127">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="f15f4-128">LINQ (jazykově integrovaný dotaz)</span><span class="sxs-lookup"><span data-stu-id="f15f4-128">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="f15f4-129">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="f15f4-129">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="f15f4-130">protected</span><span class="sxs-lookup"><span data-stu-id="f15f4-130">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="f15f4-131">internal</span><span class="sxs-lookup"><span data-stu-id="f15f4-131">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="f15f4-132">public</span><span class="sxs-lookup"><span data-stu-id="f15f4-132">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="f15f4-133">Tento</span><span class="sxs-lookup"><span data-stu-id="f15f4-133">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="f15f4-134">hosting</span><span class="sxs-lookup"><span data-stu-id="f15f4-134">namespace</span></span>](../../language-reference/keywords/namespace.md)
