---
title: pomocí statické – direktiva (referenční dokumentace jazyka C#)
ms.date: 03/10/2017
helpviewer_keywords:
- using static directive [C#]
ms.assetid: 8b8f9e34-c75e-469b-ba85-6f2eb4090314
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9b7508c6e751f83fdc16a700ad68aa7de36e497
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285132"
---
# <a name="using-static-directive-c-reference"></a><span data-ttu-id="5a3bd-102">pomocí statické – direktiva (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5a3bd-102">using static Directive (C# Reference)</span></span>

<span data-ttu-id="5a3bd-103">`using static` – Direktiva označí typu jejichž statické členy dostanete bez určení názvu typu.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-103">The `using static` directive designates a type whose static members you can access without specifying a type name.</span></span> <span data-ttu-id="5a3bd-104">Jeho syntaxe je:</span><span class="sxs-lookup"><span data-stu-id="5a3bd-104">Its syntax is:</span></span>

```csharp
using static <fully-qualified-type-name>
```

<span data-ttu-id="5a3bd-105">kde *plně kvalifikovaný typ name* je název typu, jejichž statické členy může být odkazováno bez určení názvu typu.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-105">where *fully-qualified-type-name* is the name of the type whose static members can be referenced without specifying a type name.</span></span> <span data-ttu-id="5a3bd-106">Pokud nezadáte název plně kvalifikovaný typ (název úplné oboru názvů společně s název typu), C# vygeneruje Chyba kompilátoru CS0246: "typu nebo oboru názvů '< typ name >' nebyl nalezen."</span><span class="sxs-lookup"><span data-stu-id="5a3bd-106">If you do not provide a fully qualified type name (the full namespace name along with the type name), C# generates compiler error CS0246: "The type or namespace name '<type-name>' could not be found."</span></span>

<span data-ttu-id="5a3bd-107">`using static` – Direktiva platí pro žádný typ, který má statické členy, i v případě, že má také členů instance.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-107">The `using static` directive applies to any type that has static members, even if it also has instance members.</span></span> <span data-ttu-id="5a3bd-108">Ale členů instance jde volat jenom pomocí instance typu.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-108">However, instance members can only be invoked through the type instance.</span></span>

<span data-ttu-id="5a3bd-109">`using static` – Direktiva byla zavedena v C# 6.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-109">The `using static` directive was introduced in C# 6.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a3bd-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a3bd-110">Remarks</span></span>
 
<span data-ttu-id="5a3bd-111">Normálně při volání je statický člen, zadejte název typu společně s název člena.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-111">Ordinarily, when you call a static member, you provide the type name along with the member name.</span></span> <span data-ttu-id="5a3bd-112">Opakovaně zadejte přitom stejný název typu pro vyvolání členy typu, může mít za následek podrobné, skrytého kódu.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-112">Repeatedly entering the same type name to invoke members of the type can result in verbose, obscure code.</span></span> <span data-ttu-id="5a3bd-113">Například následující definice `Circle` třída odkazuje na počet členů <xref:System.Math> třídy.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-113">For example, the following definition of a `Circle` class references a number of members of the <xref:System.Math> class.</span></span>
  
[!code-csharp[using-static#1](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static1.cs#1)]

<span data-ttu-id="5a3bd-114">Odstraněním potřeba explicitně odkazovat <xref:System.Math> třídy pokaždé, když se odkazuje člena, `using static` – direktiva vytvoří mnoho čištění kódu:</span><span class="sxs-lookup"><span data-stu-id="5a3bd-114">By eliminating the need to explicitly reference the <xref:System.Math> class each time a member is referenced, the `using static` directive produces much cleaner code:</span></span>

[!code-csharp[using-static#2](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static2.cs#1)]

<span data-ttu-id="5a3bd-115">`using static` Importuje pouze přístupné statické členy a vnořené typy, které jsou deklarované v zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-115">`using static` imports only accessible static members and nested types declared in the specified type.</span></span>  <span data-ttu-id="5a3bd-116">Zděděné členy nebyly naimportovány.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-116">Inherited members are not imported.</span></span>  <span data-ttu-id="5a3bd-117">Můžete importovat ze všech typů s názvem použití statické direktiva, včetně moduly jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-117">You can import from any named type with a using static directive, including Visual Basic modules.</span></span>  <span data-ttu-id="5a3bd-118">Pokud funkce vysoké úrovně F # se zobrazí v metadatech jako statické členy s názvem typu, jehož jméno je platný identifikátor C#, lze importovat funkce F #.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-118">If F# top-level functions appear in metadata as static members of a named type whose name is a valid C# identifier, then the F# functions can be imported.</span></span>  
  
 <span data-ttu-id="5a3bd-119">`using static` Díky rozšiřující metody, které jsou deklarované v zadaný typ, který je k dispozici pro rozšíření metoda vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-119">`using static` makes extension methods declared in the specified type available for extension method lookup.</span></span>  <span data-ttu-id="5a3bd-120">Názvy metod rozšíření však nejsou naimportovány do oboru pro neúplné odkaz v kódu.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-120">However, the names of the extension methods are not imported into scope for unqualified reference in code.</span></span>  
  
 <span data-ttu-id="5a3bd-121">Metody se stejným názvem importovat z různých typů pomocí různých `using static` direktivy v oboru názvů na stejnou jednotku kompilace tvoří skupinu metoda.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-121">Methods with the same name imported from different types by different `using static` directives in the same compilation unit or namespace form a method group.</span></span>  <span data-ttu-id="5a3bd-122">Řešení přetížení v rámci těchto skupin metoda odpovídá normální C# pravidla.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-122">Overload resolution within these method groups follows normal C# rules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a3bd-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a3bd-123">Example</span></span>

<span data-ttu-id="5a3bd-124">Následující příklad používá `using static` – direktiva, aby statické členy <xref:System.Console>, <xref:System.Math>, a <xref:System.String> třídy, které jsou k dispozici bez nutnosti zadávat název jejich typu.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-124">The following example uses the `using static` directive to make the static members of the <xref:System.Console>, <xref:System.Math>, and <xref:System.String> classes available without having to specify their type name.</span></span>

[!code-csharp[using-static#3](../../../../samples/snippets/csharp/language-reference/keywords/using/using-static3.cs)]

<span data-ttu-id="5a3bd-125">V příkladu `using static` – direktiva může také se aplikovaly <xref:System.Double> typu.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-125">In the example, the `using static` directive could also have been applied to the <xref:System.Double> type.</span></span> <span data-ttu-id="5a3bd-126">To by provedli ho lze volat <xref:System.Double.TryParse(System.String,System.Double@)> metoda bez určení názvu typu.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-126">This would have made it possible to call the <xref:System.Double.TryParse(System.String,System.Double@)> method without specifying a type name.</span></span> <span data-ttu-id="5a3bd-127">To však znamená méně čitelný kód, vzhledem k tomu, že bude nutné zkontrolovat `using static` tvrzení, abyste zjistili, jaké číselného typu `TryParse` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="5a3bd-127">However, this creates less readable code, since it becomes necessary to check the `using static` statements to determine which numeric type's `TryParse` method is called.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a3bd-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a3bd-128">See also</span></span>

<span data-ttu-id="5a3bd-129">[Using – direktiva](using-directive.md) </span><span class="sxs-lookup"><span data-stu-id="5a3bd-129">[using directive](using-directive.md) </span></span>  
<span data-ttu-id="5a3bd-130">[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5a3bd-130">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="5a3bd-131">[Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="5a3bd-131">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="5a3bd-132">[Použití oboru názvů](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="5a3bd-132">[Using Namespaces](../../../csharp/programming-guide/namespaces/using-namespaces.md) </span></span>  
<span data-ttu-id="5a3bd-133">[Namespace klíčová slova](../../../csharp/language-reference/keywords/namespace-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="5a3bd-133">[Namespace Keywords](../../../csharp/language-reference/keywords/namespace-keywords.md) </span></span>  
[<span data-ttu-id="5a3bd-134">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="5a3bd-134">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)   
