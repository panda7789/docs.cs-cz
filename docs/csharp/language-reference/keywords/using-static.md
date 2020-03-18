---
title: použití statické direktivy – odkaz jazyka C#
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 55847aceb9fdf032ba533b82ee59be53761fa2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712946"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="d8bcf-102">pomocí statické direktivy (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="d8bcf-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="d8bcf-103">Směrnice `using static` určuje typ, jehož statické členy a vnořené typy můžete přistupovat bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="d8bcf-104">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="d8bcf-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="d8bcf-105">kde *plně kvalifikovaný název typu* je název typu, na jehož statické členy a vnořené typy lze odkazovat bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="d8bcf-106">Pokud nezadáte plně kvalifikovaný název typu (úplný název oboru názvů spolu s názvem typu), c# generuje chybu kompilátoru [CS0246](../compiler-messages/cs0246.md): "Typ nebo název oboru názvů 'typ/obor názvů' nebyl nalezen (chybí vám using directive nebo odkaz na sestavení?)".</span><span class="sxs-lookup"><span data-stu-id="d8bcf-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="d8bcf-107">Směrnice `using static` platí pro všechny typy, které má statické členy (nebo vnořené typy), i v případě, že má také členy instance.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="d8bcf-108">Členové instance však mohou být vyvoláni pouze prostřednictvím instance typu.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="d8bcf-109">Směrnice `using static` byla zavedena v C# 6.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8bcf-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8bcf-110">Remarks</span></span>

<span data-ttu-id="d8bcf-111">Obvykle při volání statického člena zadáte název typu spolu s názvem člena.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="d8bcf-112">Opakované zadání stejného názvu typu k vyvolání členů typu může mít za následek podrobný, obskurní kód.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="d8bcf-113">Například následující definice `Circle` třídy odkazuje na několik členů <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="d8bcf-114">Tím, že eliminuje potřebu <xref:System.Math> explicitně odkazovat na třídu `using static` pokaždé, když je odkazováno na člen, směrnice vytváří mnohem čistší kód:</span><span class="sxs-lookup"><span data-stu-id="d8bcf-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="d8bcf-115">`using static`importuje pouze přístupné statické členy a vnořené typy deklarované v zadaném typu.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="d8bcf-116">Zděděné členy nejsou importovány.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-116">Inherited members are not imported.</span></span>  <span data-ttu-id="d8bcf-117">Můžete importovat z libovolného pojmenovaného typu pomocí statické směrnice, včetně modulů jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="d8bcf-118">Pokud f# funkce nejvyšší úrovně se zobrazí v metadatech jako statické členy pojmenovaného typu, jehož název je platný identifikátor Jazyka C#, pak f# funkce lze importovat.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="d8bcf-119">`using static`zpřístupní metody rozšíření deklarované v zadaném typu pro vyhledávání metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="d8bcf-120">Názvy rozšiřujících metod však nejsou importovány do oboru pro neúplný odkaz v kódu.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="d8bcf-121">Metody se stejným názvem importované z `using static` různých typů různými direktivami ve stejné kompilační jednotce nebo oboru názvů tvoří skupinu metod.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="d8bcf-122">Řešení přetížení v rámci těchto skupin metod se řídí normálními pravidly jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="d8bcf-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8bcf-123">Example</span></span>

<span data-ttu-id="d8bcf-124">Následující příklad používá `using static` direktivu k <xref:System.Console> <xref:System.Math>zpřístupnění <xref:System.String> statických členů , a tříd bez nutnosti zadávat jejich název typu.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="d8bcf-125">V příkladu `using static` směrnice může být také <xref:System.Double> použita na typ.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="d8bcf-126">To by umožnilo volat <xref:System.Double.TryParse(System.String,System.Double@)> metodu bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="d8bcf-127">Tím se však vytvoří méně čitelný kód, `using static` protože je nutné zkontrolovat `TryParse` příkazy k určení, která metoda číselného typu je volána.</span><span class="sxs-lookup"><span data-stu-id="d8bcf-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8bcf-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8bcf-128">See also</span></span>

- [<span data-ttu-id="d8bcf-129">pomocí směrnice</span><span class="sxs-lookup"><span data-stu-id="d8bcf-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="d8bcf-130">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d8bcf-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d8bcf-131">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="d8bcf-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d8bcf-132">Použití oborů názvů</span><span class="sxs-lookup"><span data-stu-id="d8bcf-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="d8bcf-133">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="d8bcf-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
