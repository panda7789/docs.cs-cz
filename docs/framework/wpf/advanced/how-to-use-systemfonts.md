---
title: "Postupy: Používání tipů SystemFonts"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- system fonts [WPF]
- fonts [WPF], system fonts
- classes [WPF], SystemFonts
ms.assetid: 3f46a4ec-2225-408a-8123-8838a8f7057a
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2579926dfc71028590e09993e2773ee2cfac1505
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-systemfonts"></a><span data-ttu-id="17bc8-102">Postupy: Používání tipů SystemFonts</span><span class="sxs-lookup"><span data-stu-id="17bc8-102">How to: Use SystemFonts</span></span>
<span data-ttu-id="17bc8-103">Tento příklad ukazuje, jak používat statické prostředky <xref:System.Windows.SystemFonts> třídy za účelem styl nebo na tlačítko Přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="17bc8-103">This example shows how to use the static resources of the <xref:System.Windows.SystemFonts> class in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17bc8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="17bc8-104">Example</span></span>  
 <span data-ttu-id="17bc8-105">Systémové prostředky vystavit několik systému určit hodnoty vlastnosti a prostředky k vám pomůže vytvořit vizuální prvky, které jsou v souladu s nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="17bc8-105">System resources expose several system-determined values as both resources and properties in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="17bc8-106"><xref:System.Windows.SystemFonts>je třída, která obsahuje obě hodnoty písma systému jako statické vlastnosti a vlastnosti, které odkazují na klíče prostředků, které lze použít pro přístup k tyto hodnoty dynamicky za běhu.</span><span class="sxs-lookup"><span data-stu-id="17bc8-106"><xref:System.Windows.SystemFonts> is a class that contains both system font values as static properties, and properties that reference resource keys that can be used to access those values dynamically at run time.</span></span> <span data-ttu-id="17bc8-107">Například <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> je <xref:System.Windows.SystemFonts> hodnotu, a <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> je odpovídající klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="17bc8-107">For example, <xref:System.Windows.SystemFonts.CaptionFontFamily%2A> is a <xref:System.Windows.SystemFonts> value, and <xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A> is a corresponding resource key.</span></span>  
  
 <span data-ttu-id="17bc8-108">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít členy <xref:System.Windows.SystemFonts> jako statické vlastnosti nebo dynamické prostředků odkazy (s hodnotou statickou vlastnost jako klíč).</span><span class="sxs-lookup"><span data-stu-id="17bc8-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemFonts> as either static properties or dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="17bc8-109">Použít odkaz na dynamické prostředků metriky písma automaticky aktualizovat při aplikace běží; Jinak použijte odkaz na statické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="17bc8-109">Use a dynamic resource reference if you want the font metric to automatically update while the application runs; otherwise, use a static value reference.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17bc8-110">Klíče prostředků mít příponu, které "Klíč" připojeným k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="17bc8-110">The resource keys have the suffix "Key" appended to the property name.</span></span>  
  
 <span data-ttu-id="17bc8-111">Následující příklad ukazuje, jak k přístupu a použití vlastností <xref:System.Windows.SystemFonts> jako statické hodnoty, aby bylo možné styl nebo tlačítko nastavit.</span><span class="sxs-lookup"><span data-stu-id="17bc8-111">The following example shows how to access and use the properties of <xref:System.Windows.SystemFonts> as static values in order to style or customize a button.</span></span> <span data-ttu-id="17bc8-112">Tento příklad kódu přiřadí <xref:System.Windows.SystemFonts> hodnoty pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="17bc8-112">This markup example assigns <xref:System.Windows.SystemFonts> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#FontStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#fontstaticresources)]  
  
 <span data-ttu-id="17bc8-113">Chcete-li použít hodnoty <xref:System.Windows.SystemFonts> v kódu nemáte používat statickou hodnotu nebo odkaz na dynamické prostředků.</span><span class="sxs-lookup"><span data-stu-id="17bc8-113">To use the values of <xref:System.Windows.SystemFonts> in code, you do not have to use either a static value or a dynamic resource reference.</span></span> <span data-ttu-id="17bc8-114">Místo toho použijte vlastnosti neklíčový <xref:System.Windows.SystemFonts> třídy.</span><span class="sxs-lookup"><span data-stu-id="17bc8-114">Instead, use the non-key properties of the <xref:System.Windows.SystemFonts> class.</span></span> <span data-ttu-id="17bc8-115">I když neklíčovými vlastnostmi zjevně jsou definovány jako statické vlastnosti, chování běhové [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostované systému přehodnotí vlastnosti v reálném čase a bude správně řízené uživatele změny hodnot systémového účtu.</span><span class="sxs-lookup"><span data-stu-id="17bc8-115">Although the non-key properties are apparently defined as static properties, the run-time behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in real time and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="17bc8-116">Následující příklad ukazuje, jak nastavení písma tlačítka.</span><span class="sxs-lookup"><span data-stu-id="17bc8-116">The following example shows how to specify the font settings of a button.</span></span>  
  
 [!code-csharp[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#fontresourcescode)]
 [!code-vb[SystemRes_snip#FontResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#fontresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="17bc8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="17bc8-117">See Also</span></span>  
 <xref:System.Windows.SystemFonts>  
 [<span data-ttu-id="17bc8-118">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="17bc8-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="17bc8-119">Používání třídy SystemParameters</span><span class="sxs-lookup"><span data-stu-id="17bc8-119">Use SystemParameters</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [<span data-ttu-id="17bc8-120">Použití klíčů systémových písem</span><span class="sxs-lookup"><span data-stu-id="17bc8-120">Use System Fonts Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-fonts-keys.md)  
 [<span data-ttu-id="17bc8-121">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="17bc8-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)  
 [<span data-ttu-id="17bc8-122">x:Static – rozšíření značek</span><span class="sxs-lookup"><span data-stu-id="17bc8-122">x:Static Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-static-markup-extension.md)  
 [<span data-ttu-id="17bc8-123">Prostředky XAML</span><span class="sxs-lookup"><span data-stu-id="17bc8-123">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="17bc8-124">Rozšíření značek DynamicResource</span><span class="sxs-lookup"><span data-stu-id="17bc8-124">DynamicResource Markup Extension</span></span>](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)
