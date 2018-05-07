---
title: Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 6c73c8bbfcf7631094ddf89641de9af38f86f88e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje dvě paralelní mechanismy pro změnu vzhled ovládacího prvku, když obdrží fokus klávesnice. První mechanizmus se pomocí nastavením vlastností pro vlastnosti, jako například <xref:System.Windows.UIElement.IsKeyboardFocused%2A> v rámci styl nebo šabloně, která se použije k ovládacímu prvku. Druhý mechanismus je poskytnout samostatné styl jako hodnotu <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost; "zaměřit vizuální styl" vytvoří samostatné vizuálním stromu pro adorner, který se vykreslí nad ovládacího prvku, nemusíte měnit vizuálním stromu ovládací prvek nebo jiných uživatelského rozhraní Element nahrazením ho. Toto téma popisuje scénáře, kde každý z těchto mechanismů je vhodné.  
   
  
<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>Účelem fokus vizuální styl  
 Funkce vizuální styl fokusu poskytuje běžné "model objektu" pro představení zpětnou vazbu od uživatelů visual podle navigační klávesnice pro libovolný element uživatelského rozhraní. To je možné bez použití novou šablonu pro ovládací prvek nebo znalost složení určité šablony.  
  
 Přesněji, protože funkce vizuální styl fokusu funguje bez znalosti šablon ovládacích prvků, visual zpětnou vazbu, která lze zobrazit pro ovládacího prvku s použitím vizuální styl fokus je však nutně omezena. Funkci ve skutečnosti jaké je překrytí různých vizuálním stromu (adorner) nad vizuálním stromu jako vytvořené vykreslování ovládacího prvku pomocí jeho šablony. Definování této samostatné vizuálním stromu pomocí styl, který vyplní celé <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> vlastnost.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Výchozí chování vizuální styl fokusu  
 Vizuální styly fokus fungují jenom v případě, že akce fokus byl inicializován nástrojem klávesnice. Všechny akce myši nebo změňte programový fokus zakáže režim pro vizuální styly fokus. Další informace o rozdíly mezi režimy fokus najdete v tématu [fokus přehled](../../../../docs/framework/wpf/advanced/focus-overview.md).  
  
 Motivy pro ovládací prvky zahrnují výchozí chování vizuální styl fokus, který se stane fokus vizuální styl pro všechny ovládací prvky v motivu. Tento styl motiv je identifikována hodnota statické klíče <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>. Pokud je deklarovat vlastní vizuální styl fokus na úrovni aplikace, je nahradit toto výchozí chování styl z motivů. Případně pokud definujete celý motiv, doporučujeme, abyste používali stejný klíč k definování styl pro výchozí chování pro vaši celou motiv.  
  
 V motivy je obecně velmi jednoduchý vizuální styl výchozí fokus. Toto je hrubý aproximace:  
  
