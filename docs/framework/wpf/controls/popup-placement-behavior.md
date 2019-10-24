---
title: Chování při umístění překryvného objektu
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: ca984aa724cf3f076d6073aa8b8179abfb91d26c
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "69951737"
---
# <a name="popup-placement-behavior"></a>Chování při umístění překryvného objektu
Ovládací prvek <xref:System.Windows.Controls.Primitives.Popup> zobrazí obsah v samostatném okně, které je v aplikaci plovoucí. Můžete určit pozici <xref:System.Windows.Controls.Primitives.Popup> relativní k ovládacímu prvku, myši nebo obrazovce pomocí vlastností <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>.  Tyto vlastnosti společně poskytují flexibilitu při určování pozice <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
> Třídy <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ContextMenu> také definují tyto pět vlastností a chovají se podobně.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Umístění místní nabídky  
 Umístění <xref:System.Windows.Controls.Primitives.Popup> může být relativní vzhledem k <xref:System.Windows.UIElement> nebo na celou obrazovku.  Následující příklad vytvoří čtyři <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky, které jsou relativní k <xref:System.Windows.UIElement> – v tomto případě obrázek. U všech ovládacích prvků <xref:System.Windows.Controls.Primitives.Popup> je vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nastavena na hodnotu `image1`, ale každý <xref:System.Windows.Controls.Primitives.Popup> má pro vlastnost umístění jinou hodnotu.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Následující ilustrace znázorňuje obrázek a <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky  
  
 ![Obrázek se čtyřmi ovládacími prvky místní nabídky](./media/popup-placement-behavior/popup-placement-intro.png "Obrázek se čtyřmi automaticky otevíraných oken")    
  
 Tento jednoduchý příklad ukazuje, jak nastavit vlastnosti <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, ale pomocí vlastností <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> máte ještě větší kontrolu nad tím, kde je <xref:System.Windows.Controls.Primitives.Popup> umístěn.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definice podmínek: anatomie místní nabídky  
 Následující výrazy jsou užitečné při povýšení vlastností <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> mezi sebou a <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Cílový objekt  
  
- Cílová oblast  
  
- Cílový původ  
  
- Automaticky otevírané okno – bod zarovnání  
  
 Tyto výrazy poskytují pohodlný způsob, jak odkazovat na různé aspekty <xref:System.Windows.Controls.Primitives.Popup> a na ovládacím prvku, ke kterému je přidružen.  
  
