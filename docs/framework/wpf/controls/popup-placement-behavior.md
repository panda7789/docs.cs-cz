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
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951737"
---
# <a name="popup-placement-behavior"></a>Chování při umístění překryvného objektu
<xref:System.Windows.Controls.Primitives.Popup> Ovládací prvek zobrazí obsah v samostatném okně, které je v aplikaci plovoucí. Můžete <xref:System.Windows.Controls.Primitives.Popup> určit polohu relativní k ovládacímu prvku, myši nebo obrazovce <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>pomocí vlastností, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> .  Tyto vlastnosti vzájemně spolupracují, aby vám poskytovaly flexibilitu při určování <xref:System.Windows.Controls.Primitives.Popup>pozice.  
  
> [!NOTE]
> Třídy <xref:System.Windows.Controls.ToolTip> a<xref:System.Windows.Controls.ContextMenu> také definují tyto pět vlastností a chovají se podobně.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Umístění místní nabídky  
 Umístění <xref:System.Windows.Controls.Primitives.Popup> může být relativní <xref:System.Windows.UIElement> k nebo na celou obrazovku.  Následující příklad vytvoří čtyři <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky, které jsou relativní vzhledem k a <xref:System.Windows.UIElement>– v tomto případě obrázek. Všechny ovládací prvky <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> mají vlastnost nastavenou na `image1`, ale každá <xref:System.Windows.Controls.Primitives.Popup> má jinou hodnotu pro vlastnost umístění. <xref:System.Windows.Controls.Primitives.Popup>  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 Následující ilustrace znázorňuje obrázek a <xref:System.Windows.Controls.Primitives.Popup> ovládací prvky  
  
 ![Obrázek se čtyřmi ovládacími prvky místní nabídky](./media/popup-placement-behavior/popup-placement-intro.png "Obrázek se čtyřmi automaticky otevíraných oken")    
  
 Tento jednoduchý <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> příklad ukazuje <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup> , jak nastavit vlastnosti a, ale pomocí vlastností ,amáteještěvětšíkontrolunadtím,kdejeumístěn.<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Definice podmínek: Anatomie automaticky otevíraného okna  
 Následující výrazy jsou užitečné <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>v souvislosti s tím, jak vlastnosti,, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>a vzájemně souvisí, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>a <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Cílový objekt  
  
- Cílová oblast  
  
- Cílový původ  
  
- Automaticky otevírané okno – bod zarovnání  
  
 Tyto výrazy poskytují pohodlný způsob, jak odkazovat na různé aspekty <xref:System.Windows.Controls.Primitives.Popup> a ovládací prvek, ke kterému je přidružen.  
  
