---
title: Chování při umístění překryvného objektu
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: a84ff7def944e1a037f4c26611e33de93ed9861e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650762"
---
# <a name="popup-placement-behavior"></a>Chování při umístění překryvného objektu
A <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek zobrazí obsah v samostatném okně, které čísel s plovoucí čárkou selhání aplikace. Můžete zadat umístění <xref:System.Windows.Controls.Primitives.Popup> vzhledem k ovládacího prvku, myši nebo na obrazovce s použitím <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vlastnosti.  Tyto vlastnosti spolupracují a poskytují flexibilitu v určeném umístění <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ContextMenu> třídy také definovat těchto pět vlastností a chovají se podobně.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Umístění automaticky otevíraného okna  
 Umístění <xref:System.Windows.Controls.Primitives.Popup> může být vzhledem k <xref:System.Windows.UIElement> nebo na celou obrazovku.  Následující příklad vytvoří čtyři <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky, které jsou relativně k <xref:System.Windows.UIElement>– v tomto případě bitovou kopii. Všechny <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky mají <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> vlastnost nastavena na hodnotu `image1`, ale každý <xref:System.Windows.Controls.Primitives.Popup> má jinou hodnotu pro vlastnost umístění.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Následující obrázek znázorňuje obrázek a <xref:System.Windows.Controls.Primitives.Popup> ovládacích prvků  
  
 ![Obrázek s čtyři překryvných ovládacích prvků](./media/popup-placement-behavior/popup-placement-intro.png "Image pomocí čtyř automaticky otevíraná okna")    
  
 Tento jednoduchý příklad ukazuje, jak nastavit <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnosti, ale pomocí <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vlastnosti, máte ještě větší kontrolu nad where <xref:System.Windows.Controls.Primitives.Popup> je umístěn.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definice podmínek: Anatomie automaticky otevíraného okna  
 Následující termíny jsou užitečné pro pochopení způsobu <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vzájemně souvisí vlastnosti a <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Cílový objekt  
  
- Cílovou oblast  
  
- Cíl původu  
  
- Bod zarovnání automaticky otevíraného okna  
  
 Tyto podmínky poskytují pohodlný způsob, jak odkazovat na různé aspekty <xref:System.Windows.Controls.Primitives.Popup> a ovládací prvek, který je přidružený.  
  
### <a name="target-object"></a>Cílový objekt  
 *Cílový objekt* je prvek, který <xref:System.Windows.Controls.Primitives.Popup> je přidružený. Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je hodnota nastavena, určuje cílový objekt.  Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> není nastavena a <xref:System.Windows.Controls.Primitives.Popup> má nadřazenou položku, nadřazený prvek je cílový objekt.  Pokud neexistuje žádné <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> hodnotu a žádný nadřazený objekt, neexistuje žádný cílové objektů a <xref:System.Windows.Controls.Primitives.Popup> je umístěn vzhledem k obrazovce.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> , který je podřízený <xref:System.Windows.Controls.Canvas>.  V příkladu nenastaví <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> vlastnost <xref:System.Windows.Controls.Primitives.Popup>. Výchozí hodnota pro <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, takže <xref:System.Windows.Controls.Primitives.Popup> se zobrazí pod <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> relativně k umisťovanému <xref:System.Windows.Controls.Canvas>.  
  
 ![Ovládací prvek popup PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "automaticky otevírané okno PlacementTarget.")  

 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> , který je podřízený <xref:System.Windows.Controls.Canvas>, tentokrát ale <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je nastavena na `ellipse1`, takže se automaticky otevírané okno se zobrazí pod <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> relativně k umisťovanému <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Automaticky otevírané okno umístěn vzhledem k Elipsa](./media/popup-placement-behavior/popup-placement-with-placement-target.png "automaticky otevírané okno s PlacementTarget")    
  
> [!NOTE]
>  Pro <xref:System.Windows.Controls.ToolTip>, výchozí hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Pro <xref:System.Windows.Controls.ContextMenu>, výchozí hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Tyto hodnoty jsou vysvětlené později v "Jak vlastnosti spolupracují."  
  
