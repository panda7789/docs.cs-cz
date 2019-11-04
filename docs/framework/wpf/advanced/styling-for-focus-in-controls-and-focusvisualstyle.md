---
title: Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard focus [WPF]
- focus [WPF], visual styling
- styles [WPF], focus visual style
ms.assetid: 786ac576-011b-4d72-913b-558deccb9b35
ms.openlocfilehash: 988b084144532df6f7a6073184fcf035b0813bfd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458677"
---
# <a name="styling-for-focus-in-controls-and-focusvisualstyle"></a>Nastavení stylů pro fokus v ovládacích prvcích a FocusVisualStyle
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje dva paralelní mechanismy pro změnu vizuálního vzhledu ovládacího prvku, když obdrží fokus klávesnice. Prvním mechanismem je použití setter vlastností pro vlastnosti, jako je například <xref:System.Windows.UIElement.IsKeyboardFocused%2A> v rámci stylu nebo šablony, které jsou použity pro ovládací prvek. Druhým mechanismem je poskytnout samostatný styl jako hodnotu vlastnosti <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>; styl výběru fokusu vytvoří samostatný vizuální strom pro doplňku, který kreslí nad ovládací prvek, nikoli změnou vizuálního stromu ovládacího prvku nebo jiného prvku uživatelského rozhraní jeho nahrazením. Toto téma popisuje scénáře, kde je každý z těchto mechanismů vhodný.  

<a name="Purpose"></a>   
## <a name="the-purpose-of-focus-visual-style"></a>Účel vizuálního stylu fokusu  
 Funkce vizuálního stylu fokusu poskytuje společný "objektový model" pro představení vizuální zpětné vazby uživatelů na základě navigace pomocí klávesnice do libovolného prvku uživatelského rozhraní. To je možné bez použití nové šablony k ovládacímu prvku nebo znalosti konkrétního složení šablony.  
  
 Nicméně přesně vzhledem k tomu, že funkce vizuálu fokusu funguje bez znalosti šablon ovládacích prvků, vizuální zpětnou vazbu, která se dá zobrazit pro ovládací prvek pomocí vizuálního stylu fokusu, je nutně omezená. Co funkce ve skutečnosti dělá, je překryv jiného vizuálního stromu (doplňku) na vizuálním stromu, který byl vytvořen vykreslováním ovládacího prvku prostřednictvím jeho šablony. Tento samostatný vizuální strom definujete pomocí stylu, který vyplní vlastnost <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>.  
  
<a name="Default"></a>   
## <a name="default-focus-visual-style-behavior"></a>Výchozí chování stylu vizuálu fokusu  
 Vizuální styly fokusu se chovají pouze v případě, že byla akce fokusu iniciována klávesnicí. Jakákoli akce myši nebo Programová změna v rámci fokusu zakáže režim pro výběr vizuálních stylů. Další informace o rozdílech mezi detailními režimy najdete v tématu [Přehled fokusu](focus-overview.md).  
  
 Motivy pro ovládací prvky obsahují výchozí chování fokusu ovládacího prvku, které se stávají vizuálním stylem fokusu pro všechny ovládací prvky v motivu. Tento styl motivu je identifikován hodnotou statického klíče <xref:System.Windows.SystemParameters.FocusVisualStyleKey%2A>. Když deklarujete vlastní vizuální styl fokusu na úrovni aplikace, nahradíte toto výchozí chování stylu z motivů. Případně, pokud definujete celý motiv, měli byste použít stejný klíč k definování stylu pro výchozí chování celého motivu.  
  
 V motivech je výchozím vizuálním stylem fokusu všeobecně velmi jednoduché. Následuje hrubá aproximace:  
  
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
 V koncepčním případě by se měl vzhled vizuálních stylů fokusu aplikovaný na ovládací prvky spojit s ovládacím prvkem. Jedním ze způsobů, jak zajistit soudržnost, je změnit styl vizuálního zaměření pouze v případě, že sestavování celého motivu, kde každý ovládací prvek, který je definován v motivu, získá buď stejný vizuální styl fokusu, nebo určitou variaci stylu, který vizuálně souvisí s ovládacím prvkem s pokračováním. rol. Alternativně můžete použít stejný styl (nebo podobné styly) pro styl každého prvku, který je zaměřen na klávesnici na stránce nebo v uživatelském rozhraní.  
  
 Nastavení <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> pro jednotlivé styly ovládacích prvků, které nejsou součástí motivu, není zamýšlené použití vizuálních stylů fokusu. Důvodem je, že nekonzistentní vizuální chování mezi ovládacími prvky může vést k matoucímu uživatelskému rozhraní týkajícímu se fokusu klávesnice. Pokud pro fokus klávesnice nepoužíváte chování specifické pro ovládací prvky, které jsou záměrně nesouvislé v rámci motivu, je mnohem lepším řešením použití triggerů v stylech pro jednotlivé vlastnosti stavu vstupu, například <xref:System.Windows.UIElement.IsFocused%2A> nebo <xref:System.Windows.UIElement.IsKeyboardFocused%2A>.  
  
 Vizuální styly fokusu fungují výhradně pro fokus klávesnice. V takovém případě jsou vizuální styly fokusu typem funkce usnadnění. Pokud chcete změnit uživatelské rozhraní pro jakýkoliv typ fokusu, ať už přes myš, klávesnici nebo programově, neměli byste používat vizuální styly fokusu a místo toho byste měli použít metody setter a triggery v stylech nebo šablonách, které fungují z hodnoty vlastností obecného výběru. například <xref:System.Windows.UIElement.IsFocused%2A> nebo <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>.  
  