### <a name="target-object"></a>Cílový objekt  
 *Cílový objekt* je prvek, ke kterému je <xref:System.Windows.Controls.Primitives.Popup> přidružena. Pokud je nastavena vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, určuje cílový objekt.  Pokud není nastavena <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup> má nadřazený, nadřazený objekt je cílový objekt.  Pokud není k dispozici žádná <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> hodnota ani žádná nadřazená položka, neexistuje žádný cílový objekt a <xref:System.Windows.Controls.Primitives.Popup> je umístěn vzhledem k obrazovce.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup>, který je podřízenou položkou <xref:System.Windows.Controls.Canvas>.  V tomto příkladu není nastavena vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> v <xref:System.Windows.Controls.Primitives.Popup>. Výchozí hodnota pro <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, takže se <xref:System.Windows.Controls.Primitives.Popup> zobrazí pod <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> je umístěn vzhledem k <xref:System.Windows.Controls.Canvas>.  
  
 ![Místní ovládací prvek bez PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Automaticky otevíraná okna bez PlacementTarget.")  

 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup>, která je podřízenou položkou <xref:System.Windows.Controls.Canvas>, ale tentokrát je <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nastavena na `ellipse1`, takže se místní nabídka zobrazí pod <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> je umístěn vzhledem k <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Automaticky otevírané okno, které se umístí vzhledem k elipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Automaticky otevírané okno s PlacementTarget")    
  
> [!NOTE]
> Pro <xref:System.Windows.Controls.ToolTip> je výchozí hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Pro <xref:System.Windows.Controls.ContextMenu> je výchozí hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Tyto hodnoty jsou vysvětleny později v tématu Jak vlastnosti pracují dohromady.  
  
### <a name="target-area"></a>Cílová oblast  
 *Cílová oblast* je oblast na obrazovce, ke které je <xref:System.Windows.Controls.Primitives.Popup> relativní. V předchozích příkladech je <xref:System.Windows.Controls.Primitives.Popup> zarovnán s mezemi cílového objektu, ale v některých případech je <xref:System.Windows.Controls.Primitives.Popup> zarovnána k ostatním hranicím, i když má <xref:System.Windows.Controls.Primitives.Popup> cílový objekt.  Pokud je nastavena vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, cílová oblast se liší od hranic cílového objektu.  
  
 Následující příklad vytvoří dva objekty <xref:System.Windows.Controls.Canvas>, každý z nich obsahující <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Controls.Primitives.Popup>.  V obou případech je cílovým objektem <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>. @No__t_0 v prvním <xref:System.Windows.Controls.Canvas> má <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> sadu s vlastnostmi <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A> a <xref:System.Windows.Rect.Height%2A> nastavenými na 50, 50, 50 a 100 v uvedeném pořadí. @No__t_0 ve druhém <xref:System.Windows.Controls.Canvas> nemá <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> sadu.  V důsledku toho je první <xref:System.Windows.Controls.Primitives.Popup> umístěn pod <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> a druhý <xref:System.Windows.Controls.Primitives.Popup> je umístěn pod <xref:System.Windows.Controls.Canvas>. Každý <xref:System.Windows.Controls.Canvas> obsahuje také <xref:System.Windows.Shapes.Rectangle>, který má stejné meze jako <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> prvního <xref:System.Windows.Controls.Primitives.Popup>.  Všimněte si, že <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nevytváří viditelný element v aplikaci; příklad vytvoří <xref:System.Windows.Shapes.Rectangle> reprezentující <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Následující ilustrace znázorňuje výsledek předchozího příkladu.  
  
 ![Automaticky otevírané okno s PlacementRectangle a bez něj](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Automaticky otevírané okno s PlacementRectangle a bez něj.")  

### <a name="target-origin-and-popup-alignment-point"></a>Počátek cíle a bod zarovnání automaticky otevíraného okna  
 *Cílový zdroj* a *bod zarovnání místní nabídky* jsou referenční body v cílové oblasti a v místní nabídce, které se používají k umístění. K posunu automaticky otevírané okno z cílové oblasti můžete použít vlastnosti <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>.  @No__t_0 a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> jsou relativní vzhledem k cílovému zdroji a bodu zarovnání automaticky otevíraného okna. Hodnota vlastnosti <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> určuje, kde se nachází cílový počátek a bod zarovnání místní nabídky.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> a nastaví <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a vlastnosti <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> na hodnotu 20.  Vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (výchozí), takže cílovým zdrojem je pravý dolní roh cílové oblasti a bod zarovnání automaticky otevíraného okna je levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Následující ilustrace znázorňuje výsledek předchozího příkladu.  
  
 ![Umístění automaticky otevíraného okna s cílovým počátečním bodem zarovnání](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Automaticky otevíraná okna s HorizontalOffset a VerticalOffset.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Jak vlastnosti spolupracují  
 Hodnoty <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je potřeba zvážit společně pro zjištění správné cílové oblasti, cílového původu a bodu zarovnání automaticky otevíraného okna.  Například pokud je hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, neexistuje žádný cílový objekt, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je ignorována a cílová oblast je hranice ukazatele myši. Na druhé straně, pokud je <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazená položka určuje cílový objekt a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> určuje cílovou oblast.  
  
 Následující tabulka popisuje cílový objekt, cílovou oblast, cílový původ a místní bod zarovnání a určuje, zda jsou <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> použity pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu výčtu.  
  
|PlacementMode|Cílový objekt|Cílová oblast|Cílový původ|Automaticky otevírané okno – bod zarovnání|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Nelze použít. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Obrazovka nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k obrazovce.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Nelze použít. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Obrazovka nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k obrazovce.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený objekt.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k cílovému objektu.|Levý dolní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený objekt.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k cílovému objektu.|Střed cílové oblasti|Střed <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený objekt.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k cílovému objektu.|Definováno <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Definováno <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený objekt.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Pravý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Nelze použít. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Hranice ukazatele myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ignoruje.|Levý dolní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Nelze použít. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Hranice ukazatele myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ignoruje.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený objekt.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený objekt.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený objekt.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k cílovému objektu.|Pravý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený objekt.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavena.  @No__t_0 je relativní vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Levý dolní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Následující ilustrace znázorňují <xref:System.Windows.Controls.Primitives.Popup>, cílovou oblast, cílový původ a bod zarovnání místní nabídky pro každou hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode>. V každém obrázku je cílová oblast žlutá a <xref:System.Windows.Controls.Primitives.Popup> je modrá.  
  
 ![Automaticky otevírané okno s absolutním nebo AbsolutePointm umístěním](./media/popup-placement-behavior/popup-placement-absolute.png "Umístění je absolutní nebo AbsolutePoint.")    
  
 ![Automaticky otevírané okno s nejnižším umístěním](./media/popup-placement-behavior/popup-placement-bottom.png "Umístění je dole.")   
  
 ![Automaticky otevírané okno s Centrovým umístěním](./media/popup-placement-behavior/popup-placement-center.png "Umístění je na střed.")    
  
 ![Automaticky otevírané okno s levým umístěním](./media/popup-placement-behavior/popup-placement-left.png "Umístění je ponecháno.")   
  
 ![Místní nabídka s umístěním myši](./media/popup-placement-behavior/popup-placement-mouse.png "Umístění je myš.")  
  
 ![Automaticky otevírané okno s umístěním MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Umístění je MousePoint.")  
  
 ![Automaticky otevírané okno s relativním nebo RelativePointm umístěním](./media/popup-placement-behavior/popup-placement-relative.png "Umístění je relativní nebo RelativePoint.")    
  
 ![Místní nabídka se správným umístěním](./media/popup-placement-behavior/popup-placement-right.png "Umístění je pravé.")    
  
 ![Automaticky otevírané okno s největším umístěním](./media/popup-placement-behavior/popup-placement-top.png "Umístění je horní.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Když se v překryvném okně objeví okraj obrazovky  
 Z bezpečnostních důvodů nemůže být <xref:System.Windows.Controls.Primitives.Popup> skrytý na okraji obrazovky. Jedna z následujících tří akcí se stane, když <xref:System.Windows.Controls.Primitives.Popup> narazí na okraj obrazovky:  
  
- Místní okno se znovu zarovná s okrajem obrazovky, které by <xref:System.Windows.Controls.Primitives.Popup> zakrývat.  
  
- Automaticky otevíraná okna používá jiný bod zarovnání.  
  
- Automaticky otevíraná okna používá jiný cílový zdroj a bod zarovnání místní nabídky.  
  
 Tyto možnosti jsou podrobněji popsané dále v této části.  
  
 Chování <xref:System.Windows.Controls.Primitives.Popup>, když dojde k okraji obrazovky, závisí na hodnotě vlastnosti <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a na okraji obrazovky, na které se automaticky otevíraná okna setkávají. Následující tabulka shrnuje chování, když <xref:System.Windows.Controls.Primitives.Popup> narazí na okraj obrazovky pro každou hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
|PlacementMode|Horní hrana|Dolní hrana|Levý okraj|Pravá hrana|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Zarovná se k hornímu okraji.|Bod zarovnání automaticky otevíraného okna se změní na levý dolní roh <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Automaticky otevírané okno se změní v pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Zarovná se k hornímu okraji.|Cílový počátek se změní v levém horním rohu cílové oblasti a automaticky se změní bod zarovnání v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Cílový počátek se změní v pravém horním rohu cílové oblasti a automaticky se změní bod zarovnání v levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Zarovná se k hornímu okraji.|Cílový počátek se změní v levém horním rohu cílové oblasti (hranice ukazatele myši) a bod zarovnání automaticky otevíraného okna se změní na levý dolní roh <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Zarovná se k hornímu okraji.|Bod zarovnání automaticky otevíraného okna se změní na levý dolní roh <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Automaticky otevírané okno se změní v pravém horním rohu automaticky otevíraného okna.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Zarovná se k hornímu okraji.|Bod zarovnání automaticky otevíraného okna se změní na levý dolní roh <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Automaticky otevírané okno se změní v pravém horním rohu automaticky otevíraného okna.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Cílový počátek se změní v levém horním rohu cílové oblasti a automaticky se změní bod zarovnání v pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Cílový počátek se změní do levého dolního rohu cílové oblasti a automaticky se změní bod zarovnání v levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>. V důsledku toho je stejná jako při <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
  
### <a name="aligning-to-the-screen-edge"></a>Zarovnání na okraj obrazovky  
 @No__t_0 lze zarovnat k okraji obrazovky přemístěním sebe, aby se na obrazovce zobrazil celý <xref:System.Windows.Controls.Primitives.Popup>.  Pokud k tomu dojde, může se vzdálenost mezi cílovým počátkem a bodem zarovnání místní nabídky lišit od hodnot <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center> nebo <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> se zarovnává na všechny okraje obrazovky.  Předpokládejme například, že <xref:System.Windows.Controls.Primitives.Popup> má <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nastaveno na <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> nastavte na 100.  Pokud spodní okraj obrazovky skryje všechny nebo některé <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup> sám sebe umístí podél dolního okraje obrazovky a svislou vzdálenost mezi cílovým zdrojem a bodem zarovnání místní nabídky je menší než 100. To ukazuje následující obrázek.  
  
 ![Automaticky otevírané okno, které se zarovnává na okraj obrazovky](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Automaticky otevírané okno se zarovná k okraji obrazovky.")    
  
### <a name="changing-the-popup-alignment-point"></a>Změna bodu zarovnání automaticky otevíraného okna  
 Pokud je <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> nebo <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, změní se bod zarovnání automaticky, když se v překryvném okně narazí na spodní nebo pravé hrany obrazovky.  
  
 Následující obrázek ukazuje, že když se dolní okraj obrazovky skryje celý <xref:System.Windows.Controls.Primitives.Popup>, je bod zarovnání automaticky otevírané okno v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu dolní hrany obrazovky](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "V překryvném okně dojde k dolnímu okraji obrazovky a změna bodu zarovnání automaticky otevíraného okna.")  

 Následující obrázek ukazuje, že pokud je <xref:System.Windows.Controls.Primitives.Popup> skrytý okrajem obrazovky, je bod zarovnání automaticky otevíraného okna v pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání pro místní okno z důvodu okraje obrazovky](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "V překryvném okně dojde k pravému okraji obrazovky a změna bodu zarovnání automaticky otevíraného okna.")    
  
 Pokud <xref:System.Windows.Controls.Primitives.Popup> narazí na dolní a pravý okraj obrazovky, je bod zarovnání automaticky otevíraného okna v pravém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Změna cílového zdroje a bodu zarovnání automaticky otevíraného okna  
 Pokud je <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right> nebo <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, změní se cílový počátek a bod zarovnání automaticky, pokud je zjištěna určitá hrana obrazovky.  Okraj obrazovky, který způsobuje změnu pozice, závisí na hodnotě <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
 Následující obrázek ukazuje, že když je <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> a <xref:System.Windows.Controls.Primitives.Popup> narazí na okraj spodní obrazovky, cílovým zdrojem je levý horní roh cílové oblasti a bod zarovnání místní nabídky je levý dolní roh <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu dolní hrany obrazovky](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Umístění je dolní a v překryvném okně dojde k dolnímu okraji obrazovky.")    
  
 Následující obrázek ukazuje, že když je <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Left> a <xref:System.Windows.Controls.Primitives.Popup> narazí na levý okraj obrazovky, cílovým zdrojem je pravý horní roh cílové oblasti a bod zarovnání místní nabídky je v levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu levého okraje obrazovky](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Umístění je ponecháno a automaticky otevírané okno narazí na levý okraj obrazovky.")  
  
 Následující obrázek ukazuje, že když je <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Right> a <xref:System.Windows.Controls.Primitives.Popup> narazí na okraj pravé obrazovky, cílovým zdrojem je levý horní roh cílové oblasti a bod zarovnání místní nabídky je pravý horní roh <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu pravého okraje obrazovky](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Umístění je napravo a v překryvném okně dojde k pravému okraji obrazovky.")  

 Následující obrázek ukazuje, že když je <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Top> a <xref:System.Windows.Controls.Primitives.Popup> narazí na okraj horní obrazovky, cílovým zdrojem je levý dolní roh cílové oblasti a bod zarovnání místní nabídky je levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu horní hrany obrazovky](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Umístění je horní a v překryvném okně dojde k hornímu okraji obrazovky.")  
  
 Následující obrázek ukazuje, že když je <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> a <xref:System.Windows.Controls.Primitives.Popup> narazí na okraj spodní obrazovky, cílovým zdrojem je levý horní roh cílové oblasti (meze ukazatele myši) a bod zarovnání místní nabídky je v levém dolním rohu. roh <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nový bod zarovnání v důsledku myši poblíž okraje obrazovky](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Umístění je myš a automaticky otevírané okno narazí na spodní okraj obrazovky.")    
  
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění automaticky otevíraných oken  
 Nastavením vlastnosti <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> můžete přizpůsobit cílový počátek a bod zarovnání místní nabídky. Pak definujte delegáta <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>, který vrací sadu možných bodů umístění a primární osy (v pořadí podle priority) pro <xref:System.Windows.Controls.Primitives.Popup>. Je vybrán bod, který zobrazuje největší část <xref:System.Windows.Controls.Primitives.Popup>.  Pozice <xref:System.Windows.Controls.Primitives.Popup> se automaticky upraví, pokud je <xref:System.Windows.Controls.Primitives.Popup> na okraji obrazovky skrytá. Příklad naleznete v tématu [určení vlastní místní pozice](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Viz také:

- [Ukázka umístění místní nabídky](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
