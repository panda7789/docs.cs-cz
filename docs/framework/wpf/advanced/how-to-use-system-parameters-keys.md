---
title: "Postupy: Použití klíčů systémových parametrů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b5f45f386c58b0577a2716c6fe1396f4c44f4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-parameters-keys"></a>Postupy: Použití klíčů systémových parametrů
Systémové prostředky vystavit počet metriky systému jako prostředky, což vývojářům vytvářet vizuální prvky, které jsou v souladu s nastavení systému. <xref:System.Windows.SystemParameters>je třída, která obsahuje hodnoty parametrů systému a klíče prostředků, které vytvořit vazbu na hodnoty – například <xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A> a <xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>. Metriky parametr systému lze použít jako statickou nebo dynamickou prostředky. Pokud má parametr metrika aktualizovat automaticky při aplikaci použít dynamického prostředku spouští; Jinak použijte statické prostředků.  
  
> [!NOTE]
>  Dynamické prostředky mít klíčové slovo *klíč* připojeným k názvu vlastnosti.  
  
 Následující příklad ukazuje, jak získat přístup k prostředkům a používat systému parametr dynamické styl nebo na tlačítko Upravit. To [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad velikosti tlačítko přiřazením <xref:System.Windows.SystemParameters> hodnoty šířky a výšky na tlačítko.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>Viz také  
 [Malovat oblast štětcem systému](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [Použití SystemFonts](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [Použití SystemParameters](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
