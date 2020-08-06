---
title: Chování při umístění prvku Popup
description: Naučte se, jak pomocí vlastností určit pozici ovládacího prvku Popup subsystému Windows Presentation Foundation relativně k ovládacímu prvku, myši nebo obrazovce.
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 8184805518bc56693ead4c7d1f0e9a1bff9bff8f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167745"
---
# <a name="popup-placement-behavior"></a>Chování při umístění prvku Popup
Ovládací prvek <xref:System.Windows.Controls.Primitives.Popup> zobrazí obsah v samostatném okně, které pluje nad aplikací. Pozici ovládacího prvku <xref:System.Windows.Controls.Primitives.Popup> můžete určit relativně k ovládacímu prvku, myši nebo obrazovce pomocí vlastností <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>.  Společným použitím těchto vlastností můžete flexibilně určovat pozici prvku <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
> Těchto pět vlastností definují také třídy <xref:System.Windows.Controls.ToolTip> a <xref:System.Windows.Controls.ContextMenu> a chovají se v nich podobně.  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>Umístění prvku Popup  
 Umístění ovládacího prvku <xref:System.Windows.Controls.Primitives.Popup> může být relativní vzhledem k objektu <xref:System.Windows.UIElement> nebo k celé obrazovce.  Následující příklad vytvoří čtyři ovládací prvky <xref:System.Windows.Controls.Primitives.Popup>, které jsou umístěné relativně k objektu <xref:System.Windows.UIElement> – v tomto případě obrázku. U všech ovládacích prvků <xref:System.Windows.Controls.Primitives.Popup> je vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nastavená na hodnotu `image1`, ale každý prvek <xref:System.Windows.Controls.Primitives.Popup> má jinou hodnotu vlastnosti Placement.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Na následující ilustraci je vidět obrázek a ovládací prvky <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Obrázek se čtyřmi ovládacími prvky Popup](./media/popup-placement-behavior/popup-placement-intro.png "Obrázek se čtyřmi prvky Popup")
  
 Tento jednoduchý příklad ukazuje, jak se nastavují vlastnosti <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, ale při použití vlastností <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> máte ještě větší kontrolu nad umístěním prvku <xref:System.Windows.Controls.Primitives.Popup>.  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definice pojmů: Anatomie ovládacího prvku Popup  
 K porozumění tomu, jaký vztah mají vlastnosti <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> mezi sebou a k ovládacímu prvku <xref:System.Windows.Controls.Primitives.Popup>, jsou užitečné následující pojmy:  
  
- Cílový objekt  
  
- Cílová oblast  
  
- Počátek cíle  
  
- Bod zarovnání prvku Popup  
  
 Tyto pojmy poskytují pohodlný způsob, jak odkazovat na různé aspekty prvku <xref:System.Windows.Controls.Primitives.Popup> a ovládacího prvku, ke kterému je přidružený.  
  
