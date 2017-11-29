---
title: "Postupy: Používání tipů SystemParameters"
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
helpviewer_keywords: classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4b2ee3956017e10da8adda52fa9a0ec31cb19ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="661c5-102">Postupy: Používání tipů SystemParameters</span><span class="sxs-lookup"><span data-stu-id="661c5-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="661c5-103">Tento příklad ukazuje, jak k přístupu a použití vlastností <xref:System.Windows.SystemParameters> za účelem styl nebo na tlačítko Přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="661c5-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="661c5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="661c5-104">Example</span></span>  
 <span data-ttu-id="661c5-105">Systémové prostředky vystavit několik nastavení systému, na základě prostředků, aby vám pomůže vytvořit vizuální prvky, které jsou konzistentní s nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="661c5-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <span data-ttu-id="661c5-106"><xref:System.Windows.SystemParameters>je třída, která obsahuje vlastnosti hodnotu parametru systému a klíče prostředků, které vytvořit vazbu na hodnoty.</span><span class="sxs-lookup"><span data-stu-id="661c5-106"><xref:System.Windows.SystemParameters> is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="661c5-107">Například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> je <xref:System.Windows.SystemParameters> hodnotu vlastnosti a <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> je odpovídající klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="661c5-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="661c5-108">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít členy <xref:System.Windows.SystemParameters> jako použití statickou vlastnost nebo dynamické prostředků odkazy (s hodnotou statickou vlastnost jako klíč).</span><span class="sxs-lookup"><span data-stu-id="661c5-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="661c5-109">Pokud má hodnotu systém založený na Aktualizovat automaticky při aplikaci použít odkaz na dynamické prostředků spouští; Jinak použijte statický odkaz.</span><span class="sxs-lookup"><span data-stu-id="661c5-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="661c5-110">Prostředek klíče měly přípona `Key` připojeným k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="661c5-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="661c5-111">Následující příklad ukazuje, jak k přístupu a použití statické hodnoty <xref:System.Windows.SystemParameters> styl nebo na tlačítko Upravit.</span><span class="sxs-lookup"><span data-stu-id="661c5-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="661c5-112">Tento příklad kódu velikostí tlačítka s použitím <xref:System.Windows.SystemParameters> hodnoty pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="661c5-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="661c5-113">Chcete-li použít hodnoty <xref:System.Windows.SystemParameters> v kódu nemáte použít buď odkazy statické nebo dynamické prostředků.</span><span class="sxs-lookup"><span data-stu-id="661c5-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="661c5-114">Místo toho použijte hodnoty <xref:System.Windows.SystemParameters> třídy.</span><span class="sxs-lookup"><span data-stu-id="661c5-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="661c5-115">I když neklíčovými vlastnostmi zjevně jsou definovány jako statické vlastnosti, modul runtime chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostované v systému bude přehodnocovat vlastnosti v reálném čase, a bude správně řízené uživatele změny hodnot systémového účtu.</span><span class="sxs-lookup"><span data-stu-id="661c5-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="661c5-116">Následující příklad ukazuje, jak nastavit šířku a výšku tlačítka s pomocí <xref:System.Windows.SystemParameters> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="661c5-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="661c5-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="661c5-117">See Also</span></span>  
 <xref:System.Windows.SystemParameters>  
 [<span data-ttu-id="661c5-118">Malovat oblast štětcem systému</span><span class="sxs-lookup"><span data-stu-id="661c5-118">Paint an Area with a System Brush</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [<span data-ttu-id="661c5-119">Použití SystemFonts</span><span class="sxs-lookup"><span data-stu-id="661c5-119">Use SystemFonts</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [<span data-ttu-id="661c5-120">Používejte klíče parametry systému</span><span class="sxs-lookup"><span data-stu-id="661c5-120">Use System Parameters Keys</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [<span data-ttu-id="661c5-121">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="661c5-121">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
