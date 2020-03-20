---
title: Přehled překryvných objektů
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 911130d52744c5ba54750f214829a5d1900e083c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185957"
---
# <a name="popup-overview"></a>Přehled překryvných objektů
<xref:System.Windows.Controls.Primitives.Popup> Ovládací prvek poskytuje způsob, jak zobrazit obsah v samostatném okně, které plave přes aktuální okno aplikace vzhledem k určenému prvku nebo souřadnice obrazovky. Toto téma <xref:System.Windows.Controls.Primitives.Popup> představuje ovládací prvek a poskytuje informace o jeho použití.  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>Co je vyskakovací okno?  
 Ovládací <xref:System.Windows.Controls.Primitives.Popup> prvek zobrazuje obsah v samostatném okně vzhledem k prvku nebo bodu na obrazovce. Pokud <xref:System.Windows.Controls.Primitives.Popup> je viditelná, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> vlastnost je `true`nastavena na .  
  
> [!NOTE]
> A <xref:System.Windows.Controls.Primitives.Popup> se automaticky neotevře, když se ukazatel myši přesune nad nadřazený objekt. Pokud chcete, <xref:System.Windows.Controls.Primitives.Popup> aby se automaticky <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> otevřel, použijte třídu nebo. Další informace naleznete v [tématu Přehled popisů](tooltip-overview.md).  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>Vytvoření místního blokování  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.Primitives.Popup> definovat ovládací prvek, <xref:System.Windows.Controls.Button> který je podřízeným prvkem ovládacího prvku. Vzhledem <xref:System.Windows.Controls.Button> k tomu, že a může mít <xref:System.Windows.Controls.Button> pouze <xref:System.Windows.Controls.Primitives.Popup> jeden podřízený prvek, tento příklad umístí text pro a ovládací prvky v <xref:System.Windows.Controls.StackPanel>. Obsah <xref:System.Windows.Controls.Primitives.Popup> zobrazí v ovládacím <xref:System.Windows.Controls.TextBlock> prvku, který zobrazuje jeho text v samostatném okně, <xref:System.Windows.Controls.Button> které plave nad oknem aplikace v blízkosti související ovládací prvek.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>Ovládací prvky, které implementují místní okno  
 Ovládací prvky můžete vytvořit <xref:System.Windows.Controls.Primitives.Popup> do jiných ovládacích prvků. Následující ovládací prvky implementují <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek pro konkrétní použití:  
  
