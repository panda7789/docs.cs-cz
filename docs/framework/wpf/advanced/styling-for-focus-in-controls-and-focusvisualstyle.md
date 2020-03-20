---
title: Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: fda7ed12d232af5a7cfb8eb43cbb09eb793da171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141196"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje dva paralelní mechanismy pro změnu vizuální vzhled ovládacího prvku, když obdrží fokus klávesnice. Prvním mechanismem je použití nastavení vlastností <xref:System.Windows.UIElement.IsKeyboardFocused%2A> pro vlastnosti, například v rámci stylu nebo šablony, která je použita na ovládací prvek. Druhý mechanismus je poskytnout samostatný styl jako <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> hodnotu vlastnosti; "fokus vizuální styl" vytvoří samostatný vizuální strom pro adorner, který čerpá na horní části ovládacího prvku, spíše než měnit vizuální strom ovládacího prvku nebo jiného prvku rozhraní jeho nahrazením. Toto téma popisuje scénáře, kde každý z těchto mechanismů je vhodné.  

<a name="Purpose"></a>
## <a name="the-purpose-of-focus-visual-style"></a>Účel zaostření vizuální styl  
 Funkce vizuálního stylu fokusu poskytuje společný "objektový model" pro zavedení vizuální zpětné vazby od uživatelů na základě navigace pomocí klávesnice na libovolný prvek uživatelského rozhraní. To je možné bez použití nové šablony na ovládací prvek nebo znát konkrétní složení šablony.  
  
 Ale právě proto, že funkce vizuálnístyl fokusu funguje bez znalosti šablon ovládacích prvků, vizuální zpětná vazba, která může být zobrazena pro ovládací prvek pomocí vizuálního stylu fokusu, je nutně omezená. Co funkce ve skutečnosti dělá, je překrytí jiného vizuálního stromu (adorner) v horní části vizuálního stromu, jak je vytvořeno vykreslování ovládacího prvku prostřednictvím šablony. Tento samostatný vizuální strom definujete pomocí <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> stylu, který vyplní vlastnost.  
  
<a name="Default"></a>
## <a name="default-focus-visual-style-behavior"></a>Výchozí chování vizuálního stylu fokusu  
 Vizuální styly fokusu se chovají pouze v případě, že akce fokusu byla iniciována klávesnicí. Jakákoli akce myši nebo programová změna fokusu zakáže režim vizuálních stylů fokusu. Další informace o rozdílech mezi režimy fokusu naleznete v [tématu Focus Overview](focus-overview.md).  
  
 Motivy pro ovládací prvky zahrnují výchozí chování vizuálního stylu fokusu, které se stane vizuálním stylem fokusu pro všechny ovládací prvky v motivu. Tento styl motivu je identifikován hodnotou <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>statického klíče . Když deklarujete vlastní vizuální styl fokusu na úrovni aplikace, nahradíte toto výchozí chování stylu z motivů. Případně pokud definujete celý motiv, měli byste použít stejný klíč k definování stylu pro výchozí chování pro celý motiv.  
  
 V tématech je výchozí vizuální styl fokusu obecně velmi jednoduchý. Následuje hrubá aproximace:  
  
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
## <a name="when-to-use-focus-visual-styles"></a>Kdy použít vizuální styly fokusu  
 Koncepčně vzhled fokus vizuální styly aplikované na ovládací prvky by měly být koherentní od ovládacího prvku k ovládacímu prvku. Jedním ze způsobů, jak zajistit soudržnost, je změnit vizuální styl zaostření pouze v případě, že skládáte celý motiv, kde každý ovládací prvek, který je definován v motivu, získá buď stejný vizuální styl zaměření, nebo nějakou variantu stylu, který je vizuálně příbuzný z ovládacího prvku na Ovládací prvek. Případně můžete použít stejný styl (nebo podobné styly) styl každý prvek fokusta klávesnice na stránce nebo v ui.  
  
 Nastavení <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> jednotlivých stylů ovládacích prvků, které nejsou součástí motivu, není zamýšleným použitím vizuálních stylů fokusu. Důvodem je, že nekonzistentní vizuální chování mezi ovládacími prvky může vést k matoucí uživatelské prostředí týkající se fokusu klávesnice. Pokud máte v úmyslu chování specifické pro ovládací prvek pro fokus klávesnice, které záměrně nejsou koherentní napříč tématem, <xref:System.Windows.UIElement.IsFocused%2A> <xref:System.Windows.UIElement.IsKeyboardFocused%2A>mnohem lepší mů e být přístup některou z aktivačních událostí je použití aktivačních událostí ve stylech pro jednotlivé vlastnosti stavu vstupu, například nebo .  
  
 Vizuální styly fokusu fungují výhradně pro zaostření klávesnice. Vizuální styly fokusu jsou jako takové typem funkce usnadnění přístupu. Pokud chcete změny uživatelského rozhraní pro jakýkoli typ fokusu, ať už pomocí myši, klávesnice nebo programově, pak byste neměli používat fokus vizuální styly a místo <xref:System.Windows.UIElement.IsFocused%2A> toho <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>použít setters a aktivační události ve stylech nebo šablon, které pracují z hodnoty obecné fokus vlastnosti, jako je nebo .  
  
