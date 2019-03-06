---
title: Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 762abf9524b8dfc7903d5e33bdbe99f4d0eb7192
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377042"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje dvě paralelní mechanismy pro změnu vizuálního vzhledu ovládacího prvku, když dostane fokus klávesnice. První mechanismus je určený nastavením vlastností pro vlastnosti, jako <xref:System.Windows.UIElement.IsKeyboardFocused%2A> ve stylu nebo šablony, která platí pro ovládací prvek. Druhý mechanismus se snaží poskytnout styl samostatné jako hodnotu <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost; "zaměřit vizuální styl" vytvoří samostatné vizuálního stromu, který vykreslí nad ovládací prvek, nikoli změna vizuálním stromu ovládacího prvku nebo jiný prvek uživatelského rozhraní pro úpravy element podle jeho nahrazení. Toto téma popisuje scénáře, kde každý z těchto mechanismů je vhodné.  
   
  
<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>Účelem vizuální styl fokusu  
 Funkce vizuální styl fokusu poskytuje společnou "object model" pro zavedení zpětnou vazbu visual uživatelů podle navigaci pomocí klávesnice k libovolnému prvku uživatelského rozhraní. To je možné bez použití nové šablony do ovládacího prvku nebo znalosti složení konkrétní šablonu.  
  
 Přesně, protože funkce vizuální styl fokusu funguje bez znalosti šablon ovládacích prvků, vizuální zpětnou vazbu, která lze zobrazit pro ovládací prvek pomocí vizuální styl fokusu ale nemusí být omezené. Tato funkce ve skutečnosti čemu je překryv různých vizuálním stromu (doplněk pro úpravy) nad vizuálního stromu, jak byly vytvořeny pomocí ovládacího prvku vykreslování pomocí šablony. Můžete definovat tato samostatné vizuálního stromu pomocí styl, který vyplní <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Výchozí chování vizuální styl fokusu  
 Vizuální styly fokus fungují pouze v případě, že byla zahájena akce fokus klávesnice. Všechny akce myši nebo změna prostřednictvím kódu programu fokus zakáže režim pro vizuální styly fokus. Další informace o rozdíly mezi režimy fokus, naleznete v tématu [detailní přehled](focus-overview.md).  
  
 Motivy pro ovládací prvky zahrnují výchozí chování vizuální styl fokusu, který se stane vizuální styl fokusu pro všechny ovládací prvky v motivu. Tento styl motivu je identifikován jako hodnotu klíče statické <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>. Když deklarujete vlastní vizuální styl fokusu na úrovni aplikace, můžete nahradit toto výchozí chování stylu z motivů. Případně pokud definujete celý motiv, pak by měl použijete stejný klíč k definování styl výchozí chování pro celou motiv.  
  
 Výchozí vizuální styl fokusu v motivy, je obecně velmi jednoduchý. Hrubé přiblížení je následující:  
  
```xaml  
<Style x:Key="{x:Static SystemParameters.FocusVisualStyleKey}">  
  <Setter Property="Control.Template">  
    <Setter.Value>  
      <ControlTemplate>  
        <Rectangle StrokeThickness="1"  
          Stroke="Black"  
          StrokeDashArray="1 2"  
          SnapsToDevicePixels="true"/>  
      </ControlTemplate>  
    </Setter.Value>  
  </Setter>  
</Style>  
```  
  