### <a name="target-object"></a>Cílový objekt  
 *Cílový objekt* je prvek, ke kterému <xref:System.Windows.Controls.Primitives.Popup> je přidružen. Pokud je <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> vlastnost nastavena, určuje cílový objekt.  Pokud <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> není nastaven <xref:System.Windows.Controls.Primitives.Popup> a má nadřazený, nadřazený objekt je cílový objekt.  Pokud není <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> k dispozici žádná hodnota ani žádná nadřazená položka, není k dispozici <xref:System.Windows.Controls.Primitives.Popup> žádný cílový objekt a je umístěn vzhledem k obrazovce.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> objekt, který je podřízenou položkou <xref:System.Windows.Controls.Canvas>.  V příkladu není nastavena <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> vlastnost <xref:System.Windows.Controls.Primitives.Popup>v. Výchozí hodnota pro <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType> <xref:System.Windows.Controls.Primitives.Popup> ,<xref:System.Windows.Controls.Canvas>takže se zobrazí pod.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> je umístěn vzhledem <xref:System.Windows.Controls.Canvas>k.  
  
 ![Místní ovládací prvek bez PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Automaticky otevíraná okna bez PlacementTarget.")  

 Následující <xref:System.Windows.Controls.Primitives.Popup> příklad vytvoří podřízený objekt, který je podřízenou položkou <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Canvas>, ale tentokrát je nastavena <xref:System.Windows.Shapes.Ellipse>na `ellipse1`, takže se místní nabídka zobrazí pod.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> je umístěn vzhledem <xref:System.Windows.Shapes.Ellipse>k.  
  
 ![Automaticky otevírané okno, které se umístí vzhledem k elipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Automaticky otevírané okno s PlacementTarget")    
  
> [!NOTE]
> Výchozí <xref:System.Windows.Controls.ToolTip> hodnotapro<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>je. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>  Výchozí <xref:System.Windows.Controls.ContextMenu> hodnotapro<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>je. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Tyto hodnoty jsou vysvětleny později v tématu Jak vlastnosti pracují dohromady.  
  
### <a name="target-area"></a>Cílová oblast  
 *Cílová oblast* je oblast na obrazovce, ke které <xref:System.Windows.Controls.Primitives.Popup> je relativní. V předchozích příkladech <xref:System.Windows.Controls.Primitives.Popup> je zarovnán s mezemi cílového objektu, ale v některých případech <xref:System.Windows.Controls.Primitives.Popup> je zarovnána k ostatním hranicím, i <xref:System.Windows.Controls.Primitives.Popup> když má cílový objekt.  Pokud je <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> vlastnost nastavena, cílová oblast se liší od hranic cílového objektu.  
  
 Následující příklad vytvoří dva <xref:System.Windows.Controls.Canvas> objekty, každý z nich <xref:System.Windows.Shapes.Rectangle> obsahující a a <xref:System.Windows.Controls.Primitives.Popup>.  V obou případech cílový objekt pro <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas>je. <xref:System.Windows.Controls.Primitives.Popup> V prvním <xref:System.Windows.Controls.Canvas> má množinu<xref:System.Windows.Rect.X%2A>s vlastnostmi ,<xref:System.Windows.Rect.Y%2A> ,a<xref:System.Windows.Rect.Height%2A> nastavenými na 50, 50, 50 a 100, v uvedeném pořadí. <xref:System.Windows.Rect.Width%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup> V druhém <xref:System.Windows.Controls.Canvas> nemá sadu<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> .  Výsledkem je <xref:System.Windows.Controls.Primitives.Popup> , že první je umístěný <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pod a <xref:System.Windows.Controls.Canvas>druhý <xref:System.Windows.Controls.Primitives.Popup> je umístěný pod. Každá <xref:System.Windows.Controls.Canvas> z nich také <xref:System.Windows.Shapes.Rectangle> obsahuje a má <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> stejné meze jako pro první <xref:System.Windows.Controls.Primitives.Popup>.  Všimněte si, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> že v aplikaci není vytvořen viditelný prvek; příklad <xref:System.Windows.Shapes.Rectangle> vytvoří, který představuje <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 Následující ilustrace znázorňuje výsledek předchozího příkladu.  
  
 ![Automaticky otevírané okno s PlacementRectangle a bez něj](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Automaticky otevírané okno s PlacementRectangle a bez něj.")  

### <a name="target-origin-and-popup-alignment-point"></a>Počátek cíle a bod zarovnání automaticky otevíraného okna  
 *Cílový zdroj* a *bod zarovnání místní nabídky* jsou referenční body v cílové oblasti a v místní nabídce, které se používají k umístění. Můžete použít <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> vlastnosti a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> k posunu automaticky otevírané okno z cílové oblasti.  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> A<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> jsou relativní k cílovému původu a bodu zarovnání automaticky otevíraného okna. Hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnosti určuje, kde se nachází cílový počátek a bod zarovnání místní nabídky.  
  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.Popup> a nastaví vlastnosti a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> jako <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> hodnotu 20.  Vlastnost je nastavena na <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (výchozí), takže cílovým zdrojem je levý dolní roh cílové oblasti a bod zarovnání automaticky otevíraného okna je levý horní roh <xref:System.Windows.Controls.Primitives.Popup>. <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 Následující ilustrace znázorňuje výsledek předchozího příkladu.  
  
 ![Umístění automaticky otevíraného okna s cílovým počátečním bodem zarovnání](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Automaticky otevíraná okna s HorizontalOffset a VerticalOffset.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Jak vlastnosti spolupracují  
 Hodnoty <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>a jepotřebazvážitspolečněprozjištěnísprávnécílovéoblasti,cílovéhozdrojeaboduzarovnáníautomatickyotevíranéhookna.<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>  Například pokud hodnota <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, neexistuje <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> žádný cílový objekt, je ignorována a cílová oblast je hranice ukazatele myši. Na druhé straně, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Pokud je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> nebo nadřazená položka určuje cílový objekt a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> určí cílovou oblast.  
  
 Následující tabulka popisuje cílový objekt, cílovou oblast, cílový původ a místní bod zarovnání a určuje, zda <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jsou použity pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu výčtu.  
  
|PlacementMode|Cílový objekt|Cílová oblast|Cílový původ|Automaticky otevírané okno – bod zarovnání|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Není k dispozici. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>je ignorováno.|Obrazovka, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k obrazovce.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Není k dispozici. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>je ignorováno.|Obrazovka, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastavena.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k obrazovce.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo nadřazená položka.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaven.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílovému objektu.|Levý dolní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo nadřazená položka.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaven.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílovému objektu.|Střed cílové oblasti|Střed <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo nadřazená položka.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaven.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílovému objektu.|Definováno v <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Definováno v <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo nadřazená položka.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaven.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Pravý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Není k dispozici. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>je ignorováno.|Hranice ukazatele myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>je ignorováno.|Levý dolní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Není k dispozici. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>je ignorováno.|Hranice ukazatele myši. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>je ignorováno.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo nadřazená položka.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaven.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo nadřazená položka.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaven.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo nadřazená položka.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaven.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílovému objektu.|Pravý horní roh cílové oblasti.|Levý horní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>nebo nadřazená položka.|Cílový objekt, nebo <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Pokud je nastaven.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Je relativní vzhledem k cílovému objektu.|Levý horní roh cílové oblasti.|Levý dolní roh <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Následující ilustrace znázorňují <xref:System.Windows.Controls.Primitives.Popup>pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu bod zarovnání, cílovou oblast, cílový původ a místní okno. V každém obrázku je cílová oblast žlutá a <xref:System.Windows.Controls.Primitives.Popup> je modrá.  
  
 ![Automaticky otevírané okno s absolutním nebo AbsolutePointm umístěním](./media/popup-placement-behavior/popup-placement-absolute.png "Umístění je absolutní nebo AbsolutePoint.")    
  
 ![Automaticky otevírané okno s] nejnižším umístěním (./media/popup-placement-behavior/popup-placement-bottom.png "Umístění je dole.")   
  
 ![Automaticky otevírané okno s centrovým umístěním](./media/popup-placement-behavior/popup-placement-center.png "Umístění je na střed.")    
  
 ![Automaticky otevírané okno s levým umístěním](./media/popup-placement-behavior/popup-placement-left.png "Umístění je ponecháno.")   
  
 ![Místní nabídka s umístěním myši](./media/popup-placement-behavior/popup-placement-mouse.png "Umístění je myš.")  
  
 ![Automaticky otevírané okno s umístěním MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Umístění je MousePoint.")  
  
 ![Automaticky otevírané okno s relativním nebo RelativePointm umístěním](./media/popup-placement-behavior/popup-placement-relative.png "Umístění je relativní nebo RelativePoint.")    
  
 ![Místní nabídka se správným umístěním](./media/popup-placement-behavior/popup-placement-right.png "Umístění je pravé.")    
  
 ![Automaticky otevírané okno s největším umístěním](./media/popup-placement-behavior/popup-placement-top.png "Umístění je horní.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Když se v překryvném okně objeví okraj obrazovky  
 Z bezpečnostních důvodů <xref:System.Windows.Controls.Primitives.Popup> nemůže být okraj obrazovky skrytý. Jedna z následujících tří akcí se stane, když <xref:System.Windows.Controls.Primitives.Popup> dojde k okraji obrazovky:  
  
- Místní okno se znovu zarovnává se okrajem obrazovky, které by se <xref:System.Windows.Controls.Primitives.Popup>překrývalo.  
  
- Automaticky otevíraná okna používá jiný bod zarovnání.  
  
- Automaticky otevíraná okna používá jiný cílový zdroj a bod zarovnání místní nabídky.  
  
 Tyto možnosti jsou podrobněji popsané dále v této části.  
  
 Chování <xref:System.Windows.Controls.Primitives.Popup> při zjištění okraje obrazovky závisí na hodnotě <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnosti a na okraji obrazovky, na které se automaticky otevíraná okna setkávají. Následující tabulka shrnuje chování při <xref:System.Windows.Controls.Primitives.Popup> výskytu okraje obrazovky pro každou <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotu.  
  
|PlacementMode|Horní hrana|Dolní hrana|Levý okraj|Pravá hrana|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Zarovná se k hornímu okraji.|Automaticky otevírané okno se změní v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Místní ovládací bod zarovnání se změní v pravém horním rohu okna <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Zarovná se k hornímu okraji.|Cílový počátek se změní v levém horním rohu cílové oblasti a automaticky se změní bod zarovnání v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Cílový počátek se změní v pravém horním rohu cílové oblasti a automaticky se změní bod zarovnání v levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Zarovná se k hornímu okraji.|Cílový počátek se změní v levém horním rohu cílové oblasti (hranice ukazatele myši) a bod zarovnání automaticky otevíraného okna se změní v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Zarovná se k hornímu okraji.|Automaticky otevírané okno se změní v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Automaticky otevírané okno se změní v pravém horním rohu automaticky otevíraného okna.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Zarovná se k hornímu okraji.|Automaticky otevírané okno se změní v levém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.|Zarovná se k levému okraji.|Automaticky otevírané okno se změní v pravém horním rohu automaticky otevíraného okna.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Zarovná se k hornímu okraji.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Cílový počátek se změní v levém horním rohu cílové oblasti a automaticky se změní bod zarovnání v pravém horním rohu <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|Cílový počátek se změní do levého dolního rohu cílové oblasti a automaticky se změní bod zarovnání v levém horním rohu <xref:System.Windows.Controls.Primitives.Popup>. V důsledku toho je to stejné jako v případě <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> , <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>kdy je.|Zarovná se k dolnímu okraji.|Zarovná se k levému okraji.|Zarovná se k pravé hraně.|  
  
### <a name="aligning-to-the-screen-edge"></a>Zarovnání na okraj obrazovky  
 Objekt <xref:System.Windows.Controls.Primitives.Popup> lze zarovnat k okraji obrazovky přemístěním sebe, aby se na obrazovce zobrazila <xref:System.Windows.Controls.Primitives.Popup> celá obrazovka.  Pokud k tomu dojde, může se vzdálenost mezi cílovým počátkem a bodem zarovnání místní nabídky lišit od <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> hodnot <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>a. Když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, nebo<xref:System.Windows.Controls.Primitives.PlacementMode.Center> ,se<xref:System.Windows.Controls.Primitives.Popup> zarovnává na všechny okraje obrazovky. <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>  Předpokládejme například, <xref:System.Windows.Controls.Primitives.Popup> že má <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nastavenou <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> hodnotu a <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> nastavenou na 100.  Pokud spodní okraj obrazovky skryje vše nebo část <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup> , přemístí se sama podél dolního okraje obrazovky a svislá vzdálenost mezi cílovým zdrojem a bodem zarovnání místní nabídky je menší než 100. To ukazuje následující obrázek.  
  
 ![Automaticky otevírané okno, které se zarovnává na okraj obrazovky](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Automaticky otevírané okno se zarovná k okraji obrazovky.")    
  
### <a name="changing-the-popup-alignment-point"></a>Změna bodu zarovnání automaticky otevíraného okna  
 Pokud <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, nebo<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, místní okno se změní v případě, že se místní nabídka narazí na okraj na spodní nebo pravé straně obrazovky. <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>  
  
 Následující obrázek ukazuje, že když se dolní okraj obrazovky skryje úplně nebo částečně <xref:System.Windows.Controls.Primitives.Popup>, zůstane místní bod zarovnání v levém dolním rohu. <xref:System.Windows.Controls.Primitives.Popup>  
  
 ![Nový bod zarovnání z důvodu dolní hrany obrazovky](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "V překryvném okně dojde k dolnímu okraji obrazovky a změna bodu zarovnání automaticky otevíraného okna.")  

 Následující obrázek ukazuje, že <xref:System.Windows.Controls.Primitives.Popup> je-li obrázek skrytý na pravé straně obrazovky, je bod zarovnání automaticky zobrazen v pravém horním rohu. <xref:System.Windows.Controls.Primitives.Popup>  
  
 ![Nový bod zarovnání pro místní okno z důvodu okraje obrazovky] V překryvném okně (./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "dojde k pravému okraji obrazovky a změna bodu zarovnání automaticky otevíraného okna.")    
  
 Pokud dojde <xref:System.Windows.Controls.Primitives.Popup> k dolnímu a pravému okraji obrazovky, automaticky otevírané okno je bod zarovnání v pravém dolním rohu <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Změna cílového zdroje a bodu zarovnání automaticky otevíraného okna  
 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> Vpřípadě<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, ,<xref:System.Windows.Controls.Primitives.PlacementMode.Left> ,,<xref:System.Windows.Controls.Primitives.PlacementMode.Top>nebo se změní cílový počátek a bod zarovnání místní nabídky, pokud je zjištěna určitá hrana obrazovky. <xref:System.Windows.Controls.Primitives.PlacementMode.Right> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>  Okraj obrazovky, který způsobuje změnu pozice, závisí na <xref:System.Windows.Controls.Primitives.PlacementMode> hodnotě.  
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> a <xref:System.Windows.Controls.Primitives.Popup> dojde k výskytu dolního okraje obrazovky, cílovým zdrojem je levý horní roh cílové oblasti a bod zarovnání místní nabídky je v levém dolním rohu. <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu dolní hrany obrazovky](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Umístění je dolní a v překryvném okně dojde k dolnímu okraji obrazovky.")    
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Left> a <xref:System.Windows.Controls.Primitives.Popup> dojde k levému okraji obrazovky, cílovým zdrojem je pravý horní roh cílové oblasti a místní bod zarovnání je v levém horním rohu. <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu levého okraje obrazovky](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Umístění je ponecháno a automaticky otevírané okno narazí na levý okraj obrazovky.")  
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Right> a <xref:System.Windows.Controls.Primitives.Popup> dojde k pravému okraji obrazovky, cílový zdroj je levý horní roh cílové oblasti a bod zarovnání místní nabídky je pravý horní roh okna <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu pravého okraje obrazovky](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Umístění je napravo a v překryvném okně dojde k pravému okraji obrazovky.")  

 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Top> a <xref:System.Windows.Controls.Primitives.Popup> narazí na horní okraj obrazovky, cílovým zdrojem je levý dolní roh cílové oblasti a bod zarovnání místní nabídky je v levém horním rohu. <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nový bod zarovnání z důvodu horní hrany obrazovky](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Umístění je horní a v překryvném okně dojde k hornímu okraji obrazovky.")  
  
 Následující obrázek ukazuje, že když <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> je <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> a <xref:System.Windows.Controls.Primitives.Popup> dojde k výskytu dolního okraje obrazovky, cílovým zdrojem je levý horní roh cílové oblasti (hranice ukazatele myši) a místní zarovnání. Point je levý dolní roh okna <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nový bod zarovnání v důsledku myši poblíž okraje obrazovky](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Umístění je myš a automaticky otevírané okno narazí na spodní okraj obrazovky.")    
  
### <a name="customizing-popup-placement"></a>Přizpůsobení umístění automaticky otevíraných oken  
 Nastavením <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> vlastnosti na <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>můžete přizpůsobit cílový počátek a bod zarovnání místní nabídky. Pak definujte <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> delegáta, který vrací sadu možných bodů umístění a primární osy (v pořadí podle priority) <xref:System.Windows.Controls.Primitives.Popup>pro. Bod, který zobrazuje největší část, <xref:System.Windows.Controls.Primitives.Popup> je vybrán.  Pozice <xref:System.Windows.Controls.Primitives.Popup> se automaticky upraví, pokud je na <xref:System.Windows.Controls.Primitives.Popup> okraji obrazovky skrytá. Příklad naleznete v tématu [určení vlastní místní pozice](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Viz také:

- [Ukázka umístění místní nabídky](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
