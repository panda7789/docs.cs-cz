---
title: 'Postupy: Použití klíčů systémových parametrů'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
ms.openlocfilehash: a71551c5d539d7009fb9a052c81928a009fc4c35
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357193"
---
# <a name="how-to-use-system-parameters-keys"></a>Postupy: Použití klíčů systémových parametrů
Systémové prostředky vystavit řadu systémových metrik jako prostředky, které usnadní vývojářům vytvářet vizuály, které jsou konzistentní s nastavení systému. <xref:System.Windows.SystemParameters> je třída, která obsahuje hodnoty parametrů systému a klíče prostředku, kteří jsou navázáni na hodnoty – například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> a <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Metriky parametr systému může sloužit jako statickou nebo dynamickou prostředky. Použijte dynamický prostředek, pokud chcete, aby parametr metrika automaticky aktualizovat při aplikaci spustí; Jinak použijte statických prostředků.  
  
> [!NOTE]
>  Dynamické prostředky mají klíčové slovo *klíč* připojeným k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak přistupovat k prostředkům a používat systém parametr dynamické stylu nebo tlačítko Přizpůsobit. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad velikosti tlačítko, přiřazením <xref:System.Windows.SystemParameters> hodnoty pro šířku a výšku na tlačítko.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](~/samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Viz také:
- [Vykreslení oblasti systémovým štětcem](../graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Používání třídy SystemFonts](how-to-use-systemfonts.md)
- [Používání třídy SystemParameters](how-to-use-systemparameters.md)
