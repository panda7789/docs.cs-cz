---
title: x:Null – rozšíření značek
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 20
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f176598db00c57159bf351ea5d9ec428c5c04bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="xnull-markup-extension"></a><span data-ttu-id="bbac9-102">x:Null – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="bbac9-102">x:Null Markup Extension</span></span>
<span data-ttu-id="bbac9-103">Určuje `null` jako hodnotu pro člena XAML.</span><span class="sxs-lookup"><span data-stu-id="bbac9-103">Specifies `null` as a value for a XAML member.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="bbac9-104">Použití atributu XAML</span><span class="sxs-lookup"><span data-stu-id="bbac9-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a><span data-ttu-id="bbac9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbac9-105">Remarks</span></span>  
 <span data-ttu-id="bbac9-106">Klíčové slovo pro odkaz s hodnotou null v jazyce C# a [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="bbac9-106">The keyword for a null reference in C# and [!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)] is null.</span></span> <span data-ttu-id="bbac9-107">Microsoft Visual Basic – klíčové slovo pro odkaz s hodnotou null je `Nothing`, ale vždy používají `{x:Null}` jako bez ohledu na to XAML využití jazyk kódu, který přidružíte XAML.</span><span class="sxs-lookup"><span data-stu-id="bbac9-107">The Microsoft Visual Basic keyword for a null reference is `Nothing`, but you always use `{x:Null}` as the XAML usage regardless which code-behind language you associate with the XAML.</span></span>  
  
 <span data-ttu-id="bbac9-108">`x:Null` – Rozšíření značek nemá žádné nastavit vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bbac9-108">The `x:Null` markup extension has no settable properties.</span></span>  
  
 <span data-ttu-id="bbac9-109">Použití null je často přidružen expozici člen XAML CLR <xref:System.Nullable%601> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bbac9-109">A null usage is often associated with the XAML member exposure of a CLR <xref:System.Nullable%601> value.</span></span>  
  
 <span data-ttu-id="bbac9-110">`x:Null` – Rozšíření značek, například všechny XAML – rozšíření značek, používá složené závorky (`{,}`) pro zpracování hodnot atributu být jiné než literály nebo obslužná rutina události odkazy uvozovací znaky.</span><span class="sxs-lookup"><span data-stu-id="bbac9-110">The `x:Null` markup extension, like all XAML markup extensions, uses the braces (`{,}`) for escaping the handling of attribute values to be other than literals or event-handler references.</span></span> <span data-ttu-id="bbac9-111">Atribut syntaxe je syntaxe nejčastěji používá u tohoto rozšíření značek.</span><span class="sxs-lookup"><span data-stu-id="bbac9-111">Attribute syntax is the syntax most frequently used with this markup extension.</span></span> <span data-ttu-id="bbac9-112">Syntaxe elementu objektu `<x:Null />` je technicky možné, ale se používá zřídka, protože `x:Null` – rozšíření značek neobsahuje poziční parametry ani argumenty konstrukce.</span><span class="sxs-lookup"><span data-stu-id="bbac9-112">An object element syntax `<x:Null />` is technically possible, but is rarely used because the `x:Null` markup extension has no positional parameters or construction arguments.</span></span>  
  
 <span data-ttu-id="bbac9-113">Informace o rozšíření značek najdete v tématu [rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="bbac9-113">For information about markup extensions, see [Markup Extensions and WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
 <span data-ttu-id="bbac9-114">V rozhraní .NET Framework XAML Services je definované zpracování pro toto rozšíření značek <xref:System.Windows.Markup.NullExtension> třídy.</span><span class="sxs-lookup"><span data-stu-id="bbac9-114">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.NullExtension> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="bbac9-115">Poznámky pro použití WPF</span><span class="sxs-lookup"><span data-stu-id="bbac9-115">WPF Usage Notes</span></span>  
 <span data-ttu-id="bbac9-116">Všimněte si, že `null` není nutně počáteční nenastavenou hodnotu pro vlastnost závislosti typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="bbac9-116">Note that `null` is not necessarily the initial unset value for a reference-type dependency property.</span></span> <span data-ttu-id="bbac9-117">Počáteční výchozí hodnota pro každou vlastnost závislosti se může lišit a může být založené na metadata specifická pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bbac9-117">The initial default value can vary for each dependency property and can be based on property-specific metadata.</span></span> <span data-ttu-id="bbac9-118">Mnoho vlastností závislostí nepřijímají `null` jako hodnotu, buď prostřednictvím kód z důvodu jejich implementace zpětného volání pro ověření.</span><span class="sxs-lookup"><span data-stu-id="bbac9-118">Many dependency properties do not accept `null` as a value, either through markup or code because of their validation callback implementations.</span></span> <span data-ttu-id="bbac9-119">Další informace o vlastnostech závislostí v tématu [přehled vlastností závislostí](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bbac9-119">For more information about dependency properties, see [Dependency Properties Overview](../../../docs/framework/wpf/advanced/dependency-properties-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbac9-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbac9-120">See Also</span></span>  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [<span data-ttu-id="bbac9-121">Přehled XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="bbac9-121">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="bbac9-122">Rozšíření značek a WPF XAML</span><span class="sxs-lookup"><span data-stu-id="bbac9-122">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
