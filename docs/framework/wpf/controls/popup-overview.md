---
title: "Přehled překryvných objektů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96ee7b227d4e2ea5dfcb0b8870d77d03abf08db8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="popup-overview"></a>Přehled překryvných objektů
<xref:System.Windows.Controls.Primitives.Popup> Řízení poskytuje způsob, jak zobrazit obsah v samostatném okně, které překrývat aktuální okno aplikace relativně k určené souřadnice element nebo obrazovky. Toto téma představuje <xref:System.Windows.Controls.Primitives.Popup> řízení a poskytuje informace o jeho použití.  
  
 
  
<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Co je místní okno?  
 A <xref:System.Windows.Controls.Primitives.Popup> zobrazí obsah v samostatném okně relativně k prvku nebo bodu na obrazovce. Když <xref:System.Windows.Controls.Primitives.Popup> je viditelná, <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> je nastavena na `true`.  
  
> [!NOTE]
>  A <xref:System.Windows.Controls.Primitives.Popup> automaticky neotevře při přesunutí ukazatele myši jeho nadřazený objekt. Pokud chcete <xref:System.Windows.Controls.Primitives.Popup> Pokud chcete automaticky spustit, použijte <xref:System.Windows.Controls.ToolTip> nebo <xref:System.Windows.Controls.ToolTipService> třídy. Další informace najdete v tématu [popisek přehled](../../../../docs/framework/wpf/controls/tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Vytváření místní okno  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.Primitives.Popup> prvek, který je o podřízený prvek <xref:System.Windows.Controls.Button> ovládacího prvku. Protože <xref:System.Windows.Controls.Button> může mít pouze jeden podřízený element, umístí text pro tento příklad <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Primitives.Popup> ovládacích prvků do <xref:System.Windows.Controls.StackPanel>. Obsah <xref:System.Windows.Controls.Primitives.Popup> se zobrazí v <xref:System.Windows.Controls.TextBlock> řízení, které zobrazí jeho text v samostatném okně, které překrývat okna aplikace téměř související <xref:System.Windows.Controls.Button> ovládacího prvku.  
  
 [!code-xaml[PopupSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Ovládací prvky, které implementují místní okno  
 Můžete vytvořit <xref:System.Windows.Controls.Primitives.Popup> ovládacích prvků do jiných ovládacích prvků. Implementovat následující ovládací prvky <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek pro konkrétní účely:  
  
-   <xref:System.Windows.Controls.ToolTip>. Pokud chcete vytvořit popisek pro element, použijte <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ToolTipService> třídy. Další informace najdete v tématu [popisek přehled](../../../../docs/framework/wpf/controls/tooltip-overview.md).  
  
-   <xref:System.Windows.Controls.ContextMenu>. Pokud chcete vytvořit z kontextové nabídky pro element, použijte <xref:System.Windows.Controls.ContextMenu> ovládacího prvku. Další informace najdete v tématu [ContextMenu – přehled](../../../../docs/framework/wpf/controls/contextmenu-overview.md).  
  
-   <xref:System.Windows.Controls.ComboBox>. Pokud chcete vytvořit ovládacího prvku pro výběr s rozevíracím seznamu, který může být uvedené nebo skryté, použijte <xref:System.Windows.Controls.ComboBox> ovládacího prvku.  
  
-   <xref:System.Windows.Controls.Expander>. Pokud chcete vytvořit ovládacího prvku, který zobrazí hlavičku sbalitelné oblasti, který zobrazí obsah, použijte <xref:System.Windows.Controls.Expander> ovládacího prvku. Další informace najdete v tématu [Expander přehled](../../../../docs/framework/wpf/controls/expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Místní nabídka chování a vzhledu  
 <xref:System.Windows.Controls.Primitives.Popup> Řízení poskytuje funkce, které umožňuje přizpůsobit jeho chování a vzhledu. Například můžete nastavit otevření a zavření chování, animace, krytí a rastrový obrázek důsledky, a <xref:System.Windows.Controls.Primitives.Popup> velikost a umístění.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Otevření a zavření chování  
 A <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek zobrazí její obsah, když <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> je nastavena na `true`. Ve výchozím nastavení <xref:System.Windows.Controls.Primitives.Popup> zůstane otevřené až <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> je nastavena na `false`. Můžete však změnit výchozí chování nastavením <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> vlastnost `false`. Pokud tuto vlastnost nastavíte na `false`, <xref:System.Windows.Controls.Primitives.Popup> obsahu okna je zachycení myši. <xref:System.Windows.Controls.Primitives.Popup> Ztratí myši zachycení a zavře okno při výskytu události myši mimo <xref:System.Windows.Controls.Primitives.Popup> okno.  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened> a <xref:System.Windows.Controls.Primitives.Popup.Closed> události jsou vyvolány při <xref:System.Windows.Controls.Primitives.Popup> obsahu okno je otevřené nebo uzavřený.  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animace  
 <xref:System.Windows.Controls.Primitives.Popup> Ovládací prvek má integrovanou podporu pro animace, které jsou obvykle přidružené chování jako vysouvaly a snímku. Můžete zapnout na tyto animací nastavením <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> vlastnosti <xref:System.Windows.Controls.Primitives.PopupAnimation> hodnota výčtu. Pro <xref:System.Windows.Controls.Primitives.Popup> animací fungovala správně, je nutné nastavit <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> vlastnost `true`.  
  
 Můžete taky použít animace jako <xref:System.Windows.Media.Animation.Storyboard> k <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Krytí a rastrový obrázek efekty  
 <xref:System.Windows.UIElement.Opacity%2A> Vlastnost <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek nemá žádný vliv na jeho obsah. Ve výchozím nastavení <xref:System.Windows.Controls.Primitives.Popup> v okně obsah je plné krytí. Chcete-li vytvořit transparentní <xref:System.Windows.Controls.Primitives.Popup>, nastavte <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> vlastnost `true`.  
  
 Obsah <xref:System.Windows.Controls.Primitives.Popup> nedědí rastrový obrázek důsledky, jako například <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, přímo nastavit na <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek nebo na jakýkoli další prvek v okně nadřazené. Pro rastrový obrázek vliv na obsah <xref:System.Windows.Controls.Primitives.Popup>, je nutné nastavit vliv rastrový obrázek přímo na jeho obsah. Například pokud podřízeným <xref:System.Windows.Controls.Primitives.Popup> je <xref:System.Windows.Controls.StackPanel>, nastavení efektu rastrového obrázku na <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Velikost v automaticky otevřeném okně.  
 Ve výchozím nastavení <xref:System.Windows.Controls.Primitives.Popup> je automaticky velikost na jeho obsah. Když dojde k automatickou, některé efekty rastrového obrázku může skrýt, protože výchozí velikost oblasti obrazovky, který je definován pro <xref:System.Windows.Controls.Primitives.Popup> obsah neposkytuje dost místa pro rastrový obrázek důsledky pro zobrazení.  
  
 <xref:System.Windows.Controls.Primitives.Popup>obsah může být skryty také při nastavení <xref:System.Windows.UIElement.RenderTransform%2A> na obsah. V tomto scénáři může být skrytý obsah, pokud obsah transformovaných <xref:System.Windows.Controls.Primitives.Popup> přesahuje oblasti původní <xref:System.Windows.Controls.Primitives.Popup>. Pokud efekt rastrového obrázku nebo transformace vyžaduje více místa, můžete definovat okraj kolem <xref:System.Windows.Controls.Primitives.Popup> obsahu, aby bylo možné poskytnout další oblasti pro ovládací prvek.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Definování pozici automaticky otevřeném okně.  
 Místní okno můžete umístit nastavením <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> vlastnosti. Další informace najdete v tématu [chování místní umístění](../../../../docs/framework/wpf/controls/popup-placement-behavior.md). Když <xref:System.Windows.Controls.Primitives.Popup> se zobrazí na obrazovce ji není změnit umístění samotné pokud jeho nadřazený objekt je změnit jejich umístění.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění automaticky otevřeném okně.  
 Můžete přizpůsobit umístění <xref:System.Windows.Controls.Primitives.Popup> řízení zadáním sadu souřadnice, které jsou vzhledem k <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> místo <xref:System.Windows.Controls.Primitives.Popup> se objeví.  
  
 Chcete-li přizpůsobit umístění, nastavte <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Potom zadejte <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, který vrací sadu bodů možná umístění a primární osy (v upřednostňovaném pořadí) pro <xref:System.Windows.Controls.Primitives.Popup>. Bod, který ukazuje největší část <xref:System.Windows.Controls.Primitives.Popup> je automaticky vybrána. Příklad, naleznete v části [zadat vlastní místní pozici](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Místní a vizuálním stromu  
 A <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek nemá vlastní vizuálním stromu; místo toho vrátí velikost 0 (nula) Pokud <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> metodu pro <xref:System.Windows.Controls.Primitives.Popup> je volána. Ale pokud nastavíte <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> vlastnost <xref:System.Windows.Controls.Primitives.Popup> k `true`, se vytvoří nové okno s vlastní vizuálním stromu. Obsahuje nové okno <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsah <xref:System.Windows.Controls.Primitives.Popup>. Šířka a výška nové okno nemůže být větší než 75 procent šířky nebo výšky obrazovky.  
  
 <xref:System.Windows.Controls.Primitives.Popup> Řízení udržuje odkaz na jeho <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsah jako logické podřízené. Nové okno Vytvoření, obsah <xref:System.Windows.Controls.Primitives.Popup> stane visual podřízená okna a zůstane logické podřízeným <xref:System.Windows.Controls.Primitives.Popup>. Naopak <xref:System.Windows.Controls.Primitives.Popup> zůstává logické nadřazeného jeho <xref:System.Windows.Controls.Primitives.Popup.Child%2A> obsah.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Primitives.Popup>  
 <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>  
 <xref:System.Windows.Controls.Primitives.PlacementMode>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>  
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Postupy: témata](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [Postupy: témata](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
