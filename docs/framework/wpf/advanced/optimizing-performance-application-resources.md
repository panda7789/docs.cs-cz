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
ms.openlocfilehash: 53e906f31f32fb0f1df3f8d986daa0ae95ea9e4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546592"
---
# <a name="optimizing-performance-application-resources"></a>Optimalizace výkonu: Zdroje aplikace
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umožňuje sdílet prostředky aplikace, takže může podporovat konzistentní vzhled a chování napříč podobné typované elementy. Toto téma obsahuje několik doporučení v této oblasti, která vám může pomoct zlepšit výkon aplikací.  
  
 Další informace o prostředcích, najdete v části [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
## <a name="sharing-resources"></a>Sdílení prostředků  
 Pokud vaše aplikace používá vlastní ovládací prvky a definuje prostředky v <xref:System.Windows.ResourceDictionary> (nebo uzlu XAML prostředky), se doporučuje buď definovat prostředky na <xref:System.Windows.Application> nebo <xref:System.Windows.Window> objekt úroveň, nebo definovat ve výchozí motiv při vlastní ovládací prvky. Definování prostředky v vlastního ovládacího prvku <xref:System.Windows.ResourceDictionary> ukládá dopad na výkon pro každou instanci tohoto ovládacího prvku. Například pokud máte operace náročné na výkon štětce definované jako součást definice prostředků vlastního ovládacího prvku a počet instancí vlastního ovládacího prvku, aplikace pracovní sady se výrazně zvýšit.  
  
 Pro ilustraci tohoto bodu, zvažte následující. Řekněme, že při vývoji karty herní pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pro většinu karty hry budete potřebovat 52 karet s 52 jiné řezy. Můžete rozhodnout k implementaci vlastního ovládacího prvku karta a definovat 52 štětce (každý představuje řez karty) v prostředcích vlastního ovládacího prvku karta. V hlavní aplikaci vytvořte nejdřív 52 instance tohoto ovládacího prvku karta vlastní. Každou instanci vlastního ovládacího prvku karta generuje 52 instance <xref:System.Windows.Media.Brush> objekty, které vám dává celkem 52 * 52 <xref:System.Windows.Media.Brush> objekty ve vaší aplikaci. Přesunutím štětce mimo prostředky vlastního ovládacího prvku karta do <xref:System.Windows.Application> nebo <xref:System.Windows.Window> objekt úroveň, nebo je definují výchozího motivu pro vlastní ovládací prvek, snížit pracovní sadu aplikací, protože jsou nyní sdílení 52 štětce mezi 52 instance ovládacího prvku karta.  
  
## <a name="sharing-a-brush-without-copying"></a>Sdílení štětce bez kopírování  
 Pokud máte více elementů pomocí stejné <xref:System.Windows.Media.Brush> objektu, definovat stopy jako prostředek a odkazovat na jeho místo definice vloženě štětce v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]. Tato metoda vytvoří jedna instance a znovu použít, zatímco definování štětce vložený v [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] vytvoří novou instanci pro jednotlivé elementy.  
  
 Následující příklad kódu ukazuje tento bod:  
  
 [!code-xaml[Performance#PerformanceSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Použití statické prostředky, pokud je to možné  
 Statické prostředek poskytuje hodnotu pro všechny vlastnosti atributu XAML vyhledáním odkaz na prostředek už definované. Chování vyhledávání pro tento prostředek je obdobou kompilaci vyhledávání.  
  
 Dynamické prostředku, na druhé straně se vytvořit dočasný výraz během počáteční kompilace a proto odložení vyhledávání pro prostředky, dokud hodnota požadovaný prostředek je ve skutečnosti vyžaduje, aby bylo možné vytvořit objekt. Chování vyhledávání pro tento prostředek je analogická spuštění vyhledávání, který ukládá dopad na výkon. Pomocí statické prostředky, kdykoli je to možné ve vaší aplikaci pomocí dynamické prostředků pouze v případě potřeby.  
  
 Následující příklad kódu ukazuje použití oba typy prostředků:  
  
 [!code-xaml[Performance#PerformanceSnippet8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/DynamicResource.xaml#performancesnippet8)]  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Plánování výkonu aplikace](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Využití výhod hardwaru](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Chování objektu](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Další výkonnostní doporučení](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)
