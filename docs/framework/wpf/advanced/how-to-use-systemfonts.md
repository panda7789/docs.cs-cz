---
title: 'Postupy: Používání třídy SystemFonts'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
ms.openlocfilehash: 5976bc0cb8b34e68d5e89dd70a608d7e52ded332
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216779"
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="c36a4-102">Postupy: Používání třídy SystemFonts</span><span class="sxs-lookup"><span data-stu-id="c36a4-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="c36a4-103">Tento příklad ukazuje způsob použití statické prostředky <xref:System.Windows.SystemFonts> třídy za účelem stylu nebo tlačítko Přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="c36a4-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c36a4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c36a4-104">Example</span></span>  
 <span data-ttu-id="c36a4-105">Systémové prostředky vystavit několik systému určit hodnoty vlastnosti a prostředky k vám pomůžou vytvořit vizuály, které jsou konzistentní s nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="c36a4-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="c36a4-106"><xref:System.Windows.SystemFonts> je třída, která obsahuje obě hodnoty písma systému jako statické vlastnosti a vlastnosti, které odkazují na klíče prostředku, které lze použít pro přístup k těmto hodnoty dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="c36a4-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="c36a4-107">Například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> je <xref:System.Windows.SystemFonts> hodnotu, a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> je odpovídající klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="c36a4-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="c36a4-108">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít jako objekty její členové <xref:System.Windows.SystemFonts> jako statické vlastnosti nebo odkazy na dynamický prostředek (s hodnotou statickou vlastnost jako klíč).</span><span class="sxs-lookup"><span data-stu-id="c36a4-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="c36a4-109">Použít odkaz dynamický prostředek, pokud chcete písmo metrika se automaticky aktualizovat při aplikaci spustí; Jinak použijte odkaz na statické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c36a4-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c36a4-110">Klíče prostředku mají příponu "Klíče" připojen název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c36a4-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="c36a4-111">Následující příklad ukazuje, jak přistupovat a používat vlastnosti <xref:System.Windows.SystemFonts> jako statické hodnoty pro styl nebo tlačítko Přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="c36a4-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="c36a4-112">Tento příklad kódu přiřazuje <xref:System.Windows.SystemFonts> hodnoty k tlačítku.</span><span class="sxs-lookup"><span data-stu-id="c36a4-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="c36a4-113">Chcete-li použít hodnoty <xref:System.Windows.SystemFonts> v kódu, není nutné používat statickou hodnotou nebo odkazem dynamický prostředek.</span><span class="sxs-lookup"><span data-stu-id="c36a4-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="c36a4-114">Místo toho použijte vlastnosti neklíčovým <xref:System.Windows.SystemFonts> třídy.</span><span class="sxs-lookup"><span data-stu-id="c36a4-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="c36a4-115">I když neklíčovým vlastnosti jsou zdánlivě definovány jako statické vlastnosti, chování za běhu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostitelem systému přehodnotí vlastnosti v reálném čase a se správně řízené uživatelské změny hodnot systémového účtu.</span><span class="sxs-lookup"><span data-stu-id="c36a4-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="c36a4-116">Následující příklad ukazuje, jak určuje nastavení písma tlačítka.</span><span class="sxs-lookup"><span data-stu-id="c36a4-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="c36a4-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c36a4-117">See also</span></span>

- <xref:System.Windows.SystemFonts>
- [<span data-ttu-id="c36a4-118">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="c36a4-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="c36a4-119">Používání třídy SystemParameters</span><span class="sxs-lookup"><span data-stu-id="c36a4-119">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
- [<span data-ttu-id="c36a4-120">Použití klíčů systémových písem</span><span class="sxs-lookup"><span data-stu-id="c36a4-120">Use System Fonts Keys</span></span>](how-to-use-system-fonts-keys.md)
- [<span data-ttu-id="c36a4-121">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="c36a4-121">How-to Topics</span></span>](resources-how-to-topics.md)
- [<span data-ttu-id="c36a4-122">x:Static – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="c36a4-122">x:Static Markup Extension</span></span>](../../xaml-services/x-static-markup-extension.md)
- [<span data-ttu-id="c36a4-123">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="c36a4-123">XAML Resources</span></span>](xaml-resources.md)
- [<span data-ttu-id="c36a4-124">Rozšíření značek DynamicResource</span><span class="sxs-lookup"><span data-stu-id="c36a4-124">DynamicResource Markup Extension</span></span>](dynamicresource-markup-extension.md)
