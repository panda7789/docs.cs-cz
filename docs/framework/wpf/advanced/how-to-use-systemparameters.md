---
title: 'Postupy: Používání třídy SystemParameters'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 344fb54b48bcbf188b36a29d8205c21deff713c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199853"
---
# <a name="how-to-use-systemparameters"></a><span data-ttu-id="a80b7-102">Postupy: Používání třídy SystemParameters</span><span class="sxs-lookup"><span data-stu-id="a80b7-102">How to: Use SystemParameters</span></span>
<span data-ttu-id="a80b7-103">Tento příklad ukazuje, jak přistupovat a používat vlastnosti <xref:System.Windows.SystemParameters> za účelem stylu nebo tlačítko Přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="a80b7-103">This example shows how to access and use the properties of <xref:System.Windows.SystemParameters> in order to style or customize a button.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a80b7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a80b7-104">Example</span></span>  
 <span data-ttu-id="a80b7-105">Systémové prostředky vystavit několik nastavení systémem prostředky prostředky vám pomůžou vytvořit vizuály, které jsou konzistentní s nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="a80b7-105">System resources expose several system based settings as resources in order to help you create visuals that are consistent with system settings.</span></span> <xref:System.Windows.SystemParameters> <span data-ttu-id="a80b7-106">je třída, která obsahuje vlastnosti hodnotu parametru systému a klíče prostředku, kteří jsou navázáni na hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a80b7-106">is a class that contains both system parameter value properties, and resource keys that bind to the values.</span></span> <span data-ttu-id="a80b7-107">Například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> je <xref:System.Windows.SystemParameters> hodnotu vlastnosti a <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> je odpovídající klíč prostředku.</span><span class="sxs-lookup"><span data-stu-id="a80b7-107">For example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> is a <xref:System.Windows.SystemParameters> property value and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A> is the corresponding resource key.</span></span>  
  
 <span data-ttu-id="a80b7-108">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], můžete použít jako objekty její členové <xref:System.Windows.SystemParameters> jako statická vlastnost využití nebo odkazy dynamický prostředek (s hodnotou statickou vlastnost jako klíč).</span><span class="sxs-lookup"><span data-stu-id="a80b7-108">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can use the members of <xref:System.Windows.SystemParameters> as either a static property usage, or a dynamic resource references (with the static property value as the key).</span></span> <span data-ttu-id="a80b7-109">Použít odkaz dynamický prostředek, pokud chcete, aby hodnota systémem automaticky aktualizovat při aplikaci spustí; Jinak použijte statický odkaz.</span><span class="sxs-lookup"><span data-stu-id="a80b7-109">Use a dynamic resource reference if you want the system based value to update automatically while the application runs; otherwise, use a static reference.</span></span> <span data-ttu-id="a80b7-110">Klíče prostředku mají příponu `Key` připojeným k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a80b7-110">Resource keys have the suffix `Key` appended to the property name.</span></span>  
  
 <span data-ttu-id="a80b7-111">Následující příklad ukazuje, jak přistupovat a používat statické hodnoty <xref:System.Windows.SystemParameters> stylu nebo tlačítko Přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="a80b7-111">The following example shows how to access and use the static values of <xref:System.Windows.SystemParameters> to style or customize a button.</span></span> <span data-ttu-id="a80b7-112">Tento příklad kódu s použitím velikosti tlačítko <xref:System.Windows.SystemParameters> hodnoty k tlačítku.</span><span class="sxs-lookup"><span data-stu-id="a80b7-112">This markup example sizes a button by applying <xref:System.Windows.SystemParameters> values to a button.</span></span>  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 <span data-ttu-id="a80b7-113">Chcete-li použít hodnoty <xref:System.Windows.SystemParameters> v kódu, není nutné používat buď statické odkazy nebo dynamický prostředek.</span><span class="sxs-lookup"><span data-stu-id="a80b7-113">To use the values of <xref:System.Windows.SystemParameters> in code, you do not have to use either static references or dynamic resource references.</span></span> <span data-ttu-id="a80b7-114">Místo toho použijte hodnoty <xref:System.Windows.SystemParameters> třídy.</span><span class="sxs-lookup"><span data-stu-id="a80b7-114">Instead, use the values of the <xref:System.Windows.SystemParameters> class.</span></span> <span data-ttu-id="a80b7-115">I když neklíčovým vlastnosti jsou zdánlivě definovány jako statické vlastnosti, modul runtime chování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako hostované v systému se opětovné vyhodnocení vlastnosti v reálném čase a se správně řízené uživatelské změny hodnot systémového účtu.</span><span class="sxs-lookup"><span data-stu-id="a80b7-115">Although the non-key properties are apparently defined as static properties, the runtime behavior of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] as hosted by the system will reevaluate the properties in realtime, and will properly account for user-driven changes to system values.</span></span> <span data-ttu-id="a80b7-116">Následující příklad ukazuje, jak nastavit šířku a výšku tlačítka pomocí <xref:System.Windows.SystemParameters> hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a80b7-116">The following example shows how to set the width and height of a button by using <xref:System.Windows.SystemParameters> values.</span></span>  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a><span data-ttu-id="a80b7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a80b7-117">See also</span></span>

- <xref:System.Windows.SystemParameters>
- [<span data-ttu-id="a80b7-118">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="a80b7-118">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="a80b7-119">Používání třídy SystemFonts</span><span class="sxs-lookup"><span data-stu-id="a80b7-119">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="a80b7-120">Používání klíčů systémových parametrů</span><span class="sxs-lookup"><span data-stu-id="a80b7-120">Use System Parameters Keys</span></span>](how-to-use-system-parameters-keys.md)
- [<span data-ttu-id="a80b7-121">– postupy</span><span class="sxs-lookup"><span data-stu-id="a80b7-121">How-to Topics</span></span>](resources-how-to-topics.md)
