---
title: použití statické direktivy C# – reference
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: 55847aceb9fdf032ba533b82ee59be53761fa2c2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712946"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="1a66e-102">using static – direktiva (C# Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="1a66e-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="1a66e-103">Direktiva `using static` označuje typ, jehož statické členy a vnořené typy mají přístup bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="1a66e-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="1a66e-104">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="1a66e-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="1a66e-105">kde *název plně kvalifikovaného typu* je název typu, jehož statické členy a vnořené typy mohou být odkazovány bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="1a66e-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="1a66e-106">Pokud nezadáte plně kvalifikovaný název typu (úplný název oboru názvů spolu s názvem typu), C# vygeneruje chybu kompilátoru [CS0246](../compiler-messages/cs0246.md): "typ nebo obor názvů ' Type/namespace ' nebyl nalezen (nechybí Direktiva using nebo odkaz na sestavení?)".</span><span class="sxs-lookup"><span data-stu-id="1a66e-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="1a66e-107">Direktiva `using static` se vztahuje na jakýkoli typ, který má statické členy (neboli vnořené typy), i když má také členy instance.</span><span class="sxs-lookup"><span data-stu-id="1a66e-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="1a66e-108">Členy instance lze však vyvolat pouze prostřednictvím instance typu.</span><span class="sxs-lookup"><span data-stu-id="1a66e-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="1a66e-109">Direktiva `using static` byla představena C# v 6.</span><span class="sxs-lookup"><span data-stu-id="1a66e-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a66e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a66e-110">Remarks</span></span>

<span data-ttu-id="1a66e-111">Obvykle při volání statického členu zadáte název typu společně s názvem člena.</span><span class="sxs-lookup"><span data-stu-id="1a66e-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="1a66e-112">Opakované zadání stejného názvu typu pro vyvolání členů typu může mít za následek verbose, zakrytí kódu.</span><span class="sxs-lookup"><span data-stu-id="1a66e-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="1a66e-113">Například následující definice `Circle` třídy odkazuje na řadu členů <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="1a66e-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="1a66e-114">Zrušením nutnosti explicitního odkazování na třídu <xref:System.Math> pokaždé, když na člena odkazuje, direktiva `using static` vytvoří mnohem čisticí kód:</span><span class="sxs-lookup"><span data-stu-id="1a66e-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="1a66e-115">`using static` importuje pouze dostupné statické členy a vnořené typy deklarované v zadaném typu.</span><span class="sxs-lookup"><span data-stu-id="1a66e-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="1a66e-116">Zděděné členy nejsou naimportovány.</span><span class="sxs-lookup"><span data-stu-id="1a66e-116">Inherited members are not imported.</span></span>  <span data-ttu-id="1a66e-117">Můžete importovat z libovolného pojmenovaného typu pomocí statické direktivy using, včetně Visual Basicch modulů.</span><span class="sxs-lookup"><span data-stu-id="1a66e-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="1a66e-118">Pokud F# jsou funkce nejvyšší úrovně zobrazeny v metadatech jako statické členy pojmenovaného typu, jehož název je platný C# identifikátor, lze F# funkce importovat.</span><span class="sxs-lookup"><span data-stu-id="1a66e-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="1a66e-119">`using static` zpřístupňuje metody rozšíření deklarované v zadaném typu pro vyhledávání rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="1a66e-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="1a66e-120">Názvy metod rozšíření však nejsou importovány do oboru pro nekvalifikované odkazy v kódu.</span><span class="sxs-lookup"><span data-stu-id="1a66e-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="1a66e-121">Metody se stejným názvem importované z různých typů pomocí různých direktiv `using static` ve stejné kompilační jednotce nebo oboru názvů tvoří skupinu metod.</span><span class="sxs-lookup"><span data-stu-id="1a66e-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="1a66e-122">Rozlišení přetížení v rámci těchto skupin metod dodržuje normální C# pravidla.</span><span class="sxs-lookup"><span data-stu-id="1a66e-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="1a66e-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a66e-123">Example</span></span>

<span data-ttu-id="1a66e-124">V následujícím příkladu je použita direktiva `using static` k zpřístupnění statických členů tříd <xref:System.Console>, <xref:System.Math>a <xref:System.String>, aniž by bylo nutné určit jejich název typu.</span><span class="sxs-lookup"><span data-stu-id="1a66e-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="1a66e-125">V tomto příkladu by mohla být také použita direktiva `using static` na typ <xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="1a66e-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="1a66e-126">To by mělo být možné volat metodu <xref:System.Double.TryParse(System.String,System.Double@)> bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="1a66e-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="1a66e-127">To však vytvoří méně čitelný kód, protože je nutné kontrolovat `using static` příkazy k určení, která metoda `TryParse` číselného typu je volána.</span><span class="sxs-lookup"><span data-stu-id="1a66e-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a66e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a66e-128">See also</span></span>

- [<span data-ttu-id="1a66e-129">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="1a66e-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="1a66e-130">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="1a66e-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1a66e-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1a66e-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1a66e-132">Použití oboru názvů</span><span class="sxs-lookup"><span data-stu-id="1a66e-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="1a66e-133">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="1a66e-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
