---
title: Using static – direktiva - C# odkaz
ms.custom: seodec18
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4fa8dc3c043665ca2f56facf516cb03e5c6bb9d7
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421764"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="8bd77-102">Using static – direktiva (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="8bd77-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="8bd77-103">`using static` – Direktiva Určuje typ, jehož statické členy a vnořené typy, které máte přístup bez určení názvu typu.</span><span class="sxs-lookup"><span data-stu-id="8bd77-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="8bd77-104">Syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="8bd77-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="8bd77-105">kde *plně kvalifikovaný type-name* je název typu, jehož statické členy a vnořené typy může být odkazováno bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="8bd77-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="8bd77-106">Pokud nezadáte plně kvalifikovaného názvu (úplná obor názvů spolu s názvem typu), C# vygeneruje Chyba kompilátoru [CS0246](../compiler-messages/cs0246.md): "Nebyl nalezen typ nebo obor názvů"typ nebo obor názvů. (nechybí using – direktiva nebo odkaz na sestavení?) ".</span><span class="sxs-lookup"><span data-stu-id="8bd77-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="8bd77-107">`using static` – Direktiva se vztahuje na libovolný typ, který má statické členy (nebo vnořené typy), i když má také členy instance.</span><span class="sxs-lookup"><span data-stu-id="8bd77-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="8bd77-108">Však můžete členy instance volat pouze prostřednictvím instance typu.</span><span class="sxs-lookup"><span data-stu-id="8bd77-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="8bd77-109">`using static` – Direktiva byla zavedena v jazyce C# 6.</span><span class="sxs-lookup"><span data-stu-id="8bd77-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="8bd77-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bd77-110">Remarks</span></span>

<span data-ttu-id="8bd77-111">Při volání statického člena, který je obvykle zadat název typu spolu s názvem člena.</span><span class="sxs-lookup"><span data-stu-id="8bd77-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="8bd77-112">Opakovaně zadávat název typu pro vyvolání členy typu může mít za následek verbose, skrytého kódu.</span><span class="sxs-lookup"><span data-stu-id="8bd77-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="8bd77-113">Například následující definice `Circle` třídy odkazuje na počet členů <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="8bd77-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="8bd77-114">Že eliminuje nutnost explicitně odkazovat <xref:System.Math> třídy pokaždé, když se odkazuje člen, `using static` – direktiva vytvoří, jaká část čisticího modulu kódu:</span><span class="sxs-lookup"><span data-stu-id="8bd77-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="8bd77-115">`using static` Importuje pouze přístupné statické členy a vnořené typy deklarované v zadaném typu.</span><span class="sxs-lookup"><span data-stu-id="8bd77-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="8bd77-116">Zděděné členy nejsou naimportovány.</span><span class="sxs-lookup"><span data-stu-id="8bd77-116">Inherited members are not imported.</span></span>  <span data-ttu-id="8bd77-117">Můžete importovat z libovolný typ s názvem using static – direktiva, včetně modulů jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8bd77-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="8bd77-118">Pokud F# nejvyšší úrovně funkce se zobrazí v metadatech jako statické členy pojmenovaného typu, jehož název je platný C# identifikátor, pak bude F# funkce lze importovat.</span><span class="sxs-lookup"><span data-stu-id="8bd77-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="8bd77-119">`using static` Díky rozšiřující metody deklarované v zadaném typu, který je k dispozici pro vyhledávání v metodě rozšíření.</span><span class="sxs-lookup"><span data-stu-id="8bd77-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="8bd77-120">Nicméně názvy metod rozšíření nejsou naimportovány do oboru pro nekvalifikovaný odkaz v kódu.</span><span class="sxs-lookup"><span data-stu-id="8bd77-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="8bd77-121">Metody se stejným názvem importován z různých typů podle různých `using static` direktivy ve stejné jednotce kompilace nebo obor názvů tvoří skupinu metod.</span><span class="sxs-lookup"><span data-stu-id="8bd77-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="8bd77-122">Řešení přetížení v rámci těchto skupin metody následuje běžných pravidel jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="8bd77-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="8bd77-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="8bd77-123">Example</span></span>

<span data-ttu-id="8bd77-124">V následujícím příkladu `using static` směrnice statické členy třídy <xref:System.Console>, <xref:System.Math>, a <xref:System.String> třídy, které jsou k dispozici bez nutnosti zadávat název jejich typu.</span><span class="sxs-lookup"><span data-stu-id="8bd77-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="8bd77-125">V tomto příkladu `using static` směrnice může také se použily <xref:System.Double> typu.</span><span class="sxs-lookup"><span data-stu-id="8bd77-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="8bd77-126">To by provedly to lze zavolat <xref:System.Double.TryParse(System.String,System.Double@)> metody bez určení názvu typu.</span><span class="sxs-lookup"><span data-stu-id="8bd77-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="8bd77-127">To však znamená méně čitelné kódu, protože bude nutné ke kontrole `using static` příkazy k určení číselného typu `TryParse` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="8bd77-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="8bd77-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bd77-128">See also</span></span>

- [<span data-ttu-id="8bd77-129">Using – direktiva</span><span class="sxs-lookup"><span data-stu-id="8bd77-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="8bd77-130">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8bd77-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8bd77-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8bd77-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8bd77-132">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="8bd77-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="8bd77-133">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="8bd77-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
