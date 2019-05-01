---
title: 'Postupy: Používání klíčů systémových parametrů'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: 147f65b4bb214c12317309081c345251d7426cd6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001439"
---
# <a name="how-to-use-system-parameters-keys"></a><span data-ttu-id="1c4ea-102">Postupy: Používání klíčů systémových parametrů</span><span class="sxs-lookup"><span data-stu-id="1c4ea-102">How to: Use System Parameters Keys</span></span>
<span data-ttu-id="1c4ea-103">Systémové prostředky vystavit řadu systémových metrik jako prostředky, které usnadní vývojářům vytvářet vizuály, které jsou konzistentní s nastavení systému.</span><span class="sxs-lookup"><span data-stu-id="1c4ea-103">System resources expose a number of system metrics as resources to help developers create visuals that are consistent with system settings.</span></span> <span data-ttu-id="1c4ea-104"><xref:System.Windows.SystemParameters> je třída, která obsahuje hodnoty parametrů systému a klíče prostředku, kteří jsou navázáni na hodnoty – například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> a <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c4ea-104"><xref:System.Windows.SystemParameters> is a class that contains both system parameter values and resource keys that bind to the values—for example, <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> and <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>.</span></span> <span data-ttu-id="1c4ea-105">Metriky parametr systému může sloužit jako statickou nebo dynamickou prostředky.</span><span class="sxs-lookup"><span data-stu-id="1c4ea-105">System parameter metrics can be used as either static or dynamic resources.</span></span> <span data-ttu-id="1c4ea-106">Použijte dynamický prostředek, pokud chcete, aby parametr metrika automaticky aktualizovat při aplikaci spustí; Jinak použijte statických prostředků.</span><span class="sxs-lookup"><span data-stu-id="1c4ea-106">Use a dynamic resource if you want the parameter metric to update automatically while the application runs; otherwise use a static resource.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c4ea-107">Dynamické prostředky mají klíčové slovo *klíč* připojeným k názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1c4ea-107">Dynamic resources have the keyword *Key* appended to the property name.</span></span>  
  
 <span data-ttu-id="1c4ea-108">Následující příklad ukazuje, jak přistupovat k prostředkům a používat systém parametr dynamické stylu nebo tlačítko Přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="1c4ea-108">The following example shows how to access and use system parameter dynamic resources to style or customize a button.</span></span> <span data-ttu-id="1c4ea-109">To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad velikosti tlačítko, přiřazením <xref:System.Windows.SystemParameters> hodnoty pro šířku a výšku na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="1c4ea-109">This [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example sizes a button by assigning <xref:System.Windows.SystemParameters> values to the button's width and height.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c4ea-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c4ea-110">Example</span></span>  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a><span data-ttu-id="1c4ea-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c4ea-111">See also</span></span>

- [<span data-ttu-id="1c4ea-112">Vykreslení oblasti systémovým štětcem</span><span class="sxs-lookup"><span data-stu-id="1c4ea-112">Paint an Area with a System Brush</span></span>](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [<span data-ttu-id="1c4ea-113">Používání třídy SystemFonts</span><span class="sxs-lookup"><span data-stu-id="1c4ea-113">Use SystemFonts</span></span>](how-to-use-systemfonts.md)
- [<span data-ttu-id="1c4ea-114">Používání třídy SystemParameters</span><span class="sxs-lookup"><span data-stu-id="1c4ea-114">Use SystemParameters</span></span>](how-to-use-systemparameters.md)
