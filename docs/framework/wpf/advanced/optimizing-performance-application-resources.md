---
title: 'Optimalizace výkonu: Zdroje aplikace'
ms.date: 03/30/2017
helpviewer_keywords:
- application resources [WPF], performance
- resources [WPF], performance
- static resources [WPF]
- sharing resources [WPF]
- brushes [WPF], performance
- sharing brushes without copying [WPF]
ms.assetid: 62b88488-c08e-4804-b7de-a1c34fbe929c
ms.openlocfilehash: 921a67a24464ff5ac782045ae022f7766f32d579
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352396"
---
# <a name="optimizing-performance-application-resources"></a>Optimalizace výkonu: Zdroje aplikace
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje sdílení prostředků aplikace tak, aby mezi elementy podobné typy může podporovat konzistentního vzhledu a chování. Toto téma obsahuje několik doporučení v této oblasti, které vám můžou pomoci zvýšit výkon vašich aplikací.  
  
 Další informace o prostředcích naleznete v tématu [prostředky XAML](xaml-resources.md).  
  
## <a name="sharing-resources"></a>Sdílení prostředků  
 Pokud vaše aplikace používá vlastní ovládací prvky a definuje prostředky v <xref:System.Windows.ResourceDictionary> (nebo prostředky XAML uzel), doporučuje se, že buď definujete prostředky na <xref:System.Windows.Application> nebo <xref:System.Windows.Window> objekt úroveň nebo definovat výchozí motivu pro vlastní ovládací prvky. Definování prostředků v vlastního ovládacího prvku <xref:System.Windows.ResourceDictionary> má dopad na výkon pro každou instanci tohoto ovládacího prvku. Například pokud máte operace náročné na výkon štětce definované jako součást definice prostředků vlastního ovládacího prvku a velký počet instancí vlastního ovládacího prvku, pracovní sada aplikace se výrazně zvýšit.  
  
 Pro ilustraci tohoto bodu, zvažte následující skutečnosti. Řekněme, že vyvíjíte a karty hry s použitím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pro většinu karetní hry je třeba 52 karet s 52 různých tváří. Rozhodnout k implementaci vlastního ovládacího prvku karty a definovat 52 štětce (nichž každý představuje karty lícem) v prostředcích vlastního ovládacího prvku karty. V hlavní aplikaci vytvoříte nejdřív 52 instance tohoto vlastního ovládacího prvku karty. Každá instance vlastního ovládacího prvku karta generuje 52 instance <xref:System.Windows.Media.Brush> objekty, které poskytuje celkový počet 52 * 52 <xref:System.Windows.Media.Brush> objekty ve vaší aplikaci. Přesunutím štětce nemá dostatek prostředků vlastní ovládací prvek karty na <xref:System.Windows.Application> nebo <xref:System.Windows.Window> úrovni objektu nebo definování výchozí motivu pro vlastní ovládací prvek, snížíte pracovní sady aplikací, protože jsou nyní sdílení 52 štětců mezi 52 instance ovládacího prvku karty.  
  
## <a name="sharing-a-brush-without-copying"></a>Sdílení štětce bez kopírování  
 Pokud máte více elementů se stejnou <xref:System.Windows.Media.Brush> objektu, definice štětec jako prostředek a odkaz, spíše definice vloženě štětce v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]. Tato metoda vytvoří jednu instanci a znovu použít to, že definice vloženě štětce v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] vytvoří novou instanci pro každý prvek.  
  
 Následující ukázkový kód to znázorňuje:  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Použití statické prostředky, pokud je to možné  
 Statický prostředek poskytuje hodnotu pro všechny atributy vlastnosti XAML vyhledáním odkaz na prostředek už definované. Chování při vyhledávání pro daný prostředek je obdobou vyhledávání za kompilace.  
  
 Dynamický prostředek na druhé straně vytvoří dočasné výraz během počáteční kompilace a vyhledávání prostředků tedy odložit, dokud hodnota požadovaný prostředek je skutečně potřeba, abyste mohli vytvořit objekt. Chování při vyhledávání pro daný prostředek je obdobou vyhledávání za běhu, což má dopad na výkon. Použití statické prostředky, kdykoli je to možné ve vaší aplikaci pomocí dynamické prostředky pouze v případě potřeby.  
  
 Následující příklad kódu ukazuje použití obou typů prostředků:  
  
 [!code-xaml[Performance#PerformanceSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Viz také:
- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
