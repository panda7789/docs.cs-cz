---
title: Chování při umístění překryvného objektu
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 1c377e62ffd334638031baee4d4831ac5a31acf3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243255"
---
# <a name="popup-placement-behavior"></a>Chování při umístění překryvného objektu
Ovládací <xref:System.Windows.Controls.Primitives.Popup> prvek zobrazí obsah v samostatném okně, které plave nad aplikací. Pomocí vlastností <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> můžete určit umístění vzhledem k ovládacímu prvku, myši nebo obrazovce.  Tyto vlastnosti spolupracují, aby vám poskytly flexibilitu při určování polohy <xref:System.Windows.Controls.Primitives.Popup>rozhraní .  
  
> [!NOTE]
> A <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ContextMenu> třídy také definovat těchto pět vlastností a chovat se podobně.  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>Umístění místního vyskakovacího místa  
 Umístění <xref:System.Windows.Controls.Primitives.Popup> může být relativní vzhledem <xref:System.Windows.UIElement> k nebo k celé obrazovce.  Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> čtyři ovládací prvky, které jsou relativní k <xref:System.Windows.UIElement>–v tomto případě obraz. Všechny ovládací <xref:System.Windows.Controls.Primitives.Popup> prvky <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> mají `image1`vlastnost nastavenou na , ale každý <xref:System.Windows.Controls.Primitives.Popup> má jinou hodnotu pro vlastnost umístění.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Následující obrázek znázorňuje <xref:System.Windows.Controls.Primitives.Popup> obrázek a ovládací prvky  
  
 ![Obrázek se čtyřmi ovládacími prvky místního přiskupovacího blokování](./media/popup-placement-behavior/popup-placement-intro.png "Obrázek se čtyřmi vyskakovacími okno")
  
 Tento jednoduchý příklad ukazuje, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> jak <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nastavit vlastnosti <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>a, ale pomocí , <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup> vlastnosti, máte ještě větší kontrolu nad umístěním je umístěn.  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definice pojmů: Anatomie popup  
 Následující pojmy jsou užitečné <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>pro <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>pochopení <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>toho, jak se vlastnosti , , , a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> vlastnosti <xref:System.Windows.Controls.Primitives.Popup>vzájemně vztahují k sobě navzájem a :  
  
- Cílový objekt  
  
- Cílová oblast  
  
- Cílový původ  
  
- Bod zarovnání automaticky otevírané okno  
  
 Tyto termíny poskytují pohodlný způsob, jak <xref:System.Windows.Controls.Primitives.Popup> odkazovat na různé aspekty a ovládací prvek, který je spojen s.  
  
