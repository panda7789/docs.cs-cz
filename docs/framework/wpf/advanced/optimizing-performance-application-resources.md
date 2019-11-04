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
ms.openlocfilehash: 59b124c28ade0a6c5119b651ff935d460bf4516d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458569"
---
# <a name="optimizing-performance-application-resources"></a>Optimalizace výkonu: Zdroje aplikace
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje sdílení prostředků aplikace, aby bylo možné podporovat konzistentní vzhled nebo chování napříč podobnými elementy typu. Toto téma nabízí několik doporučení v této oblasti, které vám pomůžou zlepšit výkon aplikací.  
  
 Další informace o prostředcích najdete v tématu věnovaném [prostředkům XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
## <a name="sharing-resources"></a>Sdílení prostředků  
 Pokud vaše aplikace používá vlastní ovládací prvky a definuje prostředky v <xref:System.Windows.ResourceDictionary> (nebo uzlu prostředků XAML), doporučuje se, abyste buď definovali prostředky na úrovni objektu <xref:System.Windows.Application> nebo <xref:System.Windows.Window>, nebo je definovali ve výchozím motivu pro vlastní ovládací prvky. Definování prostředků ve vlastním ovládacím prvku <xref:System.Windows.ResourceDictionary> nepředstavuje dopad na výkon pro každou instanci daného ovládacího prvku. Pokud máte například operace štětce náročné na výkon definované jako součást definice prostředků vlastního ovládacího prvku a mnoha instancí vlastního ovládacího prvku, bude pracovní sada aplikace významně zvýšena.  
  
 K ilustraci tohoto bodu Vezměte v úvahu následující skutečnosti. Řekněme, že vyvíjíte karetní hru pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pro většinu karetních her budete potřebovat 52 karet s 52 různými ploškami. Rozhodnete se implementovat vlastní ovládací prvek karty a v prostředcích vlastního ovládacího prvku karty definujete 52 štětců (které představují plošku na kartě). Ve vaší hlavní aplikaci jste zpočátku vytvořili 52 instancí tohoto vlastního ovládacího prvku karty. Každá instance vlastního ovládacího prvku karta generuje 52 instancí objektů <xref:System.Windows.Media.Brush>, což vám poskytne celkem 52 * 52 <xref:System.Windows.Media.Brush> objektů v aplikaci. Přesunutím štětců mimo prostředky vlastního ovládacího prvku karty na úroveň objektu <xref:System.Windows.Application> nebo <xref:System.Windows.Window> nebo jejich definováním ve výchozím motivu vlastního ovládacího prvku zmenšíte pracovní sadu aplikace, protože nyní sdílíte 52 štětce z 52 instance ovládacího prvku karta  
  
## <a name="sharing-a-brush-without-copying"></a>Sdílení štětce bez kopírování  
 Pokud máte více elementů, které používají stejný objekt <xref:System.Windows.Media.Brush>, definujte štětce jako prostředek a odkazujte na něj namísto definování štětce vloženého do XAML. Tato metoda vytvoří jednu instanci a znovu ji použije, zatímco při definování štětců v jazyce XAML se vytvoří nová instance pro každý prvek.  
  
 Tento bod znázorňuje následující příklad kódu:  
  
 [!code-xaml[Performance#PerformanceSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/BrushResource.xaml#performancesnippet7)]  
  
## <a name="use-static-resources-when-possible"></a>Pokud je to možné, používejte statické prostředky.  
 Statický prostředek poskytuje hodnotu pro libovolný atribut vlastnosti XAML vyhledáním odkazu na již definovaný prostředek. Chování vyhledávání pro tento prostředek je analogické k vyhledávání v době kompilace.  
  
 Dynamický prostředek na druhé straně vytvoří během počáteční kompilace dočasný výraz, čímž se odloží vyhledávání prostředků, dokud není požadovaná hodnota prostředku pro vytvoření objektu skutečně nutná. Chování vyhledávání pro tento prostředek je analogické k prohledávání za běhu, které zaplatí vliv na výkon. Používejte statické prostředky, kdykoli je to možné v aplikaci, použitím dynamických prostředků pouze v případě potřeby.  
  
 Následující ukázka kódu ukazuje použití obou typů prostředků:  
  
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