### <a name="target-object"></a>Cílový objekt  
 *Cílový objekt* je prvek, ke kterému je prvek <xref:System.Windows.Controls.Primitives.Popup> přidružený. Pokud je nastavená vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, určuje cílový objekt.  Pokud vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> není nastavená a prvek <xref:System.Windows.Controls.Primitives.Popup> má nadřazený prvek, je cílovým objektem nadřazený prvek.  Pokud není k dispozici žádná hodnota vlastnosti <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ani žádný nadřazený prvek, neexistuje žádný cílový objekt a prvek <xref:System.Windows.Controls.Primitives.Popup> se umístí relativně vzhledem k obrazovce.  
  
 Následující příklad vytvoří prvek <xref:System.Windows.Controls.Primitives.Popup>, který je podřízeným prvkem objektu <xref:System.Windows.Controls.Canvas>.  V tomto příkladu není u prvku <xref:System.Windows.Controls.Primitives.Popup> nastavená vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>. Výchozí hodnota vlastnosti <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, takže prvek <xref:System.Windows.Controls.Primitives.Popup> se zobrazí pod objektem <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Následující obrázek ukazuje, že prvek <xref:System.Windows.Controls.Primitives.Popup> je umístěný relativně vzhledem k objektu <xref:System.Windows.Controls.Canvas>.  
  
 ![Ovládací prvek Popup bez vlastnosti PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Prvek Popup bez vlastnosti PlacementTarget")  

 Následující příklad vytvoří prvek <xref:System.Windows.Controls.Primitives.Popup>, který je podřízeným prvkem objektu <xref:System.Windows.Controls.Canvas>, ale tentokrát je vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nastavená na `ellipse1`, takže se prvek Popup zobrazí pod objektem <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Následující obrázek ukazuje, že prvek <xref:System.Windows.Controls.Primitives.Popup> je umístěný relativně vzhledem k objektu <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Prvek Popup umístěný relativně vzhledem k elipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Prvek Popup s vlastností PlacementTarget")
  
> [!NOTE]
> Pro objekt <xref:System.Windows.Controls.ToolTip> má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> výchozí hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Pro objekt <xref:System.Windows.Controls.ContextMenu> má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> výchozí hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Tyto hodnoty jsou vysvětlené později v části o společném fungování vlastností.  
  
### <a name="target-area"></a>Cílová oblast  
 *Cílová oblast* je oblast na obrazovce, vzhledem ke které je prvek <xref:System.Windows.Controls.Primitives.Popup> relativně umístěn. V předchozích příkladech byl prvek <xref:System.Windows.Controls.Primitives.Popup> zarovnaný s mezemi cílového objektu, ale v některých případech je prvek <xref:System.Windows.Controls.Primitives.Popup> zarovnaný k jiným mezím (a to i v případě, že má prvek <xref:System.Windows.Controls.Primitives.Popup> svůj cílový objekt).  Pokud je nastavená vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, cílová oblast se liší od mezí cílového objektu.  
  
 Následující příklad vytvoří dva objekty <xref:System.Windows.Controls.Canvas>, z nichž každý obsahuje objekt <xref:System.Windows.Shapes.Rectangle> a prvek <xref:System.Windows.Controls.Primitives.Popup>.  V obou případech je pro prvek <xref:System.Windows.Controls.Primitives.Popup> cílovým objektem <xref:System.Windows.Controls.Canvas>. Prvek <xref:System.Windows.Controls.Primitives.Popup> v prvním objektu <xref:System.Windows.Controls.Canvas> má nastavený objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, jehož vlastnosti <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A> a <xref:System.Windows.Rect.Height%2A> jsou nastavené na 50, 50, 50 a 100 (v uvedeném pořadí). Prvek <xref:System.Windows.Controls.Primitives.Popup> v druhém objektu <xref:System.Windows.Controls.Canvas> nemá nastavený objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  Výsledkem bude, že první prvek <xref:System.Windows.Controls.Primitives.Popup> bude umístěný pod objektem <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> a druhý prvek <xref:System.Windows.Controls.Primitives.Popup> pod objektem <xref:System.Windows.Controls.Canvas>. Každý objekt <xref:System.Windows.Controls.Canvas> obsahuje také objekt <xref:System.Windows.Shapes.Rectangle>, který má stejné meze jako objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pro první prvek <xref:System.Windows.Controls.Primitives.Popup>.  Všimněte si, že objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> nevytváří viditelný element v aplikaci; příklad vytvoří objekt <xref:System.Windows.Shapes.Rectangle>, který reprezentuje objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Výsledek předchozího příkladu je znázorněný na následující ilustraci.  
  
 ![Prvek Popup s objektem PlacementRectangle a bez něj](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Prvek Popup s objektem PlacementRectangle a bez něj")  

### <a name="target-origin-and-popup-alignment-point"></a>Počátek cíle a bod zarovnání prvku Popup  
 *Počátek cíle* a *bod zarovnání prvku Popup* jsou referenční body cílové oblasti a prvku Popup, které se používají k umístění. K odsazení prvku Popup od cílové oblasti můžete použít vlastnosti <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>.  Vlastnosti <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> jsou relativní vzhledem k počátku cíle a bodu zarovnání prvku Popup. Hodnota vlastnosti <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> určuje, kde se počátek cíle a bod zarovnání prvku Popup nacházejí.  
  
 Následující příklad vytvoří prvek <xref:System.Windows.Controls.Primitives.Popup> a nastaví vlastnosti <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> na hodnotu 20.  Vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavená na hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (výchozí), takže počátkem cíle je levý dolní roh cílové oblasti a bodem zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> je jeho levý horní roh.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Výsledek předchozího příkladu je znázorněný na následující ilustraci.  
  
 ![Umístění prvku Popup pomocí počátku cíle a bodu zarovnání](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Prvek Popup s vlastnostmi HorizontalOffset a VerticalOffset")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>Jak tyto vlastnosti fungují společně  
 Hodnoty vlastností <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je potřeba zvážit společně, aby bylo možné určit správnou cílovou oblast, počátek cíle a bod zarovnání prvku Popup.  Pokud má například vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, neexistuje žádný cílový objekt, vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ignoruje a cílovou oblastí jsou meze ukazatele myši. Na druhé straně, pokud má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, je cílový objekt určený vlastností <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazeným prvkem a cílová oblast je určená vlastností <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 Následující tabulka popisuje cílový objekt, cílovou oblast, počátek cíle a bod zarovnání prvku Popup a uvádí, jestli se pro jednotlivé hodnoty výčtu <xref:System.Windows.Controls.Primitives.PlacementMode> používají vlastnosti <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
|PlacementMode|Cílový objekt|Cílová oblast|Počátek cíle|Bod zarovnání prvku Popup|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Nelze použít. Vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je ignorována.|Obrazovka, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k obrazovce.|Levý horní roh cílové oblasti.|Levý horní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Nelze použít. Vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je ignorována.|Obrazovka, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k obrazovce.|Levý horní roh cílové oblasti.|Levý horní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený prvek.|Cílový objekt, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k cílovému objektu.|Levý dolní roh cílové oblasti.|Levý horní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený prvek.|Cílový objekt, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k cílovému objektu.|Střed cílové oblasti.|Střed prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený prvek.|Cílový objekt, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k cílovému objektu.|Definováno delegátem <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Definováno delegátem <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený prvek.|Cílový objekt, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Pravý horní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Nelze použít. Vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je ignorována.|Meze ukazatele myši. Vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je ignorována.|Levý dolní roh cílové oblasti.|Levý horní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Nelze použít. Vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je ignorována.|Meze ukazatele myši. Vlastnost <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je ignorována.|Levý horní roh cílové oblasti.|Levý horní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený prvek.|Cílový objekt, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Levý horní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený prvek.|Cílový objekt, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Levý horní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený prvek.|Cílový objekt, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k cílovému objektu.|Pravý horní roh cílové oblasti.|Levý horní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazený prvek.|Cílový objekt, případně objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, pokud je nastavený.  Objekt <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je umístěný relativně vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Levý dolní roh prvku <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Následující ilustrace znázorňují prvek <xref:System.Windows.Controls.Primitives.Popup>, cílovou oblast, počátek cíle a bod zarovnání prvku Popup pro každou hodnotu vlastnosti <xref:System.Windows.Controls.Primitives.PlacementMode>. Na všech obrázcích je cílová oblast žlutá a prvek <xref:System.Windows.Controls.Primitives.Popup> modrý.  
  
 ![Prvek Popup s umístěním nastaveným na hodnotu Absolute nebo AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "Vlastnost Placement je nastavená na hodnotu Absolute nebo AbsolutePoint.")
  
 ![Prvek Popup s umístěním nastaveným na hodnotu Bottom](./media/popup-placement-behavior/popup-placement-bottom.png "Vlastnost Placement je nastavená na hodnotu Bottom.")
  
 ![Prvek Popup s umístěním nastaveným na hodnotu Center](./media/popup-placement-behavior/popup-placement-center.png "Vlastnost Placement je nastavená na hodnotu Center.")
  
 ![Prvek Popup s umístěním nastaveným na hodnotu Left](./media/popup-placement-behavior/popup-placement-left.png "Vlastnost Placement je nastavená na hodnotu Left.")
  
 ![Prvek Popup s umístěním nastaveným na hodnotu Mouse](./media/popup-placement-behavior/popup-placement-mouse.png "Vlastnost Placement je nastavená na hodnotu Mouse.")  
  
 ![Prvek Popup s umístěním nastaveným na hodnotu MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Vlastnost Placement je nastavená na hodnotu MousePoint.")  
  
 ![Prvek Popup s umístěním nastaveným na hodnotu Relative nebo RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "Vlastnost Placement je nastavená na hodnotu Relative nebo RelativePoint.")
  
 ![Prvek Popup s umístěním nastaveným na hodnotu Right](./media/popup-placement-behavior/popup-placement-right.png "Vlastnost Placement je nastavená na hodnotu Right.")
  
 ![Prvek Popup s umístěním nastaveným na hodnotu Top](./media/popup-placement-behavior/popup-placement-top.png "Vlastnost Placement je nastavená na hodnotu Top.")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Když prvek Popup narazí na okraj obrazovky  
 Z bezpečnostních důvodů nemůže být prvek <xref:System.Windows.Controls.Primitives.Popup> skrytý okrajem obrazovky. Když prvek <xref:System.Windows.Controls.Primitives.Popup> narazí na okraj obrazovky, stane se jedna z následujících tří věcí:  
  
- Prvek <xref:System.Windows.Controls.Primitives.Popup> se zarovná k okraji obrazovky, který by ho zakryl.  
  
- Prvek Popup použije jiný bod zarovnání.  
  
- Prvek Popup použije jiný počátek cíle a bod zarovnání prvku Popup.  
  
 Tyto možnosti jsou podrobněji popsané dále v této části.  
  
 Chování prvku <xref:System.Windows.Controls.Primitives.Popup>, když narazí na okraj obrazovky, závisí na hodnotě vlastnosti <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a na tom, na který okraj obrazovky narazí. Následující tabulka shrnuje chování prvku <xref:System.Windows.Controls.Primitives.Popup>, když narazí na okraj obrazovky, pro jednotlivé hodnoty vlastnosti <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
|PlacementMode|Horní okraj|Dolní okraj|Levý okraj|Pravý okraj|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Zarovná se k hornímu okraji.|Bod zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se změní na jeho levý dolní roh.|Zarovná se k levému okraji.|Bod zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se změní na jeho pravý horní roh.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Zarovná se k hornímu okraji.|Počátek cíle se změní na levý horní roh cílové oblasti a bod zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se změní na jeho levý dolní roh.|Zarovná se k levému okraji.|Zarovná se k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Počátek cíle se změní na pravý horní roh cílové oblasti a bod zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se změní na jeho levý horní roh.|Zarovná se k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Zarovná se k hornímu okraji.|Počátek cíle se změní na levý horní roh cílové oblasti (mezí ukazatele myši) a bod zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se změní na jeho levý dolní roh.|Zarovná se k levému okraji.|Zarovná se k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Zarovná se k hornímu okraji.|Bod zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se změní na jeho levý dolní roh.|Zarovná se k levému okraji.|Bod zarovnání prvku Popup se změní na jeho pravý horní roh.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Zarovná se k hornímu okraji.|Bod zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se změní na jeho levý dolní roh.|Zarovná se k levému okraji.|Bod zarovnání prvku Popup se změní na jeho pravý horní roh.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Počátek cíle se změní na levý horní roh cílové oblasti a bod zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se změní na jeho pravý horní roh.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Počátek cíle se změní na levý dolní roh cílové oblasti a bod zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se změní na jeho levý horní roh. Ve výsledku je to stejné, jako když má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravému okraji.|  
  
### <a name="aligning-to-the-screen-edge"></a>Zarovnání k okraji obrazovky  
 Prvek <xref:System.Windows.Controls.Primitives.Popup> se může zarovnat k okraji obrazovky tak, že se celý přemístí. Na obrazovce tak půjde vidět celý prvek <xref:System.Windows.Controls.Primitives.Popup>.  Pokud k tomuto dojde, může se vzdálenost mezi počátkem cíle a bodem zarovnání prvku Popup lišit od hodnot vlastností <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Pokud má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center> nebo <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, prvek <xref:System.Windows.Controls.Primitives.Popup> se zarovnává ke každému okraji obrazovky.  Předpokládejme například, že prvek <xref:System.Windows.Controls.Primitives.Popup> má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nastavenou na <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> a vlastnost <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> na 100.  Pokud dolní okraj obrazovky skryje celý prvek <xref:System.Windows.Controls.Primitives.Popup> nebo jeho část, prvek <xref:System.Windows.Controls.Primitives.Popup> se přemístí k dolnímu okraji obrazovky a svislá vzdálenost mezi počátkem cíle a bodem zarovnání prvku Popup bude menší než 100. Ukazuje to následující obrázek.  
  
 ![Prvek Popup, který se zarovnal k okraji obrazovky](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Prvek Popup se zarovnává k okraji obrazovky.")
  
### <a name="changing-the-popup-alignment-point"></a>Změna bodu zarovnání prvku Popup  
 Pokud má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> nebo <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> a prvek Popup narazí na dolní nebo pravý okraj obrazovky, změní se jeho bod zarovnání.  
  
 Následující ilustrace ukazuje, že když dolní okraj obrazovky skryje celý prvek <xref:System.Windows.Controls.Primitives.Popup> nebo jeho část, stane se bodem zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> jeho levý dolní roh.  
  
 ![Nový bod zarovnání z důvodu kolize s dolním okrajem obrazovky](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Prvek Popup narazí na dolní okraj obrazovky a změní se jeho bod zarovnání.")  

 Následující ilustrace ukazuje, že pokud by byl prvek <xref:System.Windows.Controls.Primitives.Popup> skrytý pravým okrajem obrazovky, stane se bodem zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> jeho pravý horní roh.  
  
 ![Nový bod zarovnání prvku Popup z důvodu kolize s okrajem obrazovky](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Prvek Popup narazí na pravý okraj obrazovky a změní se jeho bod zarovnání.")
  
 Pokud prvek <xref:System.Windows.Controls.Primitives.Popup> narazí na dolní a pravý okraj obrazovky, stane se bodem zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> jeho pravý dolní roh.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Změna počátku cíle a bodu zarovnání prvku Popup  
 Pokud má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right> nebo <xref:System.Windows.Controls.Primitives.PlacementMode.Top> a dojde ke kolizi s okrajem obrazovky, změní se počátek cíle a bod zarovnání prvku Popup.  Okraj obrazovky, který způsobí změnu pozice, závisí na hodnotě vlastnosti <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
 Následující obrázek ukazuje, že když má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> a prvek <xref:System.Windows.Controls.Primitives.Popup> narazí na dolní okraj obrazovky, stane se počátkem cíle levý horní roh cílové oblasti a bodem zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se stane jeho levý dolní roh.  
  
 ![Nový bod zarovnání z důvodu kolize s dolním okrajem obrazovky](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Vlastnost Placement je nastavená na hodnotu Bottom a prvek Popup narazí na dolní okraj obrazovky.")
  
 Následující obrázek ukazuje, že když má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Left> a prvek <xref:System.Windows.Controls.Primitives.Popup> narazí na levý okraj obrazovky, stane se počátkem cíle pravý horní roh cílové oblasti a bodem zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se stane jeho levý horní roh.  
  
 ![Nový bod zarovnání z důvodu kolize s levým okrajem obrazovky](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Vlastnost Placement je nastavená na hodnotu Left a prvek Popup narazí na levý okraj obrazovky.")  
  
 Následující obrázek ukazuje, že když má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Right> a prvek <xref:System.Windows.Controls.Primitives.Popup> narazí na pravý okraj obrazovky, stane se počátkem cíle levý horní roh cílové oblasti a bodem zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se stane jeho pravý horní roh.  
  
 ![Nový bod zarovnání z důvodu kolize s pravým okrajem obrazovky](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Vlastnost Placement je nastavená na hodnotu Right a prvek Popup narazí na pravý okraj obrazovky.")  

 Následující obrázek ukazuje, že když má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Top> a prvek <xref:System.Windows.Controls.Primitives.Popup> narazí na horní okraj obrazovky, stane se počátkem cíle levý dolní roh cílové oblasti a bodem zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se stane jeho levý horní roh.  
  
 ![Nový bod zarovnání z důvodu kolize s horním okrajem obrazovky](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Vlastnost Placement je nastavená na hodnotu Top a prvek Popup narazí na horní okraj obrazovky.")  
  
 Následující obrázek ukazuje, že když má vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotu <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> a prvek <xref:System.Windows.Controls.Primitives.Popup> narazí na dolní okraj obrazovky, stane se počátkem cíle levý horní roh cílové oblasti (mezí ukazatele myši) a bodem zarovnání prvku <xref:System.Windows.Controls.Primitives.Popup> se stane jeho levý dolní roh.  
  
 ![nový bod zarovnání kvůli myši poblíž okraje obrazovky](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Vlastnost Placement je nastavená na hodnotu Mouse a prvek Popup narazí na dolní okraj obrazovky.")
  
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění prvku Popup  
 Při nastavení vlastnosti <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> můžete přizpůsobit počátek cíle a bod zarovnání prvku Popup. Pak nadefinujte delegáta <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>, který vrací sadu možných bodů umístění a primárních os (v pořadí podle preference) pro prvek <xref:System.Windows.Controls.Primitives.Popup>. Vybere se bod, který zobrazí největší část prvku <xref:System.Windows.Controls.Primitives.Popup>.  Pozice prvku <xref:System.Windows.Controls.Primitives.Popup> se automaticky upraví, pokud by byl prvek <xref:System.Windows.Controls.Primitives.Popup> skrytý okrajem obrazovky. Příklad najdete v článku o [určení vlastního umístění prvku Popup](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Viz také:

- [Ukázka umístění prvku Popup](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