### <a name="target-area"></a>Cílovou oblast  
 *Cílové oblasti* je oblast na obrazovce, která <xref:System.Windows.Controls.Primitives.Popup> je vzhledem k. V předchozích příkladech <xref:System.Windows.Controls.Primitives.Popup> je v souladu s hranice cílového objektu, ale v některých případech <xref:System.Windows.Controls.Primitives.Popup> zarovnán do další hranice i v případě <xref:System.Windows.Controls.Primitives.Popup> je cílový objekt.  Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je hodnota nastavena, cílová oblast se liší od hranice cílového objektu.  
  
 Následující příklad vytvoří dva <xref:System.Windows.Controls.Canvas> objekty, každý z nich obsahující <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Controls.Primitives.Popup>.  V obou případech cílový objekt pro <xref:System.Windows.Controls.Primitives.Popup> je <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Controls.Primitives.Popup> v prvním <xref:System.Windows.Controls.Canvas> má <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nastavte s jeho <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, a <xref:System.Windows.Rect.Height%2A> vlastnosti nastavené na 50, 50, 50 a 100, v uvedeném pořadí. <xref:System.Windows.Controls.Primitives.Popup> Ve druhém <xref:System.Windows.Controls.Canvas> nemá <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nastavit.  V důsledku toho první <xref:System.Windows.Controls.Primitives.Popup> je umístěno pod <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> a druhá <xref:System.Windows.Controls.Primitives.Popup> je umístěno pod <xref:System.Windows.Controls.Canvas>. Každý <xref:System.Windows.Controls.Canvas> obsahuje také <xref:System.Windows.Shapes.Rectangle> , který má stejné hranice jako <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> poprvé <xref:System.Windows.Controls.Primitives.Popup>.  Všimněte si, že <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nevytvoří prvek viditelný v aplikaci, v příkladu se vytvoří <xref:System.Windows.Shapes.Rectangle> znázornit <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Následující obrázek ukazuje výsledek v předchozím příkladu.  
  
 ![Automaticky otevírané okno a nemusíte PlacementRectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "automaticky otevírané okno a nemusíte PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Cílové umístění a bod zarovnání automaticky otevíraného okna  
 *Cílit na počátku* a *bod zarovnání automaticky otevíraného okna* jsou referenční body v cílové oblasti a automaticky otevírané okno, v uvedeném pořadí, které se používají pro umístění. Můžete použít <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vlastnosti pozici automaticky otevíraného okna v cílové oblasti.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> jsou relativní vzhledem k cílové umístění a bod zarovnání automaticky otevíraného okna. Hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost určuje, kde se nachází cílový bod zarovnání původu a automaticky otevírané okno.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> a nastaví <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vlastností do 20.  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (výchozí), tak je cíl zdrojem levého dolního rohu cílovou oblast a bod zarovnání automaticky otevíraného okna je levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Následující obrázek ukazuje výsledek v předchozím příkladu.  
  
 ![Umístění automaticky otevíraného okna s cílový bod zarovnání původu](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "automaticky otevírané okno s HorizontalOffset a VerticalOffset.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Jak vlastnosti spolupracují  
 Hodnoty <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> musí být společně zvažovány zjistěte správnou cílovou oblast, cíl původu a bod zarovnání automaticky otevíraného okna.  Například pokud hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, neexistuje žádný cílové objektů <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ignoruje, a cílovou oblast je hranice ukazatel myši. Na druhé straně Pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené Určuje cílový objekt a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Určuje cílovou oblast.  
  
 Následující tabulka popisuje cílový objekt, cílovou oblast, cíl původu a bod zarovnání automaticky otevíraného okna a označuje, zda <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se používají pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnota výčtu.  
  
|PlacementMode|Cílový objekt|Cílovou oblast|Cíl původu|Bod zarovnání automaticky otevíraného okna|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Není k dispozici. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Na obrazovce nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k obrazovce.|Levém horním rohu v cílové oblasti.|Levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Není k dispozici. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Na obrazovce nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k obrazovce.|Levém horním rohu v cílové oblasti.|Levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílového objektu.|Levého dolního rohu cílovou oblast.|Levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílového objektu.|Center cílovou oblast.|Střed <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílového objektu.|Určené <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Určené <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílového objektu.|Levém horním rohu v cílové oblasti.|Pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Není k dispozici. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Hranice ukazatel myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ignoruje.|Levého dolního rohu cílovou oblast.|Levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Není k dispozici. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Hranice ukazatel myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ignoruje.|Levém horním rohu v cílové oblasti.|Levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílového objektu.|Levém horním rohu v cílové oblasti.|Levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílového objektu.|Levém horním rohu v cílové oblasti.|Levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílového objektu.|Pravém horním rohu v cílové oblasti.|Levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílového objektu.|Levém horním rohu v cílové oblasti.|Dolní části levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Následující ilustrace <xref:System.Windows.Controls.Primitives.Popup>, cílovou oblast, cíl původu a zarovnání automaticky otevíraného okna bodů pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu. Každý obrázek je žlutý, cílové oblasti a <xref:System.Windows.Controls.Primitives.Popup> modrá.  
  
 ![Automaticky otevírané okno s absolutní nebo AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "umístění je absolutní nebo AbsolutePoint.")    
  
 ![Automaticky otevírané okno s dolní umístění](./media/popup-placement-behavior/popup-placement-bottom.png "umístění je dole.")   
  
 ![Automaticky otevírané okno s Center umístění](./media/popup-placement-behavior/popup-placement-center.png "umístění je System Center.")    
  
 ![Automaticky otevírané okno s vlevo umístění](./media/popup-placement-behavior/popup-placement-left.png "umístění je vlevo.")   
  
 ![Automaticky otevírané okno s umístění myši](./media/popup-placement-behavior/popup-placement-mouse.png "umístění je myši.")  
  
 ![Automaticky otevírané okno s MousePoint umístění](./media/popup-placement-behavior/popup-placement-mousepoint.png "MousePoint je umístění.")  
  
 ![Automaticky otevírané okno s relativní nebo RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "umístění je relativní nebo RelativePoint.")    
  
 ![Automaticky otevírané okno s správné umístění](./media/popup-placement-behavior/popup-placement-right.png "umístění je vpravo.")    
  
 ![Automaticky otevírané okno s nejvyšší umístění](./media/popup-placement-behavior/popup-placement-top.png "umístění je na nejvyšší úrovni.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Pokud automaticky otevírané okno nalezne okrajem obrazovky  
 Z bezpečnostních důvodů <xref:System.Windows.Controls.Primitives.Popup> nemůže být skryty pomocí okraji obrazovky. Jeden z následujících tří se stane, když <xref:System.Windows.Controls.Primitives.Popup> zaznamená okraji obrazovky:  
  
- Automaticky otevírané okno změněné zarovnání samotné okrajem obrazovky, který by překrývat <xref:System.Windows.Controls.Primitives.Popup>.  
  
- Automaticky otevírané okno používá bod zarovnání různých automaticky otevíraného okna.  
  
- Automaticky otevírané okno používá bod jiné cílové umístění a automaticky otevírané okno zarovnání.  
  
 Tyto možnosti jsou popsány dále později v této části.  
  
 Chování <xref:System.Windows.Controls.Primitives.Popup> Pokud se setká s okraji obrazovky závisí na hodnotě <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost a které obrazovky edge dojde automaticky otevíraného okna. Následující tabulka shrnuje chování při <xref:System.Windows.Controls.Primitives.Popup> zaznamená okraji obrazovky pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu.  
  
|PlacementMode|Horní okraj|Dolní okraj|Levý okraj|Pravý okraj|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Zarovnán podle levé hrany.|Zarovnán podle pravé hrany.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Zarovnává horní okraj.|Do levého dolního rohu změní bod zarovnání automaticky otevíraného okna <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnán podle levé hrany.|Bod zarovnání automaticky otevíraného okna změny v pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Zarovnává horní okraj.|Cíl původu změny do levého horního rohu cílovou oblast a bod zarovnání automaticky otevíraného okna změny v dolní části levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnán podle levé hrany.|Zarovnán podle pravé hrany.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Zarovnán podle levé hrany.|Zarovnán podle pravé hrany.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Původní cílový změny v pravém horním rohu cílovou oblast a bod zarovnání automaticky otevíraného okna změny do levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnán podle pravé hrany.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Zarovnává horní okraj.|Cíl původu změny do levého horního rohu cílovou oblast (hranice ukazatel myši) a bod zarovnání automaticky otevíraného okna změny v dolní části levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnán podle levé hrany.|Zarovnán podle pravé hrany.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Zarovnává horní okraj.|Do levého dolního rohu změní bod zarovnání automaticky otevíraného okna <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnán podle levé hrany.|Zarovnání automaticky otevíraného okna změny přejděte pravém horním rohu automaticky otevíraného okna.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Zarovnán podle levé hrany.|Zarovnán podle pravé hrany.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Zarovnává horní okraj.|Do levého dolního rohu změní bod zarovnání automaticky otevíraného okna <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnán podle levé hrany.|Zarovnání automaticky otevíraného okna změny přejděte pravém horním rohu automaticky otevíraného okna.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Zarovnán podle levé hrany.|Cíl původu změny do levého horního rohu cílovou oblast a bod zarovnání automaticky otevíraného okna změny v pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Cíl původu změny do levého dolního rohu cílovou oblast a bod zarovnání automaticky otevíraného okna změny do levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>. V důsledku toho jde o stejný jako při <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Zarovnává dolní okraj.|Zarovnán podle levé hrany.|Zarovnán podle pravé hrany.|  
  
### <a name="aligning-to-the-screen-edge"></a>Zarovnání na okraji obrazovky  
 A <xref:System.Windows.Controls.Primitives.Popup> dokáže sladit k okraji obrazovky pomocí samotného přemístění tak celý <xref:System.Windows.Controls.Primitives.Popup> je viditelný na obrazovce.  V tomto případě vzdálenost mezi cílový bod zarovnání původu a automaticky otevírané okno se mohou lišit od hodnoty <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, nebo <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> zarovná samotné každý okraji obrazovky.  Například předpokládejme, že <xref:System.Windows.Controls.Primitives.Popup> má <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> nastavena na hodnotu 100.  Pokud jsou dolní okraje obrazovky skryje všechny nebo část <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup> přemístí samotné podél dolního okraje obrazovky a svislou vzdálenost mezi cílové umístění a automaticky otevírané okno bod zarovnání je menší než 100. Následující obrázek ukazuje to.  
  
 ![Automaticky otevírané okno, které Zarovná okraje obrazovky](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "automaticky otevírané okno nastavuje zarovnání na hranu obrazovky.")    
  
### <a name="changing-the-popup-alignment-point"></a>Změna bodu zarovnání automaticky otevíraného okna  
 Pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, nebo <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, při pravého nebo dolního okraje pravé obrazovky, zaznamená se automaticky otevírané okno se změní bod zarovnání automaticky otevíraného okna.  
  
 Následující obrázek ukazuje, že když dolnímu okraji obrazovky skryje všechny nebo část <xref:System.Windows.Controls.Primitives.Popup>, bod zarovnání automaticky otevíraného okna je dolní části levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu dolnímu okraji obrazovky](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "automaticky otevírané okno, zaznamená dolního okraje obrazovky a změní bod zarovnání automaticky otevíraného okna.")  

 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> je skrytý okraje pravé obrazovky bod zarovnání automaticky otevíraného okna je pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání automaticky otevíraného okna z důvodu okraji obrazovky](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "automaticky otevírané okno, zaznamená pravého okraje obrazovky a změní bod zarovnání automaticky otevíraného okna.")    
  
 Pokud <xref:System.Windows.Controls.Primitives.Popup> zaznamená dolní a okraje pravé obrazovky pravého dolního rohu je bod zarovnání automaticky otevíraného okna <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Změna cílové umístění a bod zarovnání automaticky otevíraného okna  
 Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, nebo <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, cílové umístění a automaticky otevírané okno zarovnání příkaz změnit, pokud dojde k určité okraji obrazovky.  Okraje obrazovky, který způsobí, že chcete-li změnit umístění závisí <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu.  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> a <xref:System.Windows.Controls.Primitives.Popup> dolnímu okraji obrazovky, zaznamená cíl původ levého horního rohu cílovou oblast a bod zarovnání automaticky otevíraného okna je dolní části levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu dolnímu okraji obrazovky](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "umístění je dolní a dolním okrajem obrazovky, zaznamená automaticky otevíraného okna.")    
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Left> a <xref:System.Windows.Controls.Primitives.Popup> narazí levému okraji obrazovky, cíl původ pravém horním rohu cílovou oblast a levého horního rohu jebodzarovnáníautomatickyotevíranéhookna<xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu levému okraji obrazovky](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "umístění je vlevo a levým okrajem obrazovky, zaznamená automaticky otevíraného okna.")  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Right> a <xref:System.Windows.Controls.Primitives.Popup> narazí pravému okraji obrazovky, je cíl zdrojem levého horního rohu cílovou oblast a bod zarovnání automaticky otevíraného okna je pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu pravému okraji obrazovky](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "umístění je vpravo a automaticky otevírané okno, zaznamená pravého okraje obrazovky.")  

 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Top> a <xref:System.Windows.Controls.Primitives.Popup> narazí hornímu okraji obrazovky, je cíl zdrojem levého dolního rohu cílovou oblast a bod zarovnání automaticky otevíraného okna je levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu hornímu okraji obrazovky](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "umístění je na nejvyšší úrovni a horním okrajem obrazovky, zaznamená automaticky otevíraného okna.")  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> a <xref:System.Windows.Controls.Primitives.Popup> dolnímu okraji obrazovky, zaznamená cíl původ levého horního rohu cílovou oblast (hranice ukazatel myši) a zarovnání automaticky otevíraného okna bod je dolní části levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nový bod zarovnání z důvodu myši u okraje obrazovky](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "umístění je myš a dolním okrajem obrazovky, zaznamená automaticky otevíraného okna.")    
  
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění automaticky otevíraného okna  
 Cílový bod zarovnání původu a automaticky otevíraného okna můžete přizpůsobit tak, že nastavíte <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Potom definujte <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, který vrátí sadu bodů možná umístění a primární osy (v upřednostňovaném pořadí) pro <xref:System.Windows.Controls.Primitives.Popup>. Bod, který zobrazuje největší část <xref:System.Windows.Controls.Primitives.Popup> zaškrtnuto.  Pozice <xref:System.Windows.Controls.Primitives.Popup> se automaticky upraví, pokud <xref:System.Windows.Controls.Primitives.Popup> je skryt okraji obrazovky. Příklad najdete v tématu [určení vlastního překryvného umístění](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Viz také:

- [Ukázka umístění automaticky otevíraného okna](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
