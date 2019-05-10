---
title: Přehled překryvných objektů
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 53283619d1bd2727bdca1df6a3a408ec0ce873a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625712"
---
# <a name="popup-overview"></a>Přehled překryvných objektů
<xref:System.Windows.Controls.Primitives.Popup> Ovládacího prvku poskytuje způsob, jak zobrazit obsah v samostatném okně umístěný za aktuální období aplikace vzhledem k určené souřadnice prvek nebo obrazovka. Toto téma představuje <xref:System.Windows.Controls.Primitives.Popup> řízení a poskytuje informace o jeho použití.  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Co je automaticky otevíraného okna?  
 A <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek zobrazí obsah v samostatném okně vzhledem k elementu nebo bodě na obrazovce. Když <xref:System.Windows.Controls.Primitives.Popup> viditelnost <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> je nastavena na `true`.  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Primitives.Popup> se neotevře automaticky při umístění ukazatele myši nad jeho nadřazený objekt. Pokud chcete, aby <xref:System.Windows.Controls.Primitives.Popup> automaticky otevřít pomocí aplikace <xref:System.Windows.Controls.ToolTip> nebo <xref:System.Windows.Controls.ToolTipService> třídy. Další informace najdete v tématu [ToolTip – přehled](tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Vytváří se automaticky otevíraného okna  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.Primitives.Popup> prvek, který je podřízený prvek <xref:System.Windows.Controls.Button> ovládacího prvku. Protože <xref:System.Windows.Controls.Button> může mít pouze jeden podřízený element, v tomto příkladu vloží text <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Primitives.Popup> ovládacích prvků v <xref:System.Windows.Controls.StackPanel>. Obsah <xref:System.Windows.Controls.Primitives.Popup> se zobrazí v <xref:System.Windows.Controls.TextBlock> ovládací prvek, který zobrazí jeho textu v samostatném okně, které čísel s plovoucí čárkou nad okna aplikace poblíž související <xref:System.Windows.Controls.Button> ovládacího prvku.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Ovládací prvky, které implementují automaticky otevíraného okna  
 Můžete vytvářet <xref:System.Windows.Controls.Primitives.Popup> ovládacích prvků do jiných ovládacích prvků. Implementujte následující ovládací prvky <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek pro konkrétní použití:  
  
- <xref:System.Windows.Controls.ToolTip>. Pokud chcete vytvořit popisek pro element, použijte <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> třídy. Další informace najdete v tématu [ToolTip – přehled](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Pokud chcete vytvořit kontextovou nabídku pro prvek, použijte <xref:System.Windows.Controls.ContextMenu> ovládacího prvku. Další informace najdete v tématu [ContextMenu – přehled](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Pokud chcete vytvořit ovládacího prvku pro výběr, který se má pole rozevíracího seznamu, kterou lze použít zobrazené nebo skryté, <xref:System.Windows.Controls.ComboBox> ovládacího prvku.  
  
- <xref:System.Windows.Controls.Expander>. Pokud chcete vytvořit pro ovládací prvek zobrazující záhlaví s sbalitelné oblasti, která zobrazuje obsah, použijte <xref:System.Windows.Controls.Expander> ovládacího prvku. Další informace najdete v tématu [přehled rozšíření](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Automaticky otevírané okno chování a vzhledu  
 <xref:System.Windows.Controls.Primitives.Popup> Ovládacího prvku poskytuje funkce, které umožňuje přizpůsobit jeho chování a vzhledu. Například můžete nastavit a chování, animace, krytí a rastrový obrázek efekty a <xref:System.Windows.Controls.Primitives.Popup> velikost a umístění.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Otevření a zavření chování  
 A <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek zobrazí jeho obsah, když <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> je nastavena na `true`. Ve výchozím nastavení <xref:System.Windows.Controls.Primitives.Popup> zůstane otevřený, dokud <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> je nastavena na `false`. Můžete však změnit výchozí chování tak, že nastavíte <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> vlastnost `false`. Pokud nastavíte tuto vlastnost na `false`, <xref:System.Windows.Controls.Primitives.Popup> okno obsahu má zachycení myši. <xref:System.Windows.Controls.Primitives.Popup> Myši ztratí zachycení a zavře okno při výskytu události myši mimo <xref:System.Windows.Controls.Primitives.Popup> okna.  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened> a <xref:System.Windows.Controls.Primitives.Popup.Closed> události jsou vyvolány při <xref:System.Windows.Controls.Primitives.Popup> okno obsahu je otevřeno nebo Uzavřeno.  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animace  
 <xref:System.Windows.Controls.Primitives.Popup> Ovládací prvek má integrovanou podporu pro animace, které jsou obvykle přidruženy k chování jako vysouvaly a snímků. Tyto animace budete můžete zapnout tak, že nastavíte <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> vlastnost <xref:System.Windows.Controls.Primitives.PopupAnimation> hodnota výčtu. Pro <xref:System.Windows.Controls.Primitives.Popup> animace fungovala správně, je nutné nastavit <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> vlastnost `true`.  
  
 Můžete také použít animace jako <xref:System.Windows.Media.Animation.Storyboard> k <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Krytí a bitmapových efektů  
 <xref:System.Windows.UIElement.Opacity%2A> Vlastnost <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek nemá žádný vliv na jeho obsah. Ve výchozím nastavení <xref:System.Windows.Controls.Primitives.Popup> okno obsahu je skrytá. Chcete-li vytvořit transparentní <xref:System.Windows.Controls.Primitives.Popup>, nastavte <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> vlastnost `true`.  
  
 Obsah <xref:System.Windows.Controls.Primitives.Popup> nedědí bitmapových efektů, jako například <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, přímo nastavit na <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku nebo na jiný prvek do nadřazeného okna. Pro bitmapových efektů, aby se zobrazovaly na obsah <xref:System.Windows.Controls.Primitives.Popup>, je nutné nastavit rastrový efekt přímo na jeho obsah. Například pokud podřízený <xref:System.Windows.Controls.Primitives.Popup> je <xref:System.Windows.Controls.StackPanel>, nastavit rastrový efekt <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Velikost automaticky otevíraného okna  
 Ve výchozím nastavení <xref:System.Windows.Controls.Primitives.Popup> automaticky přizpůsoben pro jeho obsah. Pokud dojde k automatické nastavování velikosti, některé bitmapových efektů může skrýt, protože výchozí velikost oblasti obrazovky, který je definován pro <xref:System.Windows.Controls.Primitives.Popup> obsah neposkytuje dost místa pro bitmapových efektů pro zobrazení.  
  
 <xref:System.Windows.Controls.Primitives.Popup> obsah můžete také zakryto při nastavení <xref:System.Windows.UIElement.RenderTransform%2A> na obsah. V tomto scénáři může být skrytá nějaký obsah, pokud obsah transformovaná <xref:System.Windows.Controls.Primitives.Popup> přesahuje oblast původní <xref:System.Windows.Controls.Primitives.Popup>. Pokud rastrový efekt nebo transformace vyžaduje více místa, můžete definovat okraje kolem <xref:System.Windows.Controls.Primitives.Popup> obsahu, aby bylo možné poskytnout další oblasti pro ovládací prvek.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Definování překryvného umístění  
 Umístíte automaticky otevíraného okna tak, že nastavíte <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> vlastnosti. Další informace najdete v tématu [chování při umístění automaticky otevíraného okna](popup-placement-behavior.md). Když <xref:System.Windows.Controls.Primitives.Popup> se zobrazí na obrazovce, je nepřemístí samotné Pokud přemístí svého nadřazeného objektu.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění automaticky otevíraného okna  
 Můžete přizpůsobit umístění <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku tak, že zadáte sady souřadnic, které jsou relativně k <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> místo, kam chcete <xref:System.Windows.Controls.Primitives.Popup> zobrazit.  
  
 Chcete-li přizpůsobit umístění, nastavte <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Potom definujte <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, který vrátí sadu bodů možná umístění a primární osy (v upřednostňovaném pořadí) pro <xref:System.Windows.Controls.Primitives.Popup>. Bod, který ukazuje největší část <xref:System.Windows.Controls.Primitives.Popup> se vybere automaticky. Příklad najdete v tématu [určení vlastního překryvného umístění](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Místní nabídka a vizuální strom  
 A <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek nemá vlastní vizuálního stromu; místo toho vrátí velikost 0 (nula) Pokud <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> metodu <xref:System.Windows.Controls.Primitives.Popup> je volána. Ale pokud nastavíte <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> vlastnost <xref:System.Windows.Controls.Primitives.Popup> k `true`, se vytvoří nové okno s vlastním vizuálního stromu. Nové okno obsahuje <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsah <xref:System.Windows.Controls.Primitives.Popup>. Šířka a výška ohraničení nové okno nemůže být větší než 75 procent šířky nebo výšky na obrazovce.  
  
 <xref:System.Windows.Controls.Primitives.Popup> Ovládací prvek udržuje odkaz na jeho <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsah jako logické podřízené. Nové okno Vytvoření, obsah <xref:System.Windows.Controls.Primitives.Popup> stane visual podřízená položka okna a zůstane logickým podřízeným <xref:System.Windows.Controls.Primitives.Popup>. Naopak <xref:System.Windows.Controls.Primitives.Popup> zůstává logický nadřazený prvek jeho <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsah.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Témata s postupy](popup-how-to-topics.md)
- [Témata s postupy](tooltip-how-to-topics.md)
