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
ms.openlocfilehash: 7dbea2c7d4010d8defc572dbdc14a0dfd6d7601e
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484712"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="957bc-102">x:Null – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="957bc-102">x:Null Markup Extension</span></span>
<span data-ttu-id="957bc-103">Určuje `null` hodnotu člena XAML.</span><span class="sxs-lookup"><span data-stu-id="957bc-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="957bc-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="957bc-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="957bc-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="957bc-105">Remarks</span></span>  
 <span data-ttu-id="957bc-106">Klíčové slovo pro odkaz s hodnotou null C# v C++ a má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="957bc-106">The keyword for a null reference in C# and C++ is null.</span></span> <span data-ttu-id="957bc-107">Klíčové slovo Microsoft Visual Basic pro odkaz s hodnotou null `Nothing`je, ale vždy používáte `{x:Null}` jako použití XAML bez ohledu na to, který kód na pozadí přidružujete k XAML.</span><span class="sxs-lookup"><span data-stu-id="957bc-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="957bc-108">Rozšíření `x:Null` značek nemá žádné nastavitelné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="957bc-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="957bc-109">Použití hodnoty null je často přidruženo k expozici členů XAML hodnoty CLR <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="957bc-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="957bc-110">Rozšíření značek, jako jsou všechna rozšíření značek XAML, používá složené závorky (`{,}`) pro uvozovací manipulaci s hodnotami atributů jiné než literály nebo odkazy obslužných rutin událostí. `x:Null`</span><span class="sxs-lookup"><span data-stu-id="957bc-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="957bc-111">Syntaxe atributu je syntaxe, která se nejčastěji používá s touto příponou označení.</span><span class="sxs-lookup"><span data-stu-id="957bc-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="957bc-112">Syntaxe `<x:Null />` elementu objektu je technicky možná, ale používá se zřídka, `x:Null` protože rozšíření značek nemá žádné poziční parametry nebo argumenty konstrukce.</span><span class="sxs-lookup"><span data-stu-id="957bc-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="957bc-113">Informace o rozšíření značek naleznete v tématu [rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="957bc-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="957bc-114">V .NET Framework služby XAML je zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.NullExtension> třídou.</span><span class="sxs-lookup"><span data-stu-id="957bc-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="957bc-115">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="957bc-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="957bc-116">Všimněte si `null` , že není nutně počáteční hodnota nenastavené vlastnosti závislostí typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="957bc-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="957bc-117">Počáteční výchozí hodnota se může u každé vlastnosti závislosti lišit a může být založena na metadatech specifických pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="957bc-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="957bc-118">Mnoho vlastností závislosti nepřijímá `null` jako hodnotu, a to buď prostřednictvím kódu, nebo kódu z důvodu implementace zpětného volání ověřování.</span><span class="sxs-lookup"><span data-stu-id="957bc-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="957bc-119">Další informace o vlastnostech závislosti najdete v tématu [Přehled vlastností závislosti](../wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="957bc-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="957bc-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="957bc-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="957bc-121">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="957bc-121">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="957bc-122">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="957bc-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
