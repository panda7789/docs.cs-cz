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
ms.openlocfilehash: e46d8561b62d9137d4fed4df447338a97fc0577b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938906"
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="d3536-102">x:Null – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="d3536-102">x:Null Markup Extension</span></span>
<span data-ttu-id="d3536-103">Určuje `null` jako hodnotu pro člena XAML.</span><span class="sxs-lookup"><span data-stu-id="d3536-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="d3536-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="d3536-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="d3536-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3536-105">Remarks</span></span>  
 <span data-ttu-id="d3536-106">Klíčové slovo pro odkaz s hodnotou null v C# a [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="d3536-106">The keyword for a null reference in C# and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="d3536-107">Microsoft Visual Basic klíčové slovo pro odkaz s hodnotou null je `Nothing`, ale vždy používají `{x:Null}` jako bez ohledu na to XAML použití modelu code-behind jazyk, který přidružíte k XAML.</span><span class="sxs-lookup"><span data-stu-id="d3536-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="d3536-108">`x:Null` Nemá žádné nastavitelné vlastnosti rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="d3536-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="d3536-109">Null využití je často přidružený vystavení člena XAML CLR <xref:System.Nullable%601> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d3536-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="d3536-110">`x:Null` – Rozšíření značek, stejně jako všechna rozšíření značek XAML, používá složené závorky (`{,}`) pro uvození zpracování hodnoty atributů, aby byla jiná než literály nebo odkazy na obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="d3536-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="d3536-111">Syntaxe atributu je syntaxe nejčastěji používané u tohoto rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="d3536-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="d3536-112">Syntaxi elementu objektu `<x:Null />` je technicky možné, ale je použita jen zřídka, protože `x:Null` – rozšíření značek nemá žádné poziční parametry a argumenty konstrukce.</span><span class="sxs-lookup"><span data-stu-id="d3536-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="d3536-113">Informace o rozšíření značek, naleznete v tématu [– rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="d3536-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="d3536-114">V rozhraní .NET Framework XAML Services zpracování tohoto rozšíření značek definováno <xref:System.Windows.Markup.NullExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="d3536-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="d3536-115">Poznámky k použití WPF</span><span class="sxs-lookup"><span data-stu-id="d3536-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="d3536-116">Všimněte si, že `null` není nutně zrušit nastavení počáteční hodnotu pro vlastnost závislosti typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="d3536-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="d3536-117">Počáteční výchozí hodnota pro každou vlastnost závislostí se může lišit a může být založen na metadata specifická pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d3536-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="d3536-118">Mnoho vlastností závislostí nepřijímají `null` jako hodnotu, buď prostřednictvím značek nebo kódu z důvodu jejich implementace zpětného volání pro ověření.</span><span class="sxs-lookup"><span data-stu-id="d3536-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="d3536-119">Další informace o vlastnosti závislosti, naleznete v tématu [přehled vlastností závislosti](../wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d3536-119">For more information about dependency properties, see [Dependency Properties Overview](../wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3536-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3536-120">See also</span></span>

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [<span data-ttu-id="d3536-121">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="d3536-121">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
- [<span data-ttu-id="d3536-122">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="d3536-122">Markup Extensions and WPF XAML</span></span>](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
