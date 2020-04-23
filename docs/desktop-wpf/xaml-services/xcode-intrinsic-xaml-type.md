---
title: x:Code – vnitřní typ jazyka XAML
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071554"
---
# <a name="xcode-intrinsic-xaml-type"></a><span data-ttu-id="68c01-102">x:Code – vnitřní typ jazyka XAML</span><span class="sxs-lookup"><span data-stu-id="68c01-102">x:Code Intrinsic XAML Type</span></span>
<span data-ttu-id="68c01-103">Umožňuje umístění kódu v rámci výroby XAML.</span><span class="sxs-lookup"><span data-stu-id="68c01-103">Allows placement of code within a XAML production.</span></span> <span data-ttu-id="68c01-104">Takový kód může být buď zkompilován libovolnou implementací procesoru XAML, která zkompiluje XAML, nebo ponechán v produkci XAML pro pozdější použití, jako je interpretace runtime.</span><span class="sxs-lookup"><span data-stu-id="68c01-104">Such code can either be compiled by any XAML processor implementation that compiles XAML, or left in the XAML production for later uses such as interpretation by a runtime.</span></span>

## <a name="xaml-object-element-usage"></a><span data-ttu-id="68c01-105">Použití elementu objektu XAML</span><span class="sxs-lookup"><span data-stu-id="68c01-105">XAML Object Element Usage</span></span>

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a><span data-ttu-id="68c01-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68c01-106">Remarks</span></span>

<span data-ttu-id="68c01-107">Kód v `x:Code` rámci prvku direktivy XAML je stále interpretován v rámci obecného oboru názvů XML a k dispozici obory názvů XAML.</span><span class="sxs-lookup"><span data-stu-id="68c01-107">The code within the `x:Code` XAML directive element is still interpreted within the general XML namespace and the XAML namespaces provided.</span></span> <span data-ttu-id="68c01-108">Proto je obvykle nutné uzavřít kód používaný `x:Code` pro `CDATA` uvnitř segmentu.</span><span class="sxs-lookup"><span data-stu-id="68c01-108">Therefore, it is usually necessary to enclose the code used for `x:Code` inside a `CDATA` segment.</span></span>

<span data-ttu-id="68c01-109">`x:Code`není povoleno pro všechny možné mechanismy nasazení výroby XAML.</span><span class="sxs-lookup"><span data-stu-id="68c01-109">`x:Code` is not permitted for all possible deployment mechanisms of a XAML production.</span></span> <span data-ttu-id="68c01-110">Ve specifických architekturách (například WPF) musí být kód zkompilován.</span><span class="sxs-lookup"><span data-stu-id="68c01-110">In specific frameworks (for example WPF) the code must be compiled.</span></span> <span data-ttu-id="68c01-111">V jiných architekturách `x:Code` použití může být obecně zakázáno.</span><span class="sxs-lookup"><span data-stu-id="68c01-111">In other frameworks, `x:Code` usage might be generally disallowed.</span></span>

<span data-ttu-id="68c01-112">Pro architektury, které `x:Code` umožňují spravovaný obsah, `x:Code` správný kompilátor jazyka pro obsah je určen nastavení a cíle obsahující projekt, který se používá ke kompilaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="68c01-112">For frameworks that permit managed `x:Code` content, the correct language compiler to use for `x:Code` content is determined by settings and targets of the containing project that is used to compile the application.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="68c01-113">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="68c01-113">WPF Usage Notes</span></span>

<span data-ttu-id="68c01-114">Kód deklarovaný v rámci `x:Code` wpf má několik významných omezení:</span><span class="sxs-lookup"><span data-stu-id="68c01-114">Code declared within `x:Code` for WPF has several notable limitations:</span></span>

- <span data-ttu-id="68c01-115">Prvek `x:Code` směrnice musí být okamžitý podřízený prvek kořenový prvek výroby XAML.</span><span class="sxs-lookup"><span data-stu-id="68c01-115">The `x:Code` directive element must be an immediate child element of the root element of the XAML production.</span></span>

- <span data-ttu-id="68c01-116">[x:Class Směrnice](xclass-directive.md) musí být uvedeny na nadřazený kořenový prvek.</span><span class="sxs-lookup"><span data-stu-id="68c01-116">[x:Class Directive](xclass-directive.md) must be provided on the parent root element.</span></span>

- <span data-ttu-id="68c01-117">Kód umístěný `x:Code` v rámci bude zpracovánkompilací, která bude v rámci částečné třídy, která je již vytvořena pro tuto stránku XAML.</span><span class="sxs-lookup"><span data-stu-id="68c01-117">The code placed within `x:Code` will be treated by compilation to be within the scope of the partial class that is already being created for that XAML page.</span></span> <span data-ttu-id="68c01-118">Proto veškerý kód, který definujete, musí být členy nebo proměnnými této částečné třídy.</span><span class="sxs-lookup"><span data-stu-id="68c01-118">Therefore all code you define must be members or variables of that partial class.</span></span>

- <span data-ttu-id="68c01-119">Nelze definovat další třídy, jiné než vnoření třídy uvnitř částečné třídy (vnoření je povoleno, ale není typické, protože vnořené třídy nelze odkazovat v XAML).</span><span class="sxs-lookup"><span data-stu-id="68c01-119">You cannot define additional classes, other than by nesting a class inside the partial class (nesting is allowed, but it is not typical because nested classes cannot be referenced in XAML).</span></span> <span data-ttu-id="68c01-120">Obory názvů CLR jiné než obor názvů, který se používá pro existující částečnou třídu, nelze definovat ani přidat.</span><span class="sxs-lookup"><span data-stu-id="68c01-120">CLR namespaces other than the namespace that is used for the existing partial class cannot be defined or added to.</span></span>

- <span data-ttu-id="68c01-121">Odkazy na entity kódu mimo obor názvů CLR částečné třídy musí být všechny plně kvalifikované.</span><span class="sxs-lookup"><span data-stu-id="68c01-121">References to code entities outside the partial class CLR namespace must all be fully qualified.</span></span> <span data-ttu-id="68c01-122">Pokud jsou deklarovány členy přepsání na částečné třídy přepsat členy, musí být zadán s klíčovým slovem přepsat specifické pro jazyk.</span><span class="sxs-lookup"><span data-stu-id="68c01-122">If members being declared are overrides to the partial class overridable members, this must be specified with the language-specific override keyword.</span></span> <span data-ttu-id="68c01-123">Pokud členové `x:Code` deklarované v oboru konfliktu s členy částečné třídy vytvořené z XAML, takovým způsobem, že kompilátor hlásí konflikt, soubor XAML nelze kompilovat nebo načíst.</span><span class="sxs-lookup"><span data-stu-id="68c01-123">If members declared in `x:Code` scope conflict with members of the partial class created out of the XAML, in such a way that the compiler reports the conflict, the XAML file cannot compile or load.</span></span>

## <a name="see-also"></a><span data-ttu-id="68c01-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="68c01-124">See also</span></span>

- [<span data-ttu-id="68c01-125">x:Class – direktiva</span><span class="sxs-lookup"><span data-stu-id="68c01-125">x:Class Directive</span></span>](xclass-directive.md)
- [<span data-ttu-id="68c01-126">Podkladový kód a kód XAML v subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="68c01-126">Code-Behind and XAML in WPF</span></span>](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [<span data-ttu-id="68c01-127">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="68c01-127">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