### <a name="target-object"></a>Cílový objekt  
 *Cílový objekt* je prvek, <xref:System.Windows.Controls.Primitives.Popup> ke kterému je přidružen. Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je vlastnost nastavena, určuje cílový objekt.  Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> není nastavena <xref:System.Windows.Controls.Primitives.Popup> a má nadřazený objekt, nadřazený je cílový objekt.  Pokud neexistuje <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> žádná hodnota a žádný nadřazený, neexistuje žádný cílový objekt a <xref:System.Windows.Controls.Primitives.Popup> je umístěn vzhledem k obrazovce.  
  
 Následující příklad vytvoří, <xref:System.Windows.Controls.Primitives.Popup> který je <xref:System.Windows.Controls.Canvas>podřízený .  Příklad nenastaví <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> vlastnost na <xref:System.Windows.Controls.Primitives.Popup>. Výchozí hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> pro <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>je <xref:System.Windows.Controls.Primitives.Popup> , takže <xref:System.Windows.Controls.Canvas>se zobrazí pod .  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Následující obrázek znázorňuje, <xref:System.Windows.Controls.Primitives.Popup> že <xref:System.Windows.Controls.Canvas>je umístěn vzhledem k .  
  
 ![Ovládací prvek místního přijetí bez placementtargetu](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Místní okno bez PlacementTarget.")  

 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> podřízený soubor <xref:System.Windows.Controls.Canvas>, ale tentokrát <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je `ellipse1`nastavenna na , takže <xref:System.Windows.Shapes.Ellipse>se vyskakovací okno zobrazí pod položkou .  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Následující obrázek znázorňuje, <xref:System.Windows.Controls.Primitives.Popup> že <xref:System.Windows.Shapes.Ellipse>je umístěn vzhledem k .  
  
 ![Místní okno umístěné vzhledem k elipsě](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Místní okno s cílem umístění")
  
> [!NOTE]
> Pro <xref:System.Windows.Controls.ToolTip>výchozí hodnotu <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>je .  Pro <xref:System.Windows.Controls.ContextMenu>výchozí hodnotu <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>je . Tyto hodnoty jsou vysvětleny později v části Jak vlastnosti spolupracují.  
  
### <a name="target-area"></a>Cílová oblast  
 *Cílová oblast* je oblast na <xref:System.Windows.Controls.Primitives.Popup> obrazovce, ke které je relativní. V předchozích příkladech <xref:System.Windows.Controls.Primitives.Popup> je zarovnán s hranicemi cílového objektu, <xref:System.Windows.Controls.Primitives.Popup> ale v některých případech je <xref:System.Windows.Controls.Primitives.Popup> zarovnán k jiným hranicem, i když má cílový objekt.  Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> je vlastnost nastavena, cílová oblast se liší od hranice cílového objektu.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Canvas> dva objekty, <xref:System.Windows.Shapes.Rectangle> z <xref:System.Windows.Controls.Primitives.Popup>nichž každý obsahuje a a .  V obou případech <xref:System.Windows.Controls.Primitives.Popup> je cílový objekt <xref:System.Windows.Controls.Canvas>pro . V <xref:System.Windows.Controls.Primitives.Popup> první <xref:System.Windows.Controls.Canvas> má <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> sadu, s <xref:System.Windows.Rect.X%2A> <xref:System.Windows.Rect.Y%2A>jeho <xref:System.Windows.Rect.Width%2A>, <xref:System.Windows.Rect.Height%2A> , a vlastnosti nastaveny na 50, 50, 50 a 100, v uvedeném pořadí. V <xref:System.Windows.Controls.Primitives.Popup> druhém <xref:System.Windows.Controls.Canvas> nemá <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> sadu.  V důsledku toho <xref:System.Windows.Controls.Primitives.Popup> je první <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> umístěn pod <xref:System.Windows.Controls.Primitives.Popup> a druhý <xref:System.Windows.Controls.Canvas>je umístěn pod . Každý <xref:System.Windows.Controls.Canvas> také <xref:System.Windows.Shapes.Rectangle> obsahuje, který má stejné <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> hranice <xref:System.Windows.Controls.Primitives.Popup>jako pro první .  Všimněte <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si, že nevytvoří viditelný prvek v aplikaci; v příkladu <xref:System.Windows.Shapes.Rectangle> vytvoří <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>představují .  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Následující obrázek znázorňuje výsledek předchozího příkladu.  
  
 ![Místní okno s a bez UmístěníRectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Vyskakovací okno s a bez PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Cílový počátek a bod zarovnání automaticky otevírané nabídky  
 *Cílový počátek* a *vyskakovací trasový bod* jsou referenční body v cílové oblasti a vyskakovací okno, které se používají pro umístění. Vlastnosti <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> můžete použít k odsazení vyskakovacího okna z cílové oblasti.  A <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> jsou relativní vzhledem k cílovému počátku a bodu zarovnání automaticky otevírané nabídky. Hodnota vlastnosti <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> určuje, kde se nachází cílový počátek a bod zarovnání automaticky otevíraného pole.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> a <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> nastaví vlastnosti a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> na 20.  Vlastnost <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (výchozí), takže cílový počátek je levý dolní roh cílové oblasti a bod zarovnání vyskakovacího panelu <xref:System.Windows.Controls.Primitives.Popup>je levý horní roh .  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Následující obrázek znázorňuje výsledek předchozího příkladu.  
  
 ![Umístění místního umístění s cílovým bodem zarovnání počátku](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Místní okno s vodorovným posazením a verticaloffsetem.")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>Jak vlastnosti spolupracují  
 Hodnoty <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je třeba zvážit společně zjistit správnou cílovou oblast, cílový původ a popup trasovací bod.  Například pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je hodnota <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, neexistuje žádný cílový <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> objekt, je ignorována a cílová oblast je hranice ukazatele myši. Na druhou stranu, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> je , nebo nadřazený určuje cílový objekt a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> určuje cílovou oblast.  
  
 Následující tabulka popisuje cílový objekt, cílovou oblast, cílový počátek a <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> bod zarovnání automaticky otevíraných míst a označuje, zda a jsou použity pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu výčtu.  
  
|Režim umístění|Cílový objekt|Cílová oblast|Cílový původ|Bod zarovnání automaticky otevírané okno|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Neužívá se. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Obrazovka, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastavena.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k obrazovce.|Levý horní roh cílové oblasti.|Levý horní roh . <xref:System.Windows.Controls.Primitives.Popup>|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Neužívá se. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Obrazovka, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastavena.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k obrazovce.|Levý horní roh cílové oblasti.|Levý horní roh . <xref:System.Windows.Controls.Primitives.Popup>|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo rodiče.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastaven.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k cílovému objektu.|Levý dolní roh cílové oblasti.|Levý horní roh . <xref:System.Windows.Controls.Primitives.Popup>|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo rodiče.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastaven.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k cílovému objektu.|Střed cílové oblasti.|Střed . <xref:System.Windows.Controls.Primitives.Popup>|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo rodiče.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastaven.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k cílovému objektu.|Definováno <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Definováno <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo rodiče.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastaven.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k cílovému objektu.|Levý horní roh cílové oblasti.|V pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Neužívá se. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Hranice ukazatele myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ignoruje.|Levý dolní roh cílové oblasti.|Levý horní roh . <xref:System.Windows.Controls.Primitives.Popup>|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Neužívá se. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> se ignoruje.|Hranice ukazatele myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> se ignoruje.|Levý horní roh cílové oblasti.|Levý horní roh . <xref:System.Windows.Controls.Primitives.Popup>|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo rodiče.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastaven.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k cílovému objektu.|Levý horní roh cílové oblasti.|Levý horní roh . <xref:System.Windows.Controls.Primitives.Popup>|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo rodiče.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastaven.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k cílovému objektu.|Levý horní roh cílové oblasti.|Levý horní roh . <xref:System.Windows.Controls.Primitives.Popup>|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo rodiče.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastaven.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k cílovému objektu.|Pravý horní roh cílové oblasti.|Levý horní roh . <xref:System.Windows.Controls.Primitives.Popup>|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo rodiče.|Cílový objekt nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pokud je nastaven.  Je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relativní k cílovému objektu.|Levý horní roh cílové oblasti.|V levém dolním <xref:System.Windows.Controls.Primitives.Popup>rohu .|  
  
 Následující ilustrace znázorňují <xref:System.Windows.Controls.Primitives.Popup>bod , cílovou oblast, <xref:System.Windows.Controls.Primitives.PlacementMode> cílový počátek a bod zarovnání automaticky otevírané nabídky pro každou hodnotu. Na každém obrázku je cílová <xref:System.Windows.Controls.Primitives.Popup> oblast žlutá a modrá.  
  
 ![Místní okno s umístěním Absolute nebo AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "Umístění je absolutní nebo AbsolutePoint.")
  
 ![Místní okno s umístěním dole](./media/popup-placement-behavior/popup-placement-bottom.png "Umístění je dole.")
  
 ![Místní okno s umístěním center](./media/popup-placement-behavior/popup-placement-center.png "Umístění je střed.")
  
 ![Místní okno s umístěním vlevo](./media/popup-placement-behavior/popup-placement-left.png "Umístění je vlevo.")
  
 ![Místní okno s umístěním myši](./media/popup-placement-behavior/popup-placement-mouse.png "Umístění je myš.")  
  
 ![Místní okno s umístěním MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Umístění je MousePoint.")  
  
 ![Místní okno s umístěním relativní nebo relativní bodů](./media/popup-placement-behavior/popup-placement-relative.png "Umístění je relativní nebo relativníbod.")
  
 ![Místní okno s pravým umístěním](./media/popup-placement-behavior/popup-placement-right.png "Umístění je správné.")
  
 ![Místní okno s umístěním Nahoře](./media/popup-placement-behavior/popup-placement-top.png "Umístění je nahoře.")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Když popup narazí na okraj obrazovky  
 Z bezpečnostních důvodů <xref:System.Windows.Controls.Primitives.Popup> nelze a skryta u okraje obrazovky. Jedna z následujících tří <xref:System.Windows.Controls.Primitives.Popup> věcí se stane, když narazí na okraj obrazovky:  
  
- Vyskakovací okno se znovu zarovná podél okraje obrazovky, které by zakrývalo <xref:System.Windows.Controls.Primitives.Popup>.  
  
- Vyskakovací okno používá jiný bod zarovnání vyskakovacího uchýně.  
  
- Vyskakovací okno používá jiný cílový počátek a bod zarovnání automaticky otevírané okno.  
  
 Tyto možnosti jsou popsány dále v této části.  
  
 Chování při <xref:System.Windows.Controls.Primitives.Popup> setkání s okrajem obrazovky závisí na <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> hodnotě vlastnosti a na okraji obrazovky, se kterým se vyskakovací okno setká. Následující tabulka shrnuje chování, když <xref:System.Windows.Controls.Primitives.Popup> narazí na <xref:System.Windows.Controls.Primitives.PlacementMode> okraj obrazovky pro každou hodnotu.  
  
|Režim umístění|Horní hrana|Spodní okraj|Levý okraj|Pravý okraj|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Zarovná k hornímu okraji.|Zarovná k dolnímu okraji.|Zarovná k levému okraji.|Zarovná k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Zarovná k hornímu okraji.|Bod zarovnání automaticky otevíraného panelu se změní do levého dolního rohu . <xref:System.Windows.Controls.Primitives.Popup>|Zarovná k levému okraji.|Bod zarovnání automaticky otevíraného místa <xref:System.Windows.Controls.Primitives.Popup>se změní do pravého horního rohu .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Zarovná k hornímu okraji.|Cílový počátek se změní do levého horního rohu cílové oblasti a bod zarovnání automaticky otevíraného panelu se změní na levý dolní roh <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná k levému okraji.|Zarovná k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Zarovná k hornímu okraji.|Zarovná k dolnímu okraji.|Zarovná k levému okraji.|Zarovná k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Zarovná k hornímu okraji.|Zarovná k dolnímu okraji.|Cílový počátek se změní v pravém horním rohu cílové oblasti a bod zarovnání <xref:System.Windows.Controls.Primitives.Popup>automaticky otevíraného dne se změní na levý horní roh .|Zarovná k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Zarovná k hornímu okraji.|Cílový počátek se změní na levý horní roh cílové oblasti (hranice ukazatele myši) a bod zarovnání automaticky <xref:System.Windows.Controls.Primitives.Popup>otevíraného panelu se změní do levého dolního rohu .|Zarovná k levému okraji.|Zarovná k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Zarovná k hornímu okraji.|Bod zarovnání automaticky otevíraného panelu se změní do levého dolního rohu . <xref:System.Windows.Controls.Primitives.Popup>|Zarovná k levému okraji.|Bod zarovnání automaticky otevíraného místa se změní do pravého horního rohu vyskakovacího okno.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Zarovná k hornímu okraji.|Zarovná k dolnímu okraji.|Zarovná k levému okraji.|Zarovná k pravému okraji.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Zarovná k hornímu okraji.|Bod zarovnání automaticky otevíraného panelu se změní do levého dolního rohu . <xref:System.Windows.Controls.Primitives.Popup>|Zarovná k levému okraji.|Bod zarovnání automaticky otevíraného místa se změní do pravého horního rohu vyskakovacího okno.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Zarovná k hornímu okraji.|Zarovná k dolnímu okraji.|Zarovná k levému okraji.|Cílový počátek se změní v levém horním rohu cílové oblasti a bod zarovnání <xref:System.Windows.Controls.Primitives.Popup>automaticky otevíraného dne se změní do pravého horního rohu .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Cílový počátek se změní do levého dolního rohu cílové oblasti a bod zarovnání automaticky otevíraného panelu se změní na levý horní roh <xref:System.Windows.Controls.Primitives.Popup>. Ve skutečnosti je to stejné <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>jako když je .|Zarovná k dolnímu okraji.|Zarovná k levému okraji.|Zarovná k pravému okraji.|  
  
### <a name="aligning-to-the-screen-edge"></a>Zarovnání k okraji obrazovky  
 A <xref:System.Windows.Controls.Primitives.Popup> lze zarovnat k okraji obrazovky tím, že <xref:System.Windows.Controls.Primitives.Popup> přemístí sám tak, aby celý je viditelný na obrazovce.  V takovém případě se vzdálenost mezi cílovým počátkem a bodem <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> zarovnání automaticky otevíraného období může lišit od hodnot a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>je <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> nebo , zarovná se ke každému okraji obrazovky.  Předpokládejme například, <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> že <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> má <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> nastavena na a nastavena na 100.  Pokud dolní okraj obrazovky skryje celý <xref:System.Windows.Controls.Primitives.Popup>okraj <xref:System.Windows.Controls.Primitives.Popup> obrazovky nebo jeho část , přemístí se podél spodního okraje obrazovky a svislá vzdálenost mezi cílovým počátkem a bodem zarovnání vyskakovacího panelu je menší než 100. Následující obrázek to ukazuje.  
  
 ![Místní okno, které se zarovná k okraji obrazovky](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Místní okno se zarovná k okraji obrazovky.")
  
### <a name="changing-the-popup-alignment-point"></a>Změna bodu zarovnání automaticky otevírané okno  
 Pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>je <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, nebo , popup zarovnání bod změní, když popup narazí na dolní nebo pravý okraj obrazovky.  
  
 Následující obrázek znázorňuje, že když dolní okraj <xref:System.Windows.Controls.Primitives.Popup>obrazovky skryje celý dolní okraj obrazovky <xref:System.Windows.Controls.Primitives.Popup>, je koncový bod vyskakovacího panelu levý dolní roh .  
  
 ![Nový bod zarovnání vzhledem k dolnímu okraji obrazovky](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Vyskakovací okno narazí na dolní okraj obrazovky a změní bod zarovnání automaticky otevíraného panelu.")  

 Následující obrázek znázorňuje, že pokud <xref:System.Windows.Controls.Primitives.Popup> je bod zarovnání automaticky otevíraného <xref:System.Windows.Controls.Primitives.Popup>místa skrytý u pravého okraje obrazovky, je vpravém horním rohu .  
  
 ![Nový bod zarovnání automaticky otevíraného rámečku kvůli okraji obrazovky](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Vyskakovací okno narazí na pravý okraj obrazovky a změní bod zarovnání automaticky otevíraného rámečku.")
  
 Pokud <xref:System.Windows.Controls.Primitives.Popup> dojde k okraji dolní a pravé obrazovky, je bod zarovnání <xref:System.Windows.Controls.Primitives.Popup>automaticky otevíraného panelu v pravém dolním rohu .  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Změna cílového počátku a bodu zarovnání automaticky otevírané nabídky  
 Pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>dojde <xref:System.Windows.Controls.Primitives.PlacementMode.Left> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>k <xref:System.Windows.Controls.Primitives.PlacementMode.Right>určitému okraji obrazovky, <xref:System.Windows.Controls.Primitives.PlacementMode.Top>změní se bod cílového počátku a vyskakovacího bodu.  Hrana obrazovky, která způsobí změnu <xref:System.Windows.Controls.Primitives.PlacementMode> polohy, závisí na hodnotě.  
  
 Následující obrázek znázorňuje, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> že když je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> a <xref:System.Windows.Controls.Primitives.Popup> narazí na dolní okraj obrazovky, cílový počátek je levý horní roh cílové <xref:System.Windows.Controls.Primitives.Popup>oblasti a vyskakovací bod zarovnání je v levém dolním rohu .  
  
 ![Nový bod zarovnání vzhledem k dolnímu okraji obrazovky](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Umístění je dole a vyskakovací okno narazí na spodní okraj obrazovky.")
  
 Následující obrázek znázorňuje, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> že když je <xref:System.Windows.Controls.Primitives.PlacementMode.Left> a <xref:System.Windows.Controls.Primitives.Popup> narazí na levý okraj obrazovky, cílový počátek je pravý horní roh cílové <xref:System.Windows.Controls.Primitives.Popup>oblasti a vyskakovací bod zarovnání je v levém horním rohu .  
  
 ![Nový bod zarovnání vzhledem k levému okraji obrazovky](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Umístění je vlevo a vyskakovací okno narazí na levý okraj obrazovky.")  
  
 Následující obrázek znázorňuje, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> že když je <xref:System.Windows.Controls.Primitives.PlacementMode.Right> a <xref:System.Windows.Controls.Primitives.Popup> narazí na pravý okraj obrazovky, cílový počátek je levý horní roh cílové <xref:System.Windows.Controls.Primitives.Popup>oblasti a vyskakovací bod zarovnání je v pravém horním rohu .  
  
 ![Nový bod zarovnání díky pravému okraji obrazovky](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Umístění je správné a vyskakovací okno narazí na pravý okraj obrazovky.")  

 Následující obrázek znázorňuje, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> že když je <xref:System.Windows.Controls.Primitives.PlacementMode.Top> a <xref:System.Windows.Controls.Primitives.Popup> narazí na horní okraj obrazovky, cílový počátek je vlevo v dolníčásti cílové <xref:System.Windows.Controls.Primitives.Popup>oblasti a vyskakovací bod zarovnání je v levém horním rohu .  
  
 ![Nový bod zarovnání vzhledem k hornímu okraji obrazovky](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Umístění je nahoře a vyskakovací okno narazí na horní okraj obrazovky.")  
  
 Následující obrázek znázorňuje, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> že když je <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> a <xref:System.Windows.Controls.Primitives.Popup> narazí na dolní okraj obrazovky, cílový počátek je levý horní roh cílové oblasti (hranice ukazatele myši) <xref:System.Windows.Controls.Primitives.Popup>a popup trasovací bod je v levém dolním rohu .  
  
 ![nový bod zarovnání kvůli myši v blízkosti okraje obrazovky](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Umístění je myš a vyskakovací okno narazí na spodní okraj obrazovky.")
  
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění automaticky otevíraná pole  
 Cílový počátek a bod zarovnání automaticky <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> otevírané okno můžete přizpůsobit nastavením vlastnosti na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Potom definujte delegáta, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> který vrátí sadu možných bodů umístění a <xref:System.Windows.Controls.Primitives.Popup>primárních os (v pořadí podle priority) pro . Bod, který zobrazuje největší <xref:System.Windows.Controls.Primitives.Popup> část je vybrán.  Poloha je <xref:System.Windows.Controls.Primitives.Popup> automaticky upravena, <xref:System.Windows.Controls.Primitives.Popup> pokud je skryta u okraje obrazovky. Příklad najdete v [tématu Určení vlastní místní polohy](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Viz také

- [Ukázka umístění místního umístění](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
