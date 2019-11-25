---
title: Postup implementace a volání vlastní metody rozšíření – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- extension methods [C#], implementing and calling
ms.assetid: 7dab2a56-cf8e-4a47-a444-fe610a02772a
ms.openlocfilehash: f3d96c033380698ade37c49ecbfeed14f05d3e11
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970897"
---
# <a name="how-to-implement-and-call-a-custom-extension-method-c-programming-guide"></a><span data-ttu-id="3ee62-102">Postup implementace a volání vlastní metody rozšíření (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="3ee62-102">How to implement and call a custom extension method (C# Programming Guide)</span></span>
<span data-ttu-id="3ee62-103">Toto téma ukazuje, jak implementovat vlastní metody rozšíření pro libovolný typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3ee62-103">This topic shows how to implement your own extension methods for any .NET type.</span></span> <span data-ttu-id="3ee62-104">Kód klienta může použít vaše metody rozšíření přidáním odkazu na knihovnu DLL, který obsahuje, a přidáním direktivy [using](../../language-reference/keywords/using-directive.md) , která určuje obor názvů, ve kterém jsou definovány metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3ee62-104">Client code can use your extension methods by adding a reference to the DLL that contains them, and adding a [using](../../language-reference/keywords/using-directive.md) directive that specifies the namespace in which the extension methods are defined.</span></span>  
  
## <a name="to-define-and-call-the-extension-method"></a><span data-ttu-id="3ee62-105">Definování a volání metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="3ee62-105">To define and call the extension method</span></span>  
  
1. <span data-ttu-id="3ee62-106">Definujte statickou [třídu](./static-classes-and-static-class-members.md) , která bude obsahovat metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3ee62-106">Define a static [class](./static-classes-and-static-class-members.md) to contain the extension method.</span></span>  
  
     <span data-ttu-id="3ee62-107">Třída musí být viditelná pro klientský kód.</span><span class="sxs-lookup"><span data-stu-id="3ee62-107">The class must be visible to client code.</span></span> <span data-ttu-id="3ee62-108">Další informace o pravidlech přístupnosti najdete v tématu [modifikátory přístupu](./access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="3ee62-108">For more information about accessibility rules, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
2. <span data-ttu-id="3ee62-109">Implementujte metodu rozšíření jako statickou metodu s alespoň stejnou viditelností jako obsahující třídu.</span><span class="sxs-lookup"><span data-stu-id="3ee62-109">Implement the extension method as a static method with at least the same visibility as the containing class.</span></span>  
  
3. <span data-ttu-id="3ee62-110">První parametr metody určuje typ, na kterém metoda funguje; před ním musí být uveden [Tento](../../language-reference/keywords/this.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="3ee62-110">The first parameter of the method specifies the type that the method operates on; it must be preceded with the [this](../../language-reference/keywords/this.md) modifier.</span></span>  
  
4. <span data-ttu-id="3ee62-111">V kódu volajícího přidejte direktivu `using` pro určení [oboru názvů](../../language-reference/keywords/namespace.md) , který obsahuje třídu metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="3ee62-111">In the calling code, add a `using` directive to specify the [namespace](../../language-reference/keywords/namespace.md) that contains the extension method class.</span></span>  
  
5. <span data-ttu-id="3ee62-112">Zavolejte metody, jako by šlo o metody instance pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="3ee62-112">Call the methods as if they were instance methods on the type.</span></span>  
  
     <span data-ttu-id="3ee62-113">Všimněte si, že první parametr není specifikován voláním kódu, protože představuje typ, na kterém je operátor použit, a kompilátor již zná typ objektu.</span><span class="sxs-lookup"><span data-stu-id="3ee62-113">Note that the first parameter is not specified by calling code because it represents the type on which the operator is being applied, and the compiler already knows the type of your object.</span></span> <span data-ttu-id="3ee62-114">Je nutné zadat argumenty pro parametry 2 až `n`.</span><span class="sxs-lookup"><span data-stu-id="3ee62-114">You only have to provide arguments for parameters 2 through `n`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ee62-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ee62-115">Example</span></span>  
 <span data-ttu-id="3ee62-116">Následující příklad implementuje metodu rozšíření s názvem `WordCount` ve třídě `CustomExtensions.StringExtension`.</span><span class="sxs-lookup"><span data-stu-id="3ee62-116">The following example implements an extension method named `WordCount` in the `CustomExtensions.StringExtension` class.</span></span> <span data-ttu-id="3ee62-117">Metoda pracuje na třídě <xref:System.String>, která je zadána jako první parametr metody.</span><span class="sxs-lookup"><span data-stu-id="3ee62-117">The method operates on the <xref:System.String> class, which is specified as the first method parameter.</span></span> <span data-ttu-id="3ee62-118">Obor názvů `CustomExtensions` je importován do oboru názvů aplikace a metoda je volána uvnitř metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="3ee62-118">The `CustomExtensions` namespace is imported into the application namespace, and the method is called inside the `Main` method.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExtensionMethods/cs/extensionmethods.cs#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="3ee62-119">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3ee62-119">.NET Framework Security</span></span>  
 <span data-ttu-id="3ee62-120">Metody rozšíření nepředstavují žádné konkrétní chyby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3ee62-120">Extension methods present no specific security vulnerabilities.</span></span> <span data-ttu-id="3ee62-121">Nemohou být nikdy použity k zosobnění existujících metod pro typ, protože všechny kolize názvů jsou vyřešeny ve prospěch instance nebo statické metody definované samotným typem.</span><span class="sxs-lookup"><span data-stu-id="3ee62-121">They can never be used to impersonate existing methods on a type, because all name collisions are resolved in favor of the instance or static method defined by the type itself.</span></span> <span data-ttu-id="3ee62-122">Metody rozšíření nemají přístup k žádným soukromým datům v rozšířené třídě.</span><span class="sxs-lookup"><span data-stu-id="3ee62-122">Extension methods cannot access any private data in the extended class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee62-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3ee62-123">See also</span></span>

- [<span data-ttu-id="3ee62-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3ee62-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3ee62-125">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="3ee62-125">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="3ee62-126">LINQ (jazykově integrovaný dotaz)</span><span class="sxs-lookup"><span data-stu-id="3ee62-126">LINQ (Language-Integrated Query)</span></span>](../../linq/linq-in-csharp.md)
- [<span data-ttu-id="3ee62-127">Statické třídy a jejich členové</span><span class="sxs-lookup"><span data-stu-id="3ee62-127">Static Classes and Static Class Members</span></span>](./static-classes-and-static-class-members.md)
- [<span data-ttu-id="3ee62-128">protected</span><span class="sxs-lookup"><span data-stu-id="3ee62-128">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="3ee62-129">internal</span><span class="sxs-lookup"><span data-stu-id="3ee62-129">internal</span></span>](../../language-reference/keywords/internal.md)
- [<span data-ttu-id="3ee62-130">public</span><span class="sxs-lookup"><span data-stu-id="3ee62-130">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="3ee62-131">this</span><span class="sxs-lookup"><span data-stu-id="3ee62-131">this</span></span>](../../language-reference/keywords/this.md)
- [<span data-ttu-id="3ee62-132">namespace</span><span class="sxs-lookup"><span data-stu-id="3ee62-132">namespace</span></span>](../../language-reference/keywords/namespace.md)
