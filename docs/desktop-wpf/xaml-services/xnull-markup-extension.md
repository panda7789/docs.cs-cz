---
title: x:Null – rozšíření značek
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071428"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="ed675-102">x:Null – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="ed675-102">x:Null Markup Extension</span></span>

<span data-ttu-id="ed675-103">Určuje `null` jako hodnotu pro člena XAML.</span><span class="sxs-lookup"><span data-stu-id="ed675-103">Specifies `null` as a value for a XAML member.</span></span>

## <a name="xaml-attribute-usage"></a><span data-ttu-id="ed675-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="ed675-104">XAML Attribute Usage</span></span>

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a><span data-ttu-id="ed675-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed675-105">Remarks</span></span>

<span data-ttu-id="ed675-106">Klíčové slovo pro odkaz null v jazyce C# a C++ je null.</span><span class="sxs-lookup"><span data-stu-id="ed675-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="ed675-107">Klíčové slovo jazyka Microsoft Visual `Nothing`Basic pro nulový odkaz je , ale vždy používáte `{x:Null}` jako použití XAML bez ohledu na to, který jazyk za kódem přidružíte k XAML.</span><span class="sxs-lookup"><span data-stu-id="ed675-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>

<span data-ttu-id="ed675-108">Rozšíření `x:Null` značek nemá žádné vlastnosti, které by bylo možné nastavit.</span><span class="sxs-lookup"><span data-stu-id="ed675-108">The `x:Null` markup extension has no settable properties.</span></span>

<span data-ttu-id="ed675-109">Použití null je často spojena s expozicí člena <xref:System.Nullable%601> XAML clr hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ed675-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>

<span data-ttu-id="ed675-110">Rozšíření `x:Null` značek, stejně jako všechna rozšíření značek XAML,`{,}`používá závorky ( ) pro únik zpracování hodnot atributů, které mají být jiné než literály nebo odkazy na obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="ed675-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="ed675-111">Syntaxe atributu je syntaxe nejčastěji používaná s tímto rozšířením značek.</span><span class="sxs-lookup"><span data-stu-id="ed675-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="ed675-112">Syntaxe `<x:Null />` prvku objektu je technicky možná, `x:Null` ale zřídka se používá, protože rozšíření značek nemá žádné poziční parametry nebo argumenty konstrukce.</span><span class="sxs-lookup"><span data-stu-id="ed675-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>

<span data-ttu-id="ed675-113">Informace o rozšířeních značek naleznete v [tématech Rozšíření značek a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="ed675-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>

<span data-ttu-id="ed675-114">Ve službě .NET XAML Services je zpracování pro <xref:System.Windows.Markup.NullExtension> toto rozšíření značek definováno třídou.</span><span class="sxs-lookup"><span data-stu-id="ed675-114">In .NET XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>

## <a name="wpf-usage-notes"></a><span data-ttu-id="ed675-115">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="ed675-115">WPF Usage Notes</span></span>

<span data-ttu-id="ed675-116">Všimněte `null` si, že není nutně počáteční unset hodnotu pro vlastnost závislost typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="ed675-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="ed675-117">Počáteční výchozí hodnota se může lišit pro každou vlastnost závislosti a může být založena na metadatech specifických pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ed675-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="ed675-118">Mnoho vlastností závislostí `null` nepřijímá jako hodnotu, a to buď prostřednictvím značek nebo kódu z důvodu jejich implementace zpětného volání ověření.</span><span class="sxs-lookup"><span data-stu-id="ed675-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="ed675-119">Další informace o vlastnostech závislostí naleznete v [tématu Přehled vlastností závislostí](../../framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ed675-119">For more information about dependency properties, see [Dependency Properties Overview](../../framework/wpf/advanced/dependency-properties-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed675-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed675-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="ed675-121">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="ed675-121">XAML Overview (WPF)</span></span>](../fundamentals/xaml.md)
- [<span data-ttu-id="ed675-122">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="ed675-122">Markup Extensions and WPF XAML</span></span>](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
