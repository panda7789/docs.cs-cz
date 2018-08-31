---
title: Using static – direktiva (referenční dokumentace jazyka C#)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e7368a6b6a4453f2dd07c7afdc0bffa7473ed1
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257461"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="cd288-102">Using static – direktiva (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cd288-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="cd288-103">`using static` – Direktiva Určuje typ, jehož statické členy a vnořené typy, které máte přístup bez určení názvu typu.</span><span class="sxs-lookup"><span data-stu-id="cd288-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="cd288-104">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="cd288-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="cd288-105">kde *plně kvalifikovaný type-name* je název typu, jehož statické členy a vnořené typy může být odkazováno bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="cd288-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="cd288-106">Pokud nezadáte plně kvalifikovaného názvu (název oboru názvů úplné spolu s názvem typu), C# vygeneruje Chyba kompilátoru [CS0246](../compiler-messages/cs0246.md): "typ nebo obor názvů 'typ nebo obor názvů' nebyl nalezen. (nechybí using – direktiva nebo odkaz na sestavení?) ".</span><span class="sxs-lookup"><span data-stu-id="cd288-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="cd288-107">`using static` – Direktiva se vztahuje na libovolný typ, který má statické členy (nebo vnořené typy), i když má také členy instance.</span><span class="sxs-lookup"><span data-stu-id="cd288-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="cd288-108">Však můžete členy instance volat pouze prostřednictvím instance typu.</span><span class="sxs-lookup"><span data-stu-id="cd288-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="cd288-109">`using static` – Direktiva byla zavedena v jazyce C# 6.</span><span class="sxs-lookup"><span data-stu-id="cd288-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd288-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd288-110">Remarks</span></span>
 
<span data-ttu-id="cd288-111">Při volání statického člena, který je obvykle zadat název typu spolu s názvem člena.</span><span class="sxs-lookup"><span data-stu-id="cd288-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="cd288-112">Opakovaně zadávat název typu pro vyvolání členy typu může mít za následek verbose, skrytého kódu.</span><span class="sxs-lookup"><span data-stu-id="cd288-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="cd288-113">Například následující definice `Circle` třídy odkazuje na počet členů <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="cd288-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="cd288-114">Že eliminuje nutnost explicitně odkazovat <xref:System.Math> třídy pokaždé, když se odkazuje člen, `using static` – direktiva vytvoří, jaká část čisticího modulu kódu:</span><span class="sxs-lookup"><span data-stu-id="cd288-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="cd288-115">`using static` Importuje pouze přístupné statické členy a vnořené typy deklarované v zadaném typu.</span><span class="sxs-lookup"><span data-stu-id="cd288-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="cd288-116">Zděděné členy nejsou naimportovány.</span><span class="sxs-lookup"><span data-stu-id="cd288-116">Inherited members are not imported.</span></span>  <span data-ttu-id="cd288-117">Můžete importovat z libovolný typ s názvem using static – direktiva, včetně modulů jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="cd288-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="cd288-118">Pokud funkce nejvyšší úrovně F # se zobrazí v metadatech jako statické členy pojmenovaného typu, jehož název je platný identifikátor jazyka C#, je možné importovat funkcí F #.</span><span class="sxs-lookup"><span data-stu-id="cd288-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="cd288-119">`using static` Díky rozšiřující metody deklarované v zadaném typu, který je k dispozici pro vyhledávání v metodě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="cd288-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="cd288-120">Nicméně názvy metod rozšíření nejsou naimportovány do oboru pro nekvalifikovaný odkaz v kódu.</span><span class="sxs-lookup"><span data-stu-id="cd288-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="cd288-121">Metody se stejným názvem importován z různých typů podle různých `using static` direktivy ve stejné jednotce kompilace nebo obor názvů tvoří skupinu metod.</span><span class="sxs-lookup"><span data-stu-id="cd288-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="cd288-122">Řešení přetížení v rámci těchto skupin metody následuje běžných pravidel jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cd288-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd288-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd288-123">Example</span></span>

<span data-ttu-id="cd288-124">V následujícím příkladu `using static` směrnice statické členy třídy <xref:System.Console>, <xref:System.Math>, a <xref:System.String> třídy, které jsou k dispozici bez nutnosti zadávat název jejich typu.</span><span class="sxs-lookup"><span data-stu-id="cd288-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="cd288-125">V tomto příkladu `using static` směrnice může také se použily <xref:System.Double> typu.</span><span class="sxs-lookup"><span data-stu-id="cd288-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="cd288-126">To by provedly to lze zavolat <xref:System.Double.TryParse(System.String,System.Double@)> metody bez určení názvu typu.</span><span class="sxs-lookup"><span data-stu-id="cd288-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="cd288-127">To však znamená méně čitelné kódu, protože bude nutné ke kontrole `using static` příkazy k určení číselného typu `TryParse` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="cd288-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd288-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd288-128">See also</span></span>

- [<span data-ttu-id="cd288-129">Using – direktiva</span><span class="sxs-lookup"><span data-stu-id="cd288-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="cd288-130">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd288-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="cd288-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd288-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="cd288-132">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="cd288-132">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="cd288-133">Klíčová slova oboru názvů</span><span class="sxs-lookup"><span data-stu-id="cd288-133">Namespace Keywords</span></span>](../../../csharp/language-reference/keywords/namespace-keywords.md)
- [<span data-ttu-id="cd288-134">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="cd288-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