```  
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
## <a name="when-to-use-focus-visual-styles"></a>Kdy použít fokus vizuální styly  
 Koncepčně vzhled fokus vizuální styly aplikovat na ovládací prvky měla být v souladu ovládací. Jeden způsob, jak zajistit soulad se má změnit zaměření vizuální styl jenom v případě, že jsou skládání celý motiv, kde každý ovládací prvek, který je definován v motivu získá velmi stejné vizuální styl fokus nebo některé variace styl, se vztahuje vizuálně z ovládacího prvku na potřeba Karta. Alternativně můžete použít stejný styl (nebo podobné styly) k úpravě stylu každý element, může získat fokus klávesnice na stránce nebo v uživatelského rozhraní.  
  
 Nastavení <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> na styly jednotlivých ovládacích prvků, které nejsou součástí motiv není zamýšlené použití fokus vizuální styly. To je proto nekonzistentní visual chování mezi ovládacími prvky může vést k matoucí činnost koncového uživatele o fokus klávesnice. Pokud jsou záměrné chování specifické pro ovládací prvek pro fokus klávesnice, které nejsou záměrně souvislý napříč motiv, mnohem lepší přístup je použití aktivační události v styly pro jednotlivé vstupní stav vlastnosti, jako například <xref:System.Windows.UIElement.IsFocused%2A> nebo <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Vizuální styly fokus slouží výhradně pro fokus klávesnice. Vizuální styly fokus jako takový jsou typ funkce usnadnění přístupu. Pokud chcete změny uživatelského rozhraní pro jakýkoli typ fokus, zda pomocí myši, klávesnice, nebo prostřednictvím kódu programu, pak můžete neměli používat fokus vizuální styly a místo toho používejte setter a aktivační události v styly nebo šablony, které pracují z hodnoty vlastnosti Obecné fokus například `IsFocused` nebo `IsFocusWithin`.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Postup vytvoření vizuální styl fokusu  
 Styl vytvoříte pro vizuální styl fokus měli mít vždy <xref:System.Windows.Style.TargetType%2A> z <xref:System.Windows.Controls.Control>. Styl by měla obsahovat především <xref:System.Windows.Controls.ControlTemplate>. Nezadávejte cílový typ má být typ, kde je přiřazena vizuální styl fokus <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
 Vzhledem k tomu, že cílový typ je vždy <xref:System.Windows.Controls.Control>, musí styl pomocí vlastností, které jsou společné pro všechny ovládací prvky (pomocí vlastnosti <xref:System.Windows.Controls.Control> třídy a jejích základních tříd). Měli byste vytvořit šablonu, která bude správně fungovat jako překrytí k prvku uživatelského rozhraní a která nebude skrývat funkčním oblastem ovládacího prvku. Obecně platí to znamená, že vizuální zpětnou vazbu by se měla objevit mimo okraje ovládací prvek, nebo jako dočasné nebo nerušivý účinky, které nebude blokovat přístupů testování v ovládacím prvku kde se použije vizuální styl fokus. Vlastnosti, které můžete použít v šabloně vazby, které jsou užitečné pro určení Změna velikosti a rozmístění překrytí šablony zahrnují <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, a <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternativy k používání vizuální styl fokusu  
 V situacích, kde pomocí vizuální styl fokus není vhodný, buď protože jsou pouze styly jeden ovládací prvky, nebo protože chcete, aby větší kontrolu nad šablonu ovládacího prvku existuje mnoho dalších dostupné vlastnosti a techniky, které můžete vytvořit visual chování v reakci na změny v fokus.  
  
 Aktivační události, setter a událostí nastavení jsou všechny podrobněji v [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md). Zpracování událostí směrován je popsána v [směrovány Přehled událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Pokud vás zajímá konkrétně v fokus klávesnice <xref:System.Windows.UIElement.IsKeyboardFocused%2A> vlastnost závislosti lze použít pro vlastnost <xref:System.Windows.Trigger>. Aktivační událost vlastností ve stylu nebo šablonu je vhodnější technika pro definování chování fokus klávesnice, je velmi speciálně pro jeden ovládací prvek a který nemusí odpovídat vizuálně chování fokus klávesnice pro další ovládací prvky.  
  
 Jiné podobné vlastnost závislosti je <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, což může být vhodné k použití, pokud chcete vizuálně vyvolávající této fokus klávesnice je někde v rámci skládání nebo funkční oblast ovládacího prvku. Například může dojít <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> aktivační události tak, aby panel, který seskupuje několik ovládacích prvků se zobrazuje odlišně, i když fokus klávesnice přesněji může být na jednotlivý prvek v rámci tohoto panelu.  
  
 Můžete také události <xref:System.Windows.UIElement.GotKeyboardFocus> a <xref:System.Windows.UIElement.LostKeyboardFocus> (i jejich ekvivalenty u Preview). Tyto události můžete použít jako základ pro <xref:System.Windows.EventSetter>, nebo můžete napsat obslužné rutiny události v kódu.  
  
### <a name="other-focus-properties"></a>Ostatní vlastnosti fokusu  
 Pokud chcete, aby všechny možné příčiny změny fokus dosaženo visual chování, by měla základní setter nebo aktivovat na <xref:System.Windows.UIElement.IsFocused%2A> vlastnost závislosti, případně na <xref:System.Windows.UIElement.GotFocus> nebo <xref:System.Windows.UIElement.LostFocus> události použité pro <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled fokusu](../../../../docs/framework/wpf/advanced/focus-overview.md)  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)
