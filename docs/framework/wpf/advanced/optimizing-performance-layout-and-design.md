---
title: "Optimalizace výkonu: Rozložení a návrh"
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
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 13763e0487314fdbe7ab6fcb8b7b8711715e7a6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-layout-and-design"></a>Optimalizace výkonu: Rozložení a návrh
Návrh vašeho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace může mít vliv na jeho výkon vytvořením nárokům v Výpočet rozložení a ověření odkazy na objekty. Konstrukce objektů, zejména v době běhu může ovlivnit výkonové charakteristiky vaší aplikace.  
  
 Toto téma obsahuje doporučení pro optimální výkon v těchto oblastech.  
  
## <a name="layout"></a>Rozložení  
 Termín "rozložení průchodu" popisuje proces měření a uspořádání členů <xref:System.Windows.Controls.Panel>-odvozené kolekce objektu podřízené objekty a pak kreslení je na obrazovce. Rozložení průchodu je proces matematicky náročných – větší počet podřízených prvků v kolekci, tím větší je počet výpočty potřebné. Například pokaždé, když podřízené <xref:System.Windows.UIElement> objekt v kolekci změní pozici, má potenciál k aktivaci nového průchodu systémem rozložení. Z důvodu zavřít vztah mezi objekt charakteristiky a chování rozložení je důležité si uvědomit, typ události, které můžete vyvolat rozložení systému. Aplikace budou líp fungovat snížením co nejvíce že předat všechny nepotřebné volání rozložení.  
  
 Rozložení systému dokončení dva předává pro každý podřízený člen v kolekci: průchodu měr a předejte uspořádání. Každý podřízený objekt poskytuje vlastní přepsaného implementaci <xref:System.Windows.UIElement.Measure%2A> a <xref:System.Windows.UIElement.Arrange%2A> metody s cílem poskytnout vlastní rozložení konkrétní chování. V nejjednodušším rozložení je rekurzivní systém, který vede k element stal velikosti, umístěný a vykreslovány na obrazovce.  
  
-   Podřízená <xref:System.Windows.UIElement> objekt zahájí proces rozložení tak, že první jeho základní vlastnosti měří.  
  
-   Objektu <xref:System.Windows.FrameworkElement> vlastnosti, které souvisí s velikostí, jako například <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, a <xref:System.Windows.FrameworkElement.Margin%2A>, jsou vyhodnocovány.  
  
-   <xref:System.Windows.Controls.Panel>-určitou logiku platí, jako <xref:System.Windows.Controls.DockPanel.Dock%2A> vlastnost <xref:System.Windows.Controls.DockPanel>, nebo <xref:System.Windows.Controls.StackPanel.Orientation%2A> vlastnost <xref:System.Windows.Controls.StackPanel>.  
  
-   Obsah je uspořádané nebo umístěný po měří všechny podřízené objekty.  
  
-   Kolekce podřízených objektů je znázorněna na obrazovku.  
  
 Proces průchodu rozložení je volána znovu, pokud dojde k některé z následujících akcí:  
  
-   Podřízený objekt se přidá do kolekce.  
  
-   A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> se použije pro podřízený objekt.  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda je volána pro podřízený objekt.  
  
-   Když dojde ke změně na hodnotu vlastnosti závislosti, které je označené jako metadat, které mají vliv na míru nebo uspořádat předává.  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>Použijte nejúčinnější Panel, kde je to možné  
 Složitost proces rozložení přímo podle chování rozložení <xref:System.Windows.Controls.Panel>-odvozené elementy, které používáte. Například <xref:System.Windows.Controls.Grid> nebo <xref:System.Windows.Controls.StackPanel> řízení poskytuje mnohem více funkcí než <xref:System.Windows.Controls.Canvas> ovládacího prvku. Ceny pro toto větší zvýšení funkce je větší zvýšení výkonu nákladů. Ale pokud nechcete, aby funkce, <xref:System.Windows.Controls.Grid> poskytuje ovládací prvek, byste měli používat levněji alternativy, jako například <xref:System.Windows.Controls.Canvas> nebo vlastní panel.  
  
 Další informace najdete v tématu [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>Aktualizovat spíše než náhradou RenderTransform  
 Může být možné aktualizovat <xref:System.Windows.Media.Transform> místo nahrazení jako hodnotu <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost. To platí hlavně v situacích, které obsahují animace. Při aktualizaci existující <xref:System.Windows.Media.Transform>, se vyhnout inicializaci výpočtu nepotřebné rozložení.  
  
### <a name="build-your-tree-top-down"></a>Sestavení vaší shora dolů stromu  
 Pokud uzel je přidat nebo odebrat z logického stromu, vlastnost invalidations jsou vyvolané nadřazeného uzlu a všechny její podřízené položky. Vzor konstrukce shora dolů v důsledku toho by měla vždycky dodržet předejdete náklady nepotřebné invalidations na uzly, které již byly ověřeny. Následující tabulka ukazuje rozdíl v provádění rychlost mezi vytváření stromu shora dolů a zdola nahoru, kde je stromu 150 úrovní do hloubky s jedním <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.DockPanel> na každé úrovni.  
  
|**Akce**|**Strom sestavování (v ms)**|**Vykreslení – zahrnuje stromu sestavování (v ms)**|  
|----------------|---------------------------------|-------------------------------------------------|  
|Zdola nahoru|366|454|  
|Shora dolů|11|96|  
  
 Následující příklad kódu ukazuje, jak vytvořit top stromu dolů.  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 Další informace o logickém stromu najdete v tématu [stromy v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Plánování výkonu aplikace](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Využití výhod hardwaru](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [2D grafika a vytvoření bitové kopie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Chování objektů](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Další doporučení výkonu](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)
