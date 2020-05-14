---
title: použití statické direktivy – Reference jazyka C#
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
ms.openlocfilehash: bffbc026e8f7937db91d42b7a06a5b7bba3bc2f8
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396154"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="8bbe1-102">using static – direktiva (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8bbe1-102">using static directive (C# Reference)</span></span>

<span data-ttu-id="8bbe1-103">Tato `using static` direktiva určuje typ, jehož statické členy a vnořené typy mají přístup bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-103">The `using static` directive designates a type whose static members and nested types you can access without specifying a type name.</span></span> <span data-ttu-id="8bbe1-104">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="8bbe1-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>;
```

<span data-ttu-id="8bbe1-105">kde *název plně kvalifikovaného typu* je název typu, jehož statické členy a vnořené typy mohou být odkazovány bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-105">where *fully-qualified-type-name* is the name of the type whose static members and nested types can be referenced without specifying a type name.</span></span> <span data-ttu-id="8bbe1-106">Pokud nezadáte plně kvalifikovaný název typu (úplný název oboru názvů spolu s názvem typu), C# generuje chybu kompilátoru [CS0246](../compiler-messages/cs0246.md): "typ nebo obor názvů ' Type/namespace ' nebyl nalezen (nechybí Direktiva using nebo odkaz na sestavení?)".</span><span class="sxs-lookup"><span data-stu-id="8bbe1-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error [CS0246](../compiler-messages/cs0246.md): "The type or namespace name 'type/namespace' could not be found (are you missing a using directive or an assembly reference?)".</span></span>

<span data-ttu-id="8bbe1-107">`using static`Direktiva se vztahuje na libovolný typ, který má statické členy (nebo vnořené typy), i když má také členy instance.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-107">The `using static` directive applies to any type that has static members (or nested types), even if it also has instance members.</span></span> <span data-ttu-id="8bbe1-108">Členy instance lze však vyvolat pouze prostřednictvím instance typu.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="8bbe1-109">`using static`Direktiva byla představena v C# 6.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="8bbe1-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bbe1-110">Remarks</span></span>

<span data-ttu-id="8bbe1-111">Obvykle při volání statického členu zadáte název typu společně s názvem člena.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="8bbe1-112">Opakované zadání stejného názvu typu pro vyvolání členů typu může mít za následek verbose, zakrytí kódu.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="8bbe1-113">Například následující definice `Circle` třídy odkazuje na určitý počet členů <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>

[!code-csharp[using-static#1](~/samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="8bbe1-114">Zrušením nutnosti explicitního odkazování na <xref:System.Math> třídu pokaždé, když na člena je odkazováno, tato `using static` direktiva vytvoří mnohem čisticí kód:</span><span class="sxs-lookup"><span data-stu-id="8bbe1-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](~/samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="8bbe1-115">`using static`importuje pouze dostupné statické členy a vnořené typy deklarované v zadaném typu.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="8bbe1-116">Zděděné členy nejsou naimportovány.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-116">Inherited members are not imported.</span></span>  <span data-ttu-id="8bbe1-117">Můžete importovat z libovolného pojmenovaného typu pomocí statické direktivy using, včetně Visual Basicch modulů.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="8bbe1-118">Pokud jsou funkce nejvyšší úrovně F # zobrazeny v metadatech jako statické členy pojmenovaného typu, jehož název je platný identifikátor jazyka C#, mohou být importovány funkce jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>

 <span data-ttu-id="8bbe1-119">`using static`Zpřístupňuje metody rozšíření deklarované v zadaném typu k dispozici pro vyhledávání rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="8bbe1-120">Názvy metod rozšíření však nejsou importovány do oboru pro nekvalifikované odkazy v kódu.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>

 <span data-ttu-id="8bbe1-121">Metody se stejným názvem importované z různých typů podle různých `using static` direktiv ve stejné kompilační jednotce nebo oboru názvů tvoří skupinu metod.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="8bbe1-122">Rozlišení přetížení v rámci těchto skupin metod sleduje normální pravidla jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-122">Overload resolution within these method groups follows normal C# rules.</span></span>

## <a name="example"></a><span data-ttu-id="8bbe1-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="8bbe1-123">Example</span></span>

<span data-ttu-id="8bbe1-124">V následujícím příkladu je použita `using static` direktiva k tomu, aby byly statické <xref:System.Console> členy <xref:System.Math> tříd, a <xref:System.String> dostupné bez nutnosti zadat jejich název typu.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](~/samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="8bbe1-125">V tomto příkladu `using static` byla direktiva také použita pro <xref:System.Double> typ.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="8bbe1-126">To by mělo být umožněno volání <xref:System.Double.TryParse(System.String,System.Double@)> metody bez zadání názvu typu.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="8bbe1-127">Tím se však vytvoří méně čitelný kód, protože je nutné ověřit `using static` direktivy, abyste zjistili, která metoda číselného typu `TryParse` je volána.</span><span class="sxs-lookup"><span data-stu-id="8bbe1-127">However, this creates less readable code, since it becomes necessary to check the `using static` directives to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="8bbe1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bbe1-128">See also</span></span>

- [<span data-ttu-id="8bbe1-129">using – direktiva</span><span class="sxs-lookup"><span data-stu-id="8bbe1-129">using directive</span></span>](using-directive.md)
- [<span data-ttu-id="8bbe1-130">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8bbe1-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8bbe1-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8bbe1-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8bbe1-132">Používání oborů názvů</span><span class="sxs-lookup"><span data-stu-id="8bbe1-132">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="8bbe1-133">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="8bbe1-133">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
