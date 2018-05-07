---
title: Chování při umístění překryvného objektu
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 3aef3d7863bc02aa4164b1fc9ef4464fbe799cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="popup-placement-behavior"></a>Chování při umístění překryvného objektu
A <xref:System.Windows.Controls.Primitives.Popup> ovládací prvek zobrazí obsah v samostatném okně, které překrývat aplikace. Můžete zadat umístění <xref:System.Windows.Controls.Primitives.Popup> relativně k ovládacího prvku, myš nebo obrazovky pomocí <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vlastnosti.  Tyto vlastnosti spolupracovat a poskytuje vám flexibilitu při určující pozici <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
>  <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ContextMenu> třídy také definovat těchto pět vlastnosti a chovají podobně.  
  

  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Umístění automaticky otevřeném okně.  
 Umístění <xref:System.Windows.Controls.Primitives.Popup> může být vzhledem k <xref:System.Windows.UIElement> nebo na celou obrazovku.  Následující příklad vytvoří čtyři <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky, které jsou vzhledem k <xref:System.Windows.UIElement>– v tomto případě bitovou kopii. Všechny <xref:System.Windows.Controls.Primitives.Popup> mají ovládací prvky <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> vlastnost nastavena na hodnotu `image1`, ale každý <xref:System.Windows.Controls.Primitives.Popup> má jinou hodnotu pro vlastnost umístění.  
  
 [!code-xaml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Následující obrázek znázorňuje bitovou kopii a <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky  
  
 ![Bitové kopie s čtyři ovládací prvky místní](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
Bitové kopie s čtyři automaticky otevíraná okna  
  
 Tento jednoduchý příklad ukazuje, jak nastavit <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnosti, ale pomocí <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vlastnosti, máte ještě větší kontrolu nad where <xref:System.Windows.Controls.Primitives.Popup> je umístěn.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definice podmínek: anatomie místní okno  
 Následující termíny jsou užitečné v pochopení jak <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vzájemně souvisejí vlastnosti a <xref:System.Windows.Controls.Primitives.Popup>:  
  
-   Cílový objekt  
  
-   Cílovou oblast  
  
-   Původní cíl  
  
-   Místní nabídka Zarovnání bodu  
  
 Tyto podmínky poskytnout vhodný způsob k odkazování na různé aspekty <xref:System.Windows.Controls.Primitives.Popup> a ovládací prvek, který je přidružen.  
  
### <a name="target-object"></a>Cílový objekt  
 *Cílový objekt* elementu, <xref:System.Windows.Controls.Primitives.Popup> je přidružen. Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> vlastnost nastavena, určuje cílový objekt.  Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> není nastavena a <xref:System.Windows.Controls.Primitives.Popup> má nadřazený objekt, nadřazená položka cílový objekt.  Pokud je žádné <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> hodnota a žádné nadřazeným prvkem, neexistuje žádný cílový objekt a <xref:System.Windows.Controls.Primitives.Popup> je umístěn relativně k obrazovce.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> který je podřízeným <xref:System.Windows.Controls.Canvas>.  V příkladu nenastaví <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> vlastnost <xref:System.Windows.Controls.Primitives.Popup>. Výchozí hodnota pro <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, proto <xref:System.Windows.Controls.Primitives.Popup> se zobrazí pod <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> je umístěn vzhledem k <xref:System.Windows.Controls.Canvas>.  
  
 ![Ovládací prvek místního PlacementTarget](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.PNG "PopupPlacementNoPlacementTarget")  
Místní nabídka PlacementTarget  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> který je podřízeným <xref:System.Windows.Controls.Canvas>, ale tentokrát <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je nastaven na `ellipse1`, takže automaticky otevřeném okně se zobrazí pod <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> je umístěn vzhledem k <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Místní okno umístěné relativně k elipsy](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.PNG "PopupPlacementWithPlacementTarget")  
Místní okno s PlacementTarget  
  
> [!NOTE]
>  Pro <xref:System.Windows.Controls.ToolTip>, výchozí hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Pro <xref:System.Windows.Controls.ContextMenu>, výchozí hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Tyto hodnoty jsou vysvětleny později v "Jak vlastnosti spolupracují."  
  
### <a name="target-area"></a>Cílovou oblast  
 *Cílové oblasti* je oblast na obrazovce, <xref:System.Windows.Controls.Primitives.Popup> je vzhledem k. V předchozích příkladech <xref:System.Windows.Controls.Primitives.Popup> je zarovnáno s hranice cílového objektu, ale v některých případech <xref:System.Windows.Controls.Primitives.Popup> je umístěno na další hranice i v případě <xref:System.Windows.Controls.Primitives.Popup> je cílový objekt.  Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> vlastnost nastavena, cílovou oblast se liší od hranice cílového objektu.  
  
 Následující příklad vytvoří dvě <xref:System.Windows.Controls.Canvas> objekty, každé z nich obsahující <xref:System.Windows.Shapes.Rectangle> a <xref:System.Windows.Controls.Primitives.Popup>.  V obou případech cílový objekt pro <xref:System.Windows.Controls.Primitives.Popup> je <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Controls.Primitives.Popup> v prvním <xref:System.Windows.Controls.Canvas> má <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nastavte s jeho <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, a <xref:System.Windows.Rect.Height%2A> vlastnosti nastavena na 50, 50, 50 až 100, v uvedeném pořadí. <xref:System.Windows.Controls.Primitives.Popup> Za sekundu <xref:System.Windows.Controls.Canvas> nemá <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nastavit.  V důsledku toho první <xref:System.Windows.Controls.Primitives.Popup> je umístěno pod <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> a druhý <xref:System.Windows.Controls.Primitives.Popup> je umístěno pod <xref:System.Windows.Controls.Canvas>. Každý <xref:System.Windows.Controls.Canvas> také obsahuje <xref:System.Windows.Shapes.Rectangle> má stejné hranice jako <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pro první <xref:System.Windows.Controls.Primitives.Popup>.  Všimněte si, že <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nevytvoří element viditelné v aplikaci; v příkladu se vytváří <xref:System.Windows.Shapes.Rectangle> představují <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Následující obrázek znázorňuje výsledek v předchozím příkladu.  
  
 ![Místní a bez PlacementRectangle](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.PNG "PopupPlacementPlacementRectangle")  
Místní a bez PlacementRectangle  
  
### <a name="target-origin-and-popup-alignment-point"></a>Cíl původ a bod zarovnání místního okna  
 *Cíle počátek* a *bod zarovnání místního okna* jsou body odkazu na cílovou oblast a místní, v uvedeném pořadí, které se používají pro umístění. Můžete použít <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vlastnosti k posunutí místní z cílové oblasti.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> jsou relativní vzhledem k cílové původ a bod zarovnání místního okna. Hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost určuje, kde se nachází cílového bodu zarovnání původ a místní.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> a nastaví <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vlastnosti až 20 číslic.  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (výchozí), tak cílové pochází okraje v levém dolním rohu cílovou oblast a místní zarovnání bod je levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Následující obrázek znázorňuje výsledek v předchozím příkladu.  
  
 ![Místní umístění s cílovým počátek zarovnání bodem](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
Místní okno s HorizontalOffset a VerticalOffset  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Jak fungují společně vlastnosti  
 Hodnoty <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je potřeba zvážit společně a pokuste se zjistit správnou cílovou oblast, cílový původ a bod zarovnání místního okna.  Například pokud hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, neexistuje žádný cílový objekt, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ignoruje, a cílovou oblast je rozsah ukazatele myši. Na druhé straně Pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené Určuje cílový objekt a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Určuje cílovou oblast.  
  
 Následující tabulka popisuje cílový objekt, cílovou oblast, cílový původ a místní zarovnání bodu a určuje, zda <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se používají pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnota výčtu.  
  
|PlacementMode|Cílový objekt|Cílovou oblast|Původní cíl|Místní nabídka Zarovnání bodu|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Nelze použít. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je ignorován.|Na obrazovce nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k obrazovce.|Levém horním rohu cílové oblasti.|Levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Nelze použít. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je ignorován.|Na obrazovce nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k obrazovce.|Levém horním rohu cílové oblasti.|Levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem ke cílový objekt.|Okraje v levém dolním rohu cílovou oblast.|Levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem ke cílový objekt.|Center cílovou oblast.|Střed <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem ke cílový objekt.|Určené <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Určené <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem ke cílový objekt.|Levém horním rohu cílové oblasti.|Pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Nelze použít. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je ignorován.|Rozsah ukazatele myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je ignorován.|Okraje v levém dolním rohu cílovou oblast.|Levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Nelze použít. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je ignorován.|Rozsah ukazatele myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je ignorován.|Levém horním rohu cílové oblasti.|Levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem ke cílový objekt.|Levém horním rohu cílové oblasti.|Levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem ke cílový objekt.|Levém horním rohu cílové oblasti.|Levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem ke cílový objekt.|Pravém horním rohu cílové oblasti.|Levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazené.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaveno.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem ke cílový objekt.|Levém horním rohu cílové oblasti.|Okraje v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Následující ilustrace zobrazit <xref:System.Windows.Controls.Primitives.Popup>, cílovou oblast, cílový původ a zarovnání místní bod pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu. Každý obrázku cílovou oblast je žlutý a <xref:System.Windows.Controls.Primitives.Popup> modře.  
  
 ![Místní okno s absolutní nebo AbsolutePoint](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
Umístění je absolutní nebo AbsolutePoint  
  
 ![Místní okno s dolní](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
Umístění je dolní  
  
 ![Místní okno s Center](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
Umístění je Center  
  
 ![Místní okno s levém](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
Umístění je vlevo  
  
 ![Místní okno s myši](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
Umístění je myši  
  
 ![Místní okno s MousePoint](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
Umístění je MousePoint  
  
 ![Místní okno s relativním nebo RelativePoint](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
Umístění je relativní vůči nebo RelativePoint  
  
 ![Místní okno s správné](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
Umístění je vpravo  
  
 ![Místní okno s nejvyšší](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
Umístění je na nejvyšší úrovni  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Pokud automaticky otevřeném okně nalezne okraje obrazovky  
 Z bezpečnostních důvodů <xref:System.Windows.Controls.Primitives.Popup> nemůže být skrytý na základě okraji obrazovky. Jeden z následujících tří akcí se stane, když <xref:System.Windows.Controls.Primitives.Popup> zaznamená okraji obrazovky:  
  
-   Automaticky otevřeném okně změněné zarovnání samotné podél okraje obrazovky, který by skrývat <xref:System.Windows.Controls.Primitives.Popup>.  
  
-   Automaticky otevřeném okně použije bod zarovnání jinou místní.  
  
-   Automaticky otevřeném okně použije bod počátek a místní jiný cíl zarovnání.  
  
 Tyto možnosti jsou popsány dále později v této části.  
  
 Chování <xref:System.Windows.Controls.Primitives.Popup> Pokud se setká s okraji obrazovky závisí na hodnotu <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost a které obrazovce edge zaznamená automaticky otevřeném okně. Následující tabulka shrnuje chování při <xref:System.Windows.Controls.Primitives.Popup> zaznamená okraji obrazovky pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu.  
  
|PlacementMode|Horní okraj|Dolní okraj|Levý okraj|Pravý okraj|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Zarovnává na levý okraj.|Zarovnává na pravý okraj.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Zarovnává horní okraj.|Bod zarovnání místní změny do okraje v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnává na levý okraj.|Bod zarovnání místní změny pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Zarovnává horní okraj.|Cíl počátek změny do levého horního rohu cílovou oblast a bodem zarovnání místní změny do okraje v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnává na levý okraj.|Zarovnává na pravý okraj.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Zarovnává na levý okraj.|Zarovnává na pravý okraj.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Cíl počátek změní na pravém horním rohu cílovou oblast a bodem zarovnání místní změny do levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnává na pravý okraj.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Zarovnává horní okraj.|Cíl počátek změny do levého horního rohu cílovou oblast (hranice ukazatelem myši) a bodem zarovnání místní změny do okraje v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnává na levý okraj.|Zarovnává na pravý okraj.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Zarovnává horní okraj.|Bod zarovnání místní změny do okraje v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnává na levý okraj.|Zarovnání místní bod změny na pravém horním rohu místní nabídky.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Zarovnává na levý okraj.|Zarovnává na pravý okraj.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Zarovnává horní okraj.|Bod zarovnání místní změny do okraje v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovnává na levý okraj.|Zarovnání místní bod změny na pravém horním rohu místní nabídky.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Zarovnává horní okraj.|Zarovnává dolní okraj.|Zarovnává na levý okraj.|Cíl počátek změny do levého horního rohu cílovou oblast a bodem zarovnání místní změny pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Cíl počátek změny do okraje v levém dolním rohu cílovou oblast a bodem zarovnání místní změny do levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>. Ve skutečnosti je to stejné jako při <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Zarovnává dolní okraj.|Zarovnává na levý okraj.|Zarovnává na pravý okraj.|  
  
### <a name="aligning-to-the-screen-edge"></a>Zarovnání na hranu obrazovky  
 A <xref:System.Windows.Controls.Primitives.Popup> můžete zarovnat na okraji obrazovky pomocí samotného tak přemístění celý <xref:System.Windows.Controls.Primitives.Popup> je viditelný na obrazovce.  V takovém případě vzdálenost mezi bodem zarovnání původ a místní cíl může lišit od hodnoty <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, nebo <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> zarovnává sám sebe pro každou okraji obrazovky.  Například předpokládejme, že <xref:System.Windows.Controls.Primitives.Popup> má <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> nastavena na hodnotu 100.  Pokud jsou dolní okraje obrazovky skryje nebo jeho část <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.Primitives.Popup> přemístí samotné podél dolního okraje obrazovky a svislá vzdálenost mezi cíl původ a místní bod zarovnání je menší než 100. Následující obrázek ukazuje to.  
  
 ![Místní nabídka, aby u okraje obrazovky](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
Místní nabídka nastavuje zarovnání na hranu obrazovky  
  
### <a name="changing-the-popup-alignment-point"></a>Změna bodu zarovnání automaticky otevřeném okně.  
 Pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, nebo <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, bodem zarovnání místní změní, když v místní nabídce dojde dolní nebo pravému okraji obrazovky.  
  
 Následující obrázek ukazuje, která při dolnímu okraji obrazovky skryje nebo jeho část <xref:System.Windows.Controls.Primitives.Popup>, bod zarovnání automaticky otevřeném okně je okraje v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání kvůli dolnímu okraji obrazovky](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
Místní nabídka zaznamená dolnímu okraji obrazovky a změní bod zarovnání místního okna  
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup> skryt okraji pravého obrazovky a bodem zarovnání automaticky otevřeném okně je pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání místní kvůli okraji obrazovky](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
Místní nabídka zaznamená pravého okraje obrazovky a změní bod zarovnání místního okna  
  
 Pokud <xref:System.Windows.Controls.Primitives.Popup> zaznamená dolním a pravém obrazovky okraji bod zarovnání automaticky otevřeném okně je pravém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Změna cílové původ a bod zarovnání místního okna  
 Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, nebo <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, zarovnání původ a místní cíl bodu změnit, pokud je zjištěna určitá okraji obrazovky.  Okraje obrazovky, který způsobuje, že pozice změnit závisí na <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu.  
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> a <xref:System.Windows.Controls.Primitives.Popup> dolnímu okraji obrazovky, zaznamená cíl pochází levého horního rohu cílovou oblast a zarovnání bod automaticky otevřeném okně je okraje v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání kvůli dolnímu okraji obrazovky](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
Umístění je dolní a v místní nabídce dojde jsou dolní okraje obrazovky  
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Left> a <xref:System.Windows.Controls.Primitives.Popup> zaznamená obrazovky levém okraji a cíl pochází pravém horním rohu cílovou oblast a bod zarovnání automaticky otevřeném okně je levého horního rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání kvůli levému okraji obrazovky](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
Umístění je doleva a v místní nabídce dojde levém okraji obrazovky  
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Right> a <xref:System.Windows.Controls.Primitives.Popup> zaznamená okraji pravého obrazovky a cíl pochází levého horního rohu cílovou oblast a místní zarovnání bod je pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání kvůli pravému okraji obrazovky](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
Umístění není pravé a v místní nabídce dojde pravého okraje obrazovky  
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Top> a <xref:System.Windows.Controls.Primitives.Popup> dojde hornímu okraji obrazovky, počátek cíl je okraje v levém dolním rohu cílovou oblast a místní zarovnání bod je levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání kvůli hornímu okraji obrazovky](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
Umístění je na nejvyšší úrovni a v místní nabídce dojde jsou horní okraje obrazovky  
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> a <xref:System.Windows.Controls.Primitives.Popup> zaznamená dolnímu okraji obrazovky počátek cíl je levém horním rohu cílovou oblast (hranice ukazatelem myši) a zarovnání místní nabídka bod je okraje v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nový bod zarovnání kvůli myši blízkosti okraje obrazovky](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
Umístění je myši a v místní nabídce dojde jsou dolní okraje obrazovky  
  
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění automaticky otevřeném okně.  
 Můžete přizpůsobit cílového bodu zarovnání původ a místní nastavení <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnost <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Potom zadejte <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, který vrací sadu bodů možná umístění a primární osy (v upřednostňovaném pořadí) pro <xref:System.Windows.Controls.Primitives.Popup>. Bod, který ukazuje na největší část <xref:System.Windows.Controls.Primitives.Popup> je vybrána.  Pozice <xref:System.Windows.Controls.Primitives.Popup> je automaticky upravována, pokud <xref:System.Windows.Controls.Primitives.Popup> je skrytý na základě okraji obrazovky. Příklad, naleznete v části [zadat vlastní místní pozici](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázka umístění automaticky otevřeném okně.](http://go.microsoft.com/fwlink/?LinkID=160032)
