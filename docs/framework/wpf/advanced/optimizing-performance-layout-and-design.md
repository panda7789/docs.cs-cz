---
title: 'Optimalizace výkonu: Rozložení a návrh'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: 8a76dd5de9f374d77345eeab3d259624546fed7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107065"
---
# <a name="optimizing-performance-layout-and-design"></a>Optimalizace výkonu: Rozložení a návrh
Návrh vašich [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci může ovlivnit její výkon tak, že vytvoříte zbytečnou režii v Výpočet rozložení a ověření odkazy na objekty. Konstrukce objektů, zejména v době běhu, mohou ovlivnit charakteristiky výkonu vaší aplikace.  
  
 Toto téma obsahuje doporučení k výkonu v těchto oblastech.  
  
## <a name="layout"></a>Rozložení  
 Termín "předání rozložení" popisuje proces měření a uspořádání členů <xref:System.Windows.Controls.Panel>-odvozené objektu kolekce podřízené prvky a nakreslením je na obrazovce. Předání rozložení je proces matematicky náročné – Čím větší počet podřízených položek v kolekci, tím větší počet vyžaduje výpočty. Například pokaždé, když podřízený <xref:System.Windows.UIElement> objekt v kolekci změní pozici, má potenciál pro aktivaci nové předáván systém rozložení. Z důvodu zavřít vztah mezi objekt charakteristiky a chování rozložení je důležité pochopit, typu události, které můžete vyvolat systém rozložení. Vaše aplikace budou líp fungovat snížením co nejvíc že předávat všechny nepotřebné volání rozložení.  
  
 Systém rozložení dokončení dva průchody pro každý podřízený člen v kolekci: míra pass a průchodu uspořádat. Každý podřízený objekt poskytuje vlastní přepsané provádění <xref:System.Windows.UIElement.Measure%2A> a <xref:System.Windows.UIElement.Arrange%2A> metody za účelem zajišťují vlastní chování specifické rozložení. V nejjednodušším rozložení je rekurzivní, která vede k elementu se velikost, umístěn a vykreslit na obrazovce.  
  
-   Podřízený <xref:System.Windows.UIElement> objekt zahájí proces rozložení tak, že první jeho základní vlastnosti měří.  
  
-   Objektu <xref:System.Windows.FrameworkElement> vlastnosti, které se vztahují na velikost, například <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, a <xref:System.Windows.FrameworkElement.Margin%2A>, jsou vyhodnocovány.  
  
-   <xref:System.Windows.Controls.Panel>– Logika specifická pro použití, jako <xref:System.Windows.Controls.DockPanel.Dock%2A> vlastnost <xref:System.Windows.Controls.DockPanel>, nebo <xref:System.Windows.Controls.StackPanel.Orientation%2A> vlastnost <xref:System.Windows.Controls.StackPanel>.  
  
-   Obsah je uspořádat nebo po změření všechny podřízené objekty umístěny.  
  
-   Kolekce podřízených objektů vykreslením na obrazovku.  
  
 Proces průchodu rozložení je znovu vyvolána, pokud kterákoli z následujících akcí:  
  
-   Podřízený objekt se přidá do kolekce.  
  
-   A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> se použije na podřízený objekt.  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda je volána pro podřízený objekt.  
  
-   Když dojde k hodnotě vlastnosti závislosti, která je označená pomocí metadat by to mělo dopad měření nebo uspořádání předá ke změně.  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>Použít Panel nejúčinnější, kde je to možné  
 Složitost procesu rozložení je přímo založena na chování rozložení <xref:System.Windows.Controls.Panel>-odvozené elementy, které používáte. Například <xref:System.Windows.Controls.Grid> nebo <xref:System.Windows.Controls.StackPanel> řízení poskytuje výrazně víc funkcí než <xref:System.Windows.Controls.Canvas> ovládacího prvku. Cena za toto větší zvýšení funkce je větší zvýšení nákladů na výkon. Ale pokud nechcete, aby funkce, která <xref:System.Windows.Controls.Grid> poskytuje ovládací prvek, jako byste měli použít méně nákladnější alternativy <xref:System.Windows.Controls.Canvas> nebo vlastní panel.  
  
 Další informace najdete v tématu [přehled panelů](../controls/panels-overview.md).  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>Místo nahrazení RenderTransform – aktualizovat  
 Je možné aktualizovat <xref:System.Windows.Media.Transform> místo nahrazení jako hodnoty <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost. To platí hlavně v situacích, které se týkají animace. Stačí aktualizovat existující <xref:System.Windows.Media.Transform>, byste se vyhnout zahájení výpočtu zbytečné rozložení aplikace.  
  
### <a name="build-your-tree-top-down"></a>Vytvoření stromu nahoru dolů  
 Při přidání nebo odebrání z logického stromu uzel vlastnost invalidations jsou vyvolány na nadřazeného uzlu a všechny jeho podřízené položky. Vzor konstrukce shora dolů v důsledku toho vždy byste měli dodržet, aby náklady zbytečné invalidations na uzly, které již byly ověřeny. Následující tabulka ukazuje rozdíl v rychlost provádění mezi sestavením stromu shora dolů a zdola nahoru, kde stromu je 150 úrovní do hloubky pomocí jediného <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.DockPanel> na každé úrovni.  
  
|**Akce**|**Strom sestavování (v ms)**|**Vykreslení – obsahuje strom sestavování (v ms)**|  
|----------------|---------------------------------|-------------------------------------------------|  
|Zdola nahoru|366|454|  
|Shora dolů|11|96|  
  
 Následující příklad kódu ukazuje, jak vytvořit horní části stromu dolů.  
  
 [!code-csharp[Performance#PerformanceSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Další informace o logickém stromu, naleznete v tématu [stromy v subsystému WPF](trees-in-wpf.md).  
  
## <a name="see-also"></a>Viz také:

- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další doporučení k optimalizaci výkonu](optimizing-performance-other-recommendations.md)
- [Rozložení](layout.md)