<a name="How"></a>   
## <a name="how-to-create-a-focus-visual-style"></a>Postup vytvoření vizuálního stylu fokusu  
 Styl, který vytvoříte pro vizuální styl fokusu, by měl mít vždycky <xref:System.Windows.Style.TargetType%2A> <xref:System.Windows.Controls.Control>. Styl by měl sestávat hlavně z <xref:System.Windows.Controls.ControlTemplate>. Neurčíte cílový typ, který bude typem, který je přiřazen k <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>mu stylu fokusu.  
  
 Vzhledem k tomu, že cílový typ je vždy <xref:System.Windows.Controls.Control>, je nutné styl použít pomocí vlastností, které jsou společné pro všechny ovládací prvky (pomocí vlastností třídy <xref:System.Windows.Controls.Control> a jejích základních tříd). Měli byste vytvořit šablonu, která bude správně fungovat jako překryv pro prvek uživatelského rozhraní a který nebude krýt funkční oblasti tohoto ovládacího prvku. Obecně to znamená, že vizuální zpětná vazba by se měla zobrazit mimo řídicí okraje nebo jako dočasné nebo nenáročné efekty, které neblokují testování přístupů na ovládacím prvku, kde je použit styl vizuálu fokusu. Vlastnosti, které lze použít ve vazbách šablon, které jsou užitečné při určování velikosti a umístění překryté šablony, zahrnují <xref:System.Windows.FrameworkElement.ActualHeight%2A>, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>a <xref:System.Windows.Controls.Control.Padding%2A>.  
  
<a name="Alternatives"></a>   
## <a name="alternatives-to-using-a-focus-visual-style"></a>Alternativy k použití vizuálního stylu fokusu  
 V situacích, kdy použití stylu fokusu fokusu není vhodné, buď protože přidáváte pouze jednotlivé ovládací prvky, nebo protože potřebujete větší kontrolu nad šablonou ovládacího prvku, existuje mnoho dalších přístupných vlastností a technik, které mohou vytvořit vizuál. chování v reakci na změny fokusu.  
  
 Triggery, metody setter a metody setter jsou podrobněji popsány v článku [stylování a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md). Směrované zpracování událostí je popsáno v tématu [Přehled směrovaných událostí](routed-events-overview.md).  
  
### <a name="iskeyboardfocused"></a>IsKeyboardFocused  
 Pokud vás zajímá konkrétně fokus klávesnice, lze vlastnost <xref:System.Windows.UIElement.IsKeyboardFocused%2A> Dependency použít pro <xref:System.Windows.Trigger>vlastností. Aktivační událost vlastnosti ve stylu nebo šabloně je vhodnější pro definování chování fokusu klávesnice, které je velmi vhodné pro jeden ovládací prvek a který nemusí vizuálně odpovídat chování fokusu klávesnice pro jiné ovládací prvky.  
  
 Další podobná vlastnost závislosti je <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>, která může být vhodná k použití, pokud chcete vizuálně vyzvat, aby se fokus klávesnice nacházet někde v rámci skládání nebo v rámci funkční oblasti ovládacího prvku. Například můžete umístit aktivační událost <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> tak, aby se panel, který seskupuje několik ovládacích prvků, zobrazoval jinak, i když fokus klávesnice může být přesnější na jednotlivém prvku v tomto panelu.  
  
 Můžete také použít události <xref:System.Windows.UIElement.GotKeyboardFocus> a <xref:System.Windows.UIElement.LostKeyboardFocus> (stejně jako jejich ekvivalenty ve verzi Preview). Tyto události lze použít jako základ pro <xref:System.Windows.EventSetter>, nebo můžete napsat obslužné rutiny pro události v kódu na pozadí.  
  
### <a name="other-focus-properties"></a>Vlastnosti dalších vlastností výběru  
 Pokud chcete, aby všechny možné příčiny se změnou fokusu na vizuální chování, měli byste založit metodu setter nebo Trigger na vlastnosti závislosti <xref:System.Windows.UIElement.IsFocused%2A> nebo případně na událostech <xref:System.Windows.UIElement.GotFocus> nebo <xref:System.Windows.UIElement.LostFocus>, které se používají pro <xref:System.Windows.EventSetter>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled fokusu](focus-overview.md)
- [Přehled vstupu](input-overview.md)