<a name="How"></a>
## <a name="how-to-create-a-focus-visual-style"></a>Jak vytvořit vizuální styl fokusu  
 Styl, který vytvoříte pro vizuální styl <xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.Controls.Control>fokusu, by měl mít vždy název . Styl by se měl <xref:System.Windows.Controls.ControlTemplate>skládat hlavně z . Nezadáte cílový typ jako typ, ve kterém je vizuální <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>styl fokusu přiřazen k souboru .  
  
 Vzhledem k tomu, že cílový typ je vždy <xref:System.Windows.Controls.Control>, musíte styl <xref:System.Windows.Controls.Control> pomocí vlastností, které jsou společné pro všechny ovládací prvky (pomocí vlastností třídy a její základní třídy). Měli byste vytvořit šablonu, která bude správně fungovat jako překrytí prvku uživatelského rozhraní a která nebude zakrývat funkční oblasti ovládacího prvku. Obecně to znamená, že vizuální zpětná vazba by se měla zobrazit mimo ovládací okraje nebo jako dočasné nebo nenápadné efekty, které nebudou blokovat testování přístupů na ovládací ms, kde je použit vizuální styl fokusu. Mezi vlastnosti, které lze použít ve vazbě šablony, které jsou užitečné <xref:System.Windows.FrameworkElement.ActualHeight%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A>pro <xref:System.Windows.FrameworkElement.Margin%2A>určení <xref:System.Windows.Controls.Control.Padding%2A>velikosti a umístění překryvné šablony, patří , , , a .  
  
<a name="Alternatives"></a>
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternativy k použití vizuálního stylu fokusu  
 V situacích, kdy použití vizuálního stylu fokusu není vhodné, protože jste pouze styling jednotlivé ovládací prvky nebo protože chcete větší kontrolu nad šablonou ovládacího prvku, existuje mnoho dalších přístupných vlastností a technik, které mohou vytvořit vizuální chování v reakci na změny v zaostření.  
  
 Aktivační události, nastavení a nastavení událostí jsou podrobně popsány v [stylingu a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md). Zpracování směrovaných událostí je popsáno v [přehledu směrovaných událostí](routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>Na iskeyboardfocused  
 Pokud máte konkrétně zájem o <xref:System.Windows.UIElement.IsKeyboardFocused%2A> fokus klávesnice, vlastnost závislosti <xref:System.Windows.Trigger>lze použít pro vlastnost . Aktivační událost vlastnosti ve stylu nebo šabloně je vhodnější technika pro definování chování fokusu klávesnice, která je velmi specificky pro jeden ovládací prvek a která nemusí vizuálně odpovídat chování fokusu klávesnice pro jiné ovládací prvky.  
  
 Další podobná vlastnost <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>závislosti je , které mohou být vhodné použít, pokud chcete vizuálně volat, že fokus klávesnice je někde v rámci skládání nebo v rámci funkční oblasti ovládacího prvku. Můžete například umístit <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> aktivační událost tak, aby panel, který seskupuje několik ovládacích prvků, sejmul odlišně, i když fokus klávesnice může být přesněji na jednotlivém prvku v rámci tohoto panelu.  
  
 Můžete také použít <xref:System.Windows.UIElement.GotKeyboardFocus> události <xref:System.Windows.UIElement.LostKeyboardFocus> a (stejně jako jejich ekvivalenty náhledu). Tyto události můžete použít jako <xref:System.Windows.EventSetter>základ pro , nebo můžete psát obslužné rutiny pro události v kódu na pozadí.  
  
### <a name="other-focus-properties"></a>Další vlastnosti fokusu  
 Pokud chcete, aby všechny možné příčiny změny fokusu vytvořily vizuální chování, měli byste založit nastavení nebo aktivační událost na vlastnosti <xref:System.Windows.UIElement.IsFocused%2A> závislosti nebo alternativně na událostech <xref:System.Windows.UIElement.GotFocus> nebo <xref:System.Windows.UIElement.LostFocus> událostech používaných pro . <xref:System.Windows.EventSetter>  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled fokusu](focus-overview.md)
- [Přehled vstupu](input-overview.md)
