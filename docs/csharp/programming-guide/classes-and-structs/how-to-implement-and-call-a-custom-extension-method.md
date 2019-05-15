---
title: 'Postupy: Implementace a volání vlastní metody rozšíření - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 2fe07f8e4311417980caccc9c286b4f94c7ea994
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585949"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="6573d-102">Postupy: Implementace a volání vlastní metody rozšíření (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="6573d-102">How to: Implement and Call a Custom Extension Method (C# Programming Guide)</span></span>
<span data-ttu-id="6573d-103">Toto téma ukazuje, jak implementovat vlastní metody rozšíření pro jakýkoli typ .NET.</span><span class="sxs-lookup"><span data-stu-id="6573d-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="6573d-104">Klientský kód můžete použít rozšiřující metody přidejte odkaz na knihovnu DLL, která je obsahuje, a přidáním [pomocí](../../../csharp/language-reference/keywords/using-directive.md) direktiva, která určuje obor názvů, ve kterém jsou definovány metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6573d-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../../csharp/language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="6573d-105">K definování a volání metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="6573d-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="6573d-106">Definovat statický [třídy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) obsahuje metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6573d-106">Define a static [class](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="6573d-107">Třída musí být viditelná pro klientský kód.</span><span class="sxs-lookup"><span data-stu-id="6573d-107">The class must be visible to client code.</span></span> <span data-ttu-id="6573d-108">Další informace o usnadnění pravidel, naleznete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="6573d-108">For more information about accessibility rules, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="6573d-109">Implementovat metodu rozšíření jako statickou metodu s alespoň stejnou viditelnost jako nadřazený třídy.</span><span class="sxs-lookup"><span data-stu-id="6573d-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="6573d-110">První parametr metody Určuje typ, který pracuje metodu; musíte začínající [to](../../../csharp/language-reference/keywords/this.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="6573d-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../../csharp/language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="6573d-111">Ve volajícím kódu, přidejte `using` – direktiva k určení [obor názvů](../../../csharp/language-reference/keywords/namespace.md) , který obsahuje třídu – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6573d-111">In the calling code, add a `using` directive to specify the [namespace](../../../csharp/language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="6573d-112">Volání metody, jako kdyby byly metodami instance typu.</span><span class="sxs-lookup"><span data-stu-id="6573d-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="6573d-113">Všimněte si, že první parametr není zadán voláním kódu, protože představuje typ, na které se právě používá operátor a kompilátor zná typu objektu.</span><span class="sxs-lookup"><span data-stu-id="6573d-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="6573d-114">Budete muset zadat argumenty pro parametry 2 prostřednictvím `n`.</span><span class="sxs-lookup"><span data-stu-id="6573d-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6573d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="6573d-115">Example</span></span>  
 <span data-ttu-id="6573d-116">Následující příklad implementuje metodu rozšíření s názvem `WordCount` v `CustomExtensions.StringExtension` třídy.</span><span class="sxs-lookup"><span data-stu-id="6573d-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="6573d-117">Metoda pracuje <xref:System.String> třídu, která je zadána jako první parametr metody.</span><span class="sxs-lookup"><span data-stu-id="6573d-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="6573d-118">`CustomExtensions` Obor názvů se importují do oboru názvů aplikací a metoda je volána v rámci `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="6573d-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="6573d-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6573d-119">.NET Framework Security</span></span>  
 <span data-ttu-id="6573d-120">Rozšiřující metody k dispozici žádná konkrétní zabezpečení ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6573d-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="6573d-121">Se nikdy slouží k zosobnění existující metody na typu, protože jsou vyřešeny všechny kolize názvů ve prospěch instance nebo statické metody definované v samotném typu.</span><span class="sxs-lookup"><span data-stu-id="6573d-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="6573d-122">Rozšiřující metody nelze přístup k žádným privátním datům ve třídě rozšířené.</span><span class="sxs-lookup"><span data-stu-id="6573d-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6573d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6573d-123">See also</span></span>

- [<span data-ttu-id="6573d-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6573d-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6573d-125">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="6573d-125">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="6573d-126">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="6573d-126">LINQ (Language-Integrated Query)</span></span>](../../../csharp/linq/linq-in-csharp.md)
- [<span data-ttu-id="6573d-127">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="6573d-127">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="6573d-128">protected</span><span class="sxs-lookup"><span data-stu-id="6573d-128">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
- [<span data-ttu-id="6573d-129">internal</span><span class="sxs-lookup"><span data-stu-id="6573d-129">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
- [<span data-ttu-id="6573d-130">public</span><span class="sxs-lookup"><span data-stu-id="6573d-130">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="6573d-131">this</span><span class="sxs-lookup"><span data-stu-id="6573d-131">this</span></span>](../../../csharp/language-reference/keywords/this.md)
- [<span data-ttu-id="6573d-132">namespace</span><span class="sxs-lookup"><span data-stu-id="6573d-132">namespace</span></span>](../../../csharp/language-reference/keywords/namespace.md)