<a name="When"></a>   
## <a name="when-to-use-focus-visual-styles"></a>Kdy použít vizuální styl fokusu  
 Koncepčně, vzhled použít na ovládací prvky vizuální styly fokus by měl být souvislé z ovládacího prvku do ovládacího prvku. Jeden způsob, jak zajistit soulad se změna vizuálního stylu pouze v případě, že vytváříte celý motivu, kde každý ovládací prvek, který je definován v motivu získá stejné vizuální styl fokusu nebo nějakou změnu stylu, které se vztahuje vizuálně fokus z ovládacího prvku pro pokračování Karta. Alternativně můžete použít stejný styl (nebo podobné styly) k úpravě stylu každý prvek může získat fokus klávesnice, na stránce nebo v uživatelském rozhraní.  
  
 Nastavení <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> na jednotlivé ovládací prvky stylů, které nejsou součástí motiv není zamýšlené použití fokus vizuální styly. Je to proto matoucí činnost koncového uživatele o fokus klávesnice může způsobit nekonzistentní visual chování mezi ovládacími prvky. Pokud se hodláte chování pro konkrétní ovládací prvek pro fokus klávesnice, které nejsou záměrně přeměnit napříč motiv, mnoho lepším řešením je použití aktivačních procedur v styly pro jednotlivé vstupní stav vlastnosti, například <xref:System.Windows.UIElement.IsFocused%2A> nebo <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Vizuální styly fokus pracovat výhradně pro fokus klávesnice. Vizuální styly fokus v důsledku toho jsou typem funkce usnadnění. Pokud chcete změny uživatelského rozhraní pro jakýkoli typ fokus, ať už pomocí myši, klávesnice, nebo prostřednictvím kódu programu, pak jste neměli používat vizuální styly fokus a místo toho používejte metody setter a aktivační události v styly a šablony, které pracují z hodnoty vlastnosti Obecné fokus například <xref:System.Windows.UIElement.IsFocused%2A> nebo <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Jak vytvořit vizuální styl fokusu  
 Styl vytvořit pro vizuální styl fokusu by měl mít vždy <xref:System.Windows.Style.TargetType%2A> z <xref:System.Windows.Controls.Control>. Styl by měla obsahovat hlavně <xref:System.Windows.Controls.ControlTemplate>. Není zadán typ cíle má být typ, ve kterém je přiřazená vizuální styl fokusu <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Protože cílový typ je vždy <xref:System.Windows.Controls.Control>, třeba stylu pomocí vlastnosti, které jsou společné pro všechny ovládací prvky (pomocí vlastnosti <xref:System.Windows.Controls.Control> třída a její základní třídy). By měl vytvořit šablonu, která bude správně fungovat jako překrytí na prvek uživatelského rozhraní a, který nebudete zakrývat funkční oblasti ovládacího prvku. Obecně platí to znamená, že vizuální zpětnou vazbu by se měla objevit mimo okraje ovládacího prvku, nebo jako dočasné nebo nerušivý efekty, které nebude blokovat přístupů testování na ovládacím prvku použití vizuální styl fokusu. Vlastnosti, které můžete použít v vazba šablony, které jsou užitečné při určování velikosti a polohování překrytí šablony zahrnují <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, a <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternativy k používání vizuální styl fokusu  
 V situacích, kdy použití vizuální styl fokusu není vhodný, protože jsou pouze stylů jeden ovládací prvky nebo chcete mít větší kontrolu nad šablonu ovládacího prvku existuje mnoho dostupné vlastnosti a techniky, které může vytvoření vizuálu chování v reakci na změny fokusu.  
  
 Aktivační události, metody setter a události nastavení jsou všechny podrobně popsány v [styly a šablony](../controls/styling-and-templating.md). Zpracování směrované události je podrobněji popsána [směrovat Přehled událostí](routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Pokud vás zajímají konkrétně fokus klávesnice, <xref:System.Windows.UIElement.IsKeyboardFocused%2A> vlastnost závislosti lze použít pro vlastnost <xref:System.Windows.Trigger>. Aktivační procedura vlastností ve stylu nebo šablony je vhodnější technika pro definování chování fokus klávesnice, který je velmi speciálně pro jeden ovládací prvek a které se nemusí shodovat vizuálně chování fokus klávesnice pro ostatní ovládací prvky.  
  
 Další podobné vlastnost závislosti je <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, což může být vhodné použít, pokud chcete provádět vizuálně volání, které se zaměřují klávesnice je chyba někde skládání nebo v rámci funkční oblasti ovládacího prvku. Například může dojít <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> aktivační událost tak, že panel, který seskupuje několik ovládacích prvků se zobrazí odlišně, i když fokus klávesnice může přesněji být na jednotlivý element v rámci panelu.  
  
 Můžete použít také události <xref:System.Windows.UIElement.GotKeyboardFocus> a <xref:System.Windows.UIElement.LostKeyboardFocus> (a také jejich ekvivalenty ve verzi Preview). Tyto události můžete použít jako základ pro <xref:System.Windows.EventSetter>, nebo můžete napsat obslužné rutiny událostí v modelu code-behind.  
  
### <a name="other-focus-properties"></a>Další vlastnosti fokus  
 Pokud chcete, aby všechny možné příčiny změny fokus pro vytvoření vizuální chování, byste měli založit setter nebo aktivaci <xref:System.Windows.UIElement.IsFocused%2A> vlastnost závislosti, případně na <xref:System.Windows.UIElement.GotFocus> nebo <xref:System.Windows.UIElement.LostFocus> událostech používaný pro <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Styly a šablony](../controls/styling-and-templating.md)
- [Přehled fokusu](focus-overview.md)
- [Přehled vstupu](input-overview.md)
