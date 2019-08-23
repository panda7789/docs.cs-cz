---
title: Přehled překryvných objektů
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 7e6977737d362fd0df6321702bb8a1ac6cad66e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951433"
---
# <a name="popup-overview"></a>Přehled překryvných objektů
<xref:System.Windows.Controls.Primitives.Popup> Ovládací prvek poskytuje způsob zobrazení obsahu v samostatném okně, které je plovoucí v aktuálním okně aplikace vzhledem k určenému prvku nebo souřadnici obrazovky. Toto téma představuje <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek a poskytuje informace o jeho použití.  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Co je automaticky otevírané okno?  
 <xref:System.Windows.Controls.Primitives.Popup> Ovládací prvek zobrazí obsah v samostatném okně relativně k prvku nebo bodu na obrazovce. Když je viditelný <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> , vlastnost je nastavena na `true`. <xref:System.Windows.Controls.Primitives.Popup>  
  
> [!NOTE]
> A <xref:System.Windows.Controls.Primitives.Popup> automaticky se neotevře, když se ukazatel myši pohybuje nad svým nadřazeným objektem. Pokud chcete automaticky otevřít, <xref:System.Windows.Controls.ToolTip> použijte třídu nebo <xref:System.Windows.Controls.ToolTipService>. <xref:System.Windows.Controls.Primitives.Popup> Další informace najdete v tématu [Přehled tlačítek](tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Vytvoření překryvného okna  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek, který je podřízeným prvkem <xref:System.Windows.Controls.Button> ovládacího prvku. Vzhledem k <xref:System.Windows.Controls.Button> tomu, že může mít pouze jeden podřízený element, tento příklad umístí text <xref:System.Windows.Controls.Button> pro <xref:System.Windows.Controls.StackPanel>a <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky v. Obsah je <xref:System.Windows.Controls.Primitives.Popup> zobrazen <xref:System.Windows.Controls.TextBlock> v ovládacím prvku, který zobrazuje jeho text v samostatném okně, které se nachází v okně aplikace poblíž souvisejícího <xref:System.Windows.Controls.Button> ovládacího prvku.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Ovládací prvky, které implementují automaticky otevírané okno  
 Můžete sestavit <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky pro jiné ovládací prvky. Následující ovládací prvky implementují <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek pro konkrétní použití:  
  
- <xref:System.Windows.Controls.ToolTip>. Chcete-li vytvořit popis tlačítka pro prvek, použijte <xref:System.Windows.Controls.ToolTip> třídy a. <xref:System.Windows.Controls.ToolTipService> Další informace najdete v tématu [Přehled tlačítek](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Chcete-li vytvořit kontextovou nabídku pro prvek, použijte <xref:System.Windows.Controls.ContextMenu> ovládací prvek. Další informace najdete v tématu [Přehled](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Chcete-li vytvořit ovládací prvek výběru, který má rozevírací seznam, který lze zobrazit nebo skrýt, použijte <xref:System.Windows.Controls.ComboBox> ovládací prvek.  
  
- <xref:System.Windows.Controls.Expander>. Chcete-li vytvořit ovládací prvek, který zobrazuje hlavičku s sbalitelnou oblastí, která zobrazuje obsah, použijte <xref:System.Windows.Controls.Expander> ovládací prvek. Další informace najdete v tématu [Přehled rozšíření](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Chování a vzhled místního okna  
 <xref:System.Windows.Controls.Primitives.Popup> Ovládací prvek nabízí funkce, které vám umožní přizpůsobit jeho chování a vzhled. Můžete například nastavit otevřít a zavřít chování, animaci, krytí a rastrové efekty <xref:System.Windows.Controls.Primitives.Popup> a velikost a umístění.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Chování při otevření a zavření  
 Ovládací prvek zobrazí svůj obsah, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> Pokud je vlastnost nastavena na `true`hodnotu. <xref:System.Windows.Controls.Primitives.Popup> Ve výchozím nastavení <xref:System.Windows.Controls.Primitives.Popup> zůstane otevřené, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> dokud vlastnost není nastavena na `false`hodnotu. Výchozí chování však můžete změnit nastavením <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> vlastnosti na. `false` Když nastavíte tuto vlastnost na `false`, okno <xref:System.Windows.Controls.Primitives.Popup> obsahu bude mít zachycení myši. Ztratí zachycení myši a okno se zavře, když dojde k události myši <xref:System.Windows.Controls.Primitives.Popup> mimo okno. <xref:System.Windows.Controls.Primitives.Popup>  
  
 Události a jsou<xref:System.Windows.Controls.Primitives.Popup.Closed> vyvolány, když je okno obsahuotevřenonebozavřeno.<xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Opened>  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animace  
 <xref:System.Windows.Controls.Primitives.Popup> Ovládací prvek má vestavěnou podporu pro animace, které jsou obvykle spojeny s chováním, jako je například zmizení a přechod na další. Tyto animace můžete zapnout nastavením <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> vlastnosti <xref:System.Windows.Controls.Primitives.PopupAnimation> na hodnotu výčtu. Aby animace fungovaly správně, musíte <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> nastavit vlastnost na `true`. <xref:System.Windows.Controls.Primitives.Popup>  
  
 Můžete také použít animace jako <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.Primitives.Popup> u ovládacího prvku.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Neprůhlednost a bitmapové efekty  
 <xref:System.Windows.UIElement.Opacity%2A> Vlastnost<xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku nemá žádný vliv na jeho obsah. Ve výchozím nastavení <xref:System.Windows.Controls.Primitives.Popup> je okno obsahu neprůhledné. Chcete-li vytvořit <xref:System.Windows.Controls.Primitives.Popup>průhlednou, <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> nastavte vlastnost na `true`hodnotu.  
  
 Obsah objektu <xref:System.Windows.Controls.Primitives.Popup> nedědí rastrové efekty, <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>například, které přímo nastavíte na <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek nebo na jiný prvek v nadřazeném okně. Pro efekty rastrového obrázku, které se mají zobrazit <xref:System.Windows.Controls.Primitives.Popup>v obsahu a, je nutné nastavit efekt rastrového obrázku přímo na jeho obsah. Například pokud má podřízená položka <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.StackPanel>a, nastavte efekt rastrového obrázku na <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Velikost automaticky otevíraného okna  
 Ve výchozím nastavení <xref:System.Windows.Controls.Primitives.Popup> má automaticky velikost na svůj obsah. Pokud dojde k automatickému určení velikosti, mohou být některé efekty rastrového obrázku skryté, protože výchozí velikost oblasti obrazovky, která je <xref:System.Windows.Controls.Primitives.Popup> definována pro obsah, neposkytuje dostatek místa pro zobrazení rastrových efektů.  
  
 <xref:System.Windows.Controls.Primitives.Popup>obsah lze také zakrýt při nastavení <xref:System.Windows.UIElement.RenderTransform%2A> obsahu. V tomto scénáři může být nějaký obsah skrytý, pokud obsah transformované <xref:System.Windows.Controls.Primitives.Popup> překračuje oblast původní. <xref:System.Windows.Controls.Primitives.Popup> Pokud bitmapový efekt nebo transformace vyžaduje více místa, můžete definovat okraj kolem <xref:System.Windows.Controls.Primitives.Popup> obsahu, aby bylo možné poskytnout více prostoru pro ovládací prvek.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Definování umístění automaticky otevíraného okna  
 Místní <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nabídku můžete umístit nastavením vlastností, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> . Další informace najdete v tématu [chování při umisťování do místní nabídky](popup-placement-behavior.md). Když <xref:System.Windows.Controls.Primitives.Popup> se zobrazí na obrazovce, nedojde k přemístění, pokud je přemístění jeho nadřazeného objektu.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění automaticky otevíraných oken  
 Umístění <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku lze přizpůsobit zadáním sady souřadnic, které jsou relativní <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> k umístění, kde <xref:System.Windows.Controls.Primitives.Popup> se má objevit.  
  
 Chcete-li přizpůsobit umístění, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nastavte vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>na hodnotu. Pak definujte <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, který vrací sadu možných bodů umístění a primární osy (v pořadí podle priority) <xref:System.Windows.Controls.Primitives.Popup>pro. Bod, který zobrazuje největší část, <xref:System.Windows.Controls.Primitives.Popup> je automaticky vybrán. Příklad naleznete v tématu [určení vlastní místní pozice](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Automaticky otevírané okno a vizuální strom  
 Ovládací prvek nemá svůj vlastní vizuální strom; namísto toho vrátí velikost 0 (nula) <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> při volání metody <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup> Nicméně pokud nastavíte <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> <xref:System.Windows.Controls.Primitives.Popup> vlastnost na `true`, je vytvořeno nové okno s vlastním vizuálním stromem. Nové okno obsahuje <xref:System.Windows.Controls.Primitives.Popup.Child%2A> <xref:System.Windows.Controls.Primitives.Popup>obsah. Šířka a výška nového okna nemůže být větší než 75 procent šířky nebo výšky obrazovky.  
  
 Ovládací prvek udržuje odkaz na jeho <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsah jako logickou podřízenou položku. <xref:System.Windows.Controls.Primitives.Popup> Když je vytvořeno nové okno, obsah prvku <xref:System.Windows.Controls.Primitives.Popup> se stal vizuálním podřízeným oknem okna a zůstane logickou <xref:System.Windows.Controls.Primitives.Popup>podřízenou položkou. Naopak, <xref:System.Windows.Controls.Primitives.Popup> zůstává logickým nadřazeným objektem jeho <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsahu.  
  
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
