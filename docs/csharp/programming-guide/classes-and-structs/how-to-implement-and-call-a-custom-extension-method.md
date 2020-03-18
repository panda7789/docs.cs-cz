---
title: Jak implementovat a volat vlastní metodu rozšíření - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: 7e2092a37c1f042a087e03f4a272139b585156c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705597"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="14dd4-102">Jak implementovat a volat vlastní metodu rozšíření (C# Programovací průvodce)</span><span class="sxs-lookup"><span data-stu-id="14dd4-102">How to implement and call a custom extension method (C# Programming Guide)</span></span>
<span data-ttu-id="14dd4-103">Toto téma ukazuje, jak implementovat vlastní metody rozšíření pro libovolný typ .NET.</span><span class="sxs-lookup"><span data-stu-id="14dd4-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="14dd4-104">Klientský kód můžete použít metody rozšíření přidáním odkazu na DLL, která je obsahuje a [přidáníusing](../../language-reference/keywords/using-directive.md) směrnice, která určuje obor názvů, ve kterém jsou definovány metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="14dd4-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="14dd4-105">Definování a volání metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="14dd4-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="14dd4-106">Definujte statickou [třídu,](./static-classes-and-static-class-members.md) která bude obsahovat metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="14dd4-106">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="14dd4-107">Třída musí být viditelná pro kód klienta.</span><span class="sxs-lookup"><span data-stu-id="14dd4-107">The class must be visible to client code.</span></span> <span data-ttu-id="14dd4-108">Další informace o pravidlech usnadnění naleznete [v tématu Access Modifiers](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="14dd4-108">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="14dd4-109">Implementujte metodu rozšíření jako statickou metodu s alespoň stejnou viditelností jako obsahující třída.</span><span class="sxs-lookup"><span data-stu-id="14dd4-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="14dd4-110">První parametr metody určuje typ, na kterém metoda pracuje; musí předcházet [tento](../../language-reference/keywords/this.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="14dd4-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="14dd4-111">V volajícím kódu `using` přidejte direktivu, která určí [obor názvů,](../../language-reference/keywords/namespace.md) který obsahuje třídu metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="14dd4-111">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="14dd4-112">Volání metod, jako kdyby byly instance metody na typu.</span><span class="sxs-lookup"><span data-stu-id="14dd4-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="14dd4-113">Všimněte si, že první parametr není určen voláním kódu, protože představuje typ, na kterém je operátor aplikován, a kompilátor již zná typ objektu.</span><span class="sxs-lookup"><span data-stu-id="14dd4-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="14dd4-114">Je třeba zadat pouze argumenty pro `n`parametry 2 až .</span><span class="sxs-lookup"><span data-stu-id="14dd4-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14dd4-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="14dd4-115">Example</span></span>  
 <span data-ttu-id="14dd4-116">Následující příklad implementuje metodu rozšíření pojmenovanou `WordCount` ve `CustomExtensions.StringExtension` třídě.</span><span class="sxs-lookup"><span data-stu-id="14dd4-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="14dd4-117">Metoda pracuje na <xref:System.String> třídu, která je určena jako první parametr metody.</span><span class="sxs-lookup"><span data-stu-id="14dd4-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="14dd4-118">Obor `CustomExtensions` názvů je importován do oboru názvů aplikace a `Main` metoda je volána uvnitř metody.</span><span class="sxs-lookup"><span data-stu-id="14dd4-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="14dd4-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="14dd4-119">.NET Framework Security</span></span>  
 <span data-ttu-id="14dd4-120">Metody rozšíření nepředstavují žádné konkrétní chyby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="14dd4-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="14dd4-121">Nikdy nelze použít k zosobnění existující metody na typu, protože všechny kolize názvů jsou vyřešeny ve prospěch instance nebo statické metody definované samotným typem.</span><span class="sxs-lookup"><span data-stu-id="14dd4-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="14dd4-122">Rozšiřující metody nelze získat přístup k žádné soukromé data v rozšířené třídy.</span><span class="sxs-lookup"><span data-stu-id="14dd4-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14dd4-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="14dd4-123">See also</span></span>

- [<span data-ttu-id="14dd4-124">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="14dd4-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="14dd4-125">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="14dd4-125">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="14dd4-126">LINQ (dotaz integrovaný jazykem)</span><span class="sxs-lookup"><span data-stu-id="14dd4-126">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="14dd4-127">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="14dd4-127">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="14dd4-128">protected</span><span class="sxs-lookup"><span data-stu-id="14dd4-128">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="14dd4-129">Vnitřní</span><span class="sxs-lookup"><span data-stu-id="14dd4-129">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="14dd4-130">Veřejné</span><span class="sxs-lookup"><span data-stu-id="14dd4-130">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="14dd4-131">tohoto provozu</span><span class="sxs-lookup"><span data-stu-id="14dd4-131">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="14dd4-132">Namespace</span><span class="sxs-lookup"><span data-stu-id="14dd4-132">namespace</span></span>](../../language-reference/keywords/namespace.md)