- <xref:System.Windows.Controls.ToolTip>. Pokud chcete vytvořit popis pro prvek, použijte <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> a třídy. Další informace naleznete v [tématu Přehled popisů](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Pokud chcete vytvořit místní nabídku pro prvek, použijte <xref:System.Windows.Controls.ContextMenu> ovládací prvek. Další informace naleznete v tématu [ContextMenu Overview](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Pokud chcete vytvořit ovládací prvek výběru, který obsahuje rozevírací seznam, <xref:System.Windows.Controls.ComboBox> který lze zobrazit nebo skrýt, použijte ovládací prvek.  
  
- <xref:System.Windows.Controls.Expander>. Pokud chcete vytvořit ovládací prvek, který zobrazí záhlaví s sbalitelnou oblastí, která zobrazuje obsah, použijte <xref:System.Windows.Controls.Expander> ovládací prvek. Další informace naleznete v tématu [Expander Overview](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>Místní chování a vzhled  
 Ovládací <xref:System.Windows.Controls.Primitives.Popup> prvek poskytuje funkce, které umožňuje přizpůsobit jeho chování a vzhled. Můžete například nastavit chování a zavření, animaci, krytí <xref:System.Windows.Controls.Primitives.Popup> a bitmapové efekty a velikost a umístění.  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>Chování při otevírání a zavírání  
 Ovládací <xref:System.Windows.Controls.Primitives.Popup> prvek zobrazí jeho <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> obsah, `true`když je vlastnost nastavena na . Ve výchozím <xref:System.Windows.Controls.Primitives.Popup> nastavení zůstane <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> otevřená, `false`dokud není vlastnost nastavena na . Výchozí chování však můžete změnit <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> nastavením `false`vlastnosti na . Pokud nastavíte `false`tuto <xref:System.Windows.Controls.Primitives.Popup> vlastnost na , okno obsahu má zachycení myši. Ztratí <xref:System.Windows.Controls.Primitives.Popup> zachycení myši a okno zavře, když dojde k <xref:System.Windows.Controls.Primitives.Popup> události myši mimo okno.  
  
 A <xref:System.Windows.Controls.Primitives.Popup.Opened> <xref:System.Windows.Controls.Primitives.Popup.Closed> události jsou vyvolány při otevření nebo zavření <xref:System.Windows.Controls.Primitives.Popup> okna obsahu.  
  
<a name="Animation"></a>
### <a name="animation"></a>Animace  
 Ovládací <xref:System.Windows.Controls.Primitives.Popup> prvek má integrovanou podporu pro animace, které jsou obvykle spojeny s chováním, jako je fade-in a slide-in. Tyto animace můžete zapnout nastavením vlastnosti <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> na hodnotu výčtu. <xref:System.Windows.Controls.Primitives.PopupAnimation> Aby <xref:System.Windows.Controls.Primitives.Popup> animace fungovaly správně, je <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> nutné `true`nastavit vlastnost na .  
  
 Můžete také použít animace, <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.Primitives.Popup> jako je ovládací prvek.  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>Efektkrytí a bitmapové efekty  
 Vlastnost <xref:System.Windows.UIElement.Opacity%2A> ovládacího <xref:System.Windows.Controls.Primitives.Popup> prvku nemá žádný vliv na jeho obsah. Ve výchozím <xref:System.Windows.Controls.Primitives.Popup> nastavení je okno obsahu neprůhledné. Chcete-li <xref:System.Windows.Controls.Primitives.Popup>vytvořit průhlednou vlastnost , nastavte <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> vlastnost na `true`.  
  
 Obsah bitmapové <xref:System.Windows.Controls.Primitives.Popup> efekty, například <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, které přímo nastavíte na <xref:System.Windows.Controls.Primitives.Popup> ovládacím prvku nebo na jiném prvku v nadřazeném okně. Aby se bitmapové efekty <xref:System.Windows.Controls.Primitives.Popup>zobrazily na obsahu , je nutné nastavit bitmapový efekt přímo na jeho obsah. Pokud je například podřízená součást a <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.StackPanel>, nastavte <xref:System.Windows.Controls.StackPanel>bitmapový efekt na rozhraní .  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>Velikost automaticky otevíraných vyska  
 Ve výchozím <xref:System.Windows.Controls.Primitives.Popup> nastavení je velikost a automaticky nastavena podle obsahu. Dojde-li k automatické změně velikosti, mohou být některé bitmapové efekty skryté, protože výchozí velikost oblasti obrazovky, která je definována pro <xref:System.Windows.Controls.Primitives.Popup> obsah, neposkytuje dostatek místa pro zobrazení bitmapových efektů.  
  
 <xref:System.Windows.Controls.Primitives.Popup>obsah může být také zakryt, když <xref:System.Windows.UIElement.RenderTransform%2A> nastavíte obsah. V tomto scénáři může být nějaký obsah skrytý, pokud obsah <xref:System.Windows.Controls.Primitives.Popup> transformované <xref:System.Windows.Controls.Primitives.Popup>přesahuje oblast originálu . Pokud bitmapový efekt nebo transformace vyžaduje více místa, <xref:System.Windows.Controls.Primitives.Popup> můžete definovat okraj kolem obsahu, abyste ovládacímu prvku poskytli více prostoru.  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>Definování pozice automaticky otevírané nabídky  
 Vyskakovací okno <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>můžete <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>umístit <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> nastavením vlastností , , , a. Další informace naleznete v tématu [Chování umístění v místních upech](popup-placement-behavior.md). Když <xref:System.Windows.Controls.Primitives.Popup> je zobrazen na obrazovce, není přemístit sám, pokud jeho nadřazený je přemístěn.  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění automaticky otevíraná pole  
 Umístění <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku můžete přizpůsobit zadáním sady souřadnic, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> které jsou <xref:System.Windows.Controls.Primitives.Popup> relativní vzhledem k místu, kde se má zobrazit.  
  
 Chcete-li umístění <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> přizpůsobit, <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>nastavte vlastnost na . Potom definujte delegáta, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> který vrátí sadu možných bodů umístění a <xref:System.Windows.Controls.Primitives.Popup>primárních os (v pořadí podle priority) pro . Bod, který zobrazuje největší <xref:System.Windows.Controls.Primitives.Popup> část je automaticky vybrán. Příklad najdete v [tématu Určení vlastní místní polohy](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>Místní okno a vizuální strom  
 Ovládací <xref:System.Windows.Controls.Primitives.Popup> prvek nemá vlastní vizuální strom; místo toho vrátí velikost 0 (nula) při <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> volání metody pro. <xref:System.Windows.Controls.Primitives.Popup> Však při nastavení <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> <xref:System.Windows.Controls.Primitives.Popup> vlastnosti `true`do , nové okno s vlastním vizuálním stromem je vytvořen. Nové okno obsahuje <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsah <xref:System.Windows.Controls.Primitives.Popup>. Šířka a výška nového okna nesmí být větší než 75 procent šířky nebo výšky obrazovky.  
  
 Ovládací <xref:System.Windows.Controls.Primitives.Popup> prvek udržuje odkaz <xref:System.Windows.Controls.Primitives.Popup.Child%2A> na jeho obsah jako logický podřízený. Při vytvoření nového <xref:System.Windows.Controls.Primitives.Popup> okna se obsah stane vizuální podřízenou částí <xref:System.Windows.Controls.Primitives.Popup>okna a zůstane logickým podřízeným souborem . Naopak <xref:System.Windows.Controls.Primitives.Popup> zůstává logickým nadřazeným nadřazeným obsahem jeho <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsahu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Témata s postupy](popup-how-to-topics.md)
- [Témata s postupy](tooltip-how-to-topics.md)
