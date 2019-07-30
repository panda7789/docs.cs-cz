---
title: Kreslení formátovaného textu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF]
- typography [WPF], drawing formatted text
- formatted text [WPF]
- drawing [WPF], formatted text
ms.assetid: b1d851c1-331c-4814-9964-6fe769db6f1f
ms.openlocfilehash: 3b410bcf609aca2cb201042247b8768f243ac93a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629740"
---
# <a name="drawing-formatted-text"></a>Kreslení formátovaného textu
Toto téma obsahuje přehled funkcí <xref:System.Windows.Media.FormattedText> objektu. Tento objekt poskytuje nižší úroveň ovládacího prvku pro vykreslování textu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacích.  

## <a name="technology-overview"></a>Přehled technologie  
 <xref:System.Windows.Media.FormattedText> Objekt umožňuje nakreslit víceřádkový text, ve kterém je každý znak v textu možné formátovat individuálně. Následující příklad ukazuje text, který obsahuje několik formátů, které jsou na něj aplikovány.  
  
 ![Text zobrazený pomocí objektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
>  Pro vývojáře, kteří migrují [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] z rozhraní API, tabulka v oddílu [migrace do Win32](#win32_migration) obsahuje [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] seznam příznaků DrawText a přibližný ekvivalent [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]v.  
  
### <a name="reasons-for-using-formatted-text"></a>Důvody pro použití formátovaného textu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsahuje několik ovládacích prvků pro vykreslení textu na obrazovku. Každý ovládací prvek je zaměřený na jiný scénář a má svůj vlastní seznam funkcí a omezení. Obecně platí, že <xref:System.Windows.Controls.TextBlock> element by měl být použit, pokud je vyžadována podpora omezeného textu, jako je například krátká [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]věta v. <xref:System.Windows.Controls.Label>dá se použít, když je potřeba podpora minimálního textu. Další informace najdete v tématu [dokumenty v WPF](documents-in-wpf.md).  
  
 Objekt poskytuje větší funkce formátování textu než [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] textové ovládací prvky a může být užitečné v případech, kdy chcete text použít jako dekorativní prvek. <xref:System.Windows.Media.FormattedText> Další informace naleznete v následující části [převedení formátovaného textu na geometrii](#converting_formatted_text).  
  
 Kromě toho je objekt <xref:System.Windows.Media.FormattedText> vhodný pro vytváření objektů, které jsou orientované <xref:System.Windows.Media.DrawingVisual>na text. <xref:System.Windows.Media.DrawingVisual>je odlehčená třída pro kreslení, která se používá k vykreslování tvarů, obrázků nebo textu. Další informace najdete v tématu [test přístupů pomocí DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Použití objektu FormattedText  
 Chcete-li vytvořit formátovaný text, <xref:System.Windows.Media.FormattedText.%23ctor%2A> zavolejte konstruktor pro <xref:System.Windows.Media.FormattedText> vytvoření objektu. Po vytvoření počátečního formátovaného textového řetězce můžete použít rozsah stylů formátování.  
  
 <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> Použijte vlastnost k omezení textu na určitou šířku. Text se automaticky zalomí, aby nedošlo k překročení zadané šířky. <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> Použijte vlastnost k omezení textu na určitou výšku. V textu se zobrazí tři tečky, "..." pro text, který překračuje zadanou výšku.  
  
 ![Text zobrazený pomocí WordWrap a tři tečky](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 Můžete použít více stylů formátování na jeden nebo více znaků. Například můžete zavolat <xref:System.Windows.Media.FormattedText.SetFontSize%2A> metodu a a <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> změnit tak formátování prvních pět znaků v textu.  
  
 Následující příklad kódu vytvoří <xref:System.Windows.Media.FormattedText> objekt a poté použije pro text několik stylů formátování.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Měrná jednotka velikosti písma  
 Stejně jako u jiných textových objektů [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v aplikacích <xref:System.Windows.Media.FormattedText> používá objekt jako měrnou jednotku pixely nezávislé na zařízení. Většina [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikací však jako měrnou jednotku používá body. Pokud chcete použít zobrazovaný text v jednotkách bodů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikacích, je nutné převést jednotky nezávislé na zařízení (1/1/96 palce na jednotku) na body. Následující příklad kódu ukazuje, jak provést tento převod.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Převod formátovaného textu na geometrii  
 Formátovaný text můžete převést na <xref:System.Windows.Media.Geometry> objekty, což vám umožní vytvářet další typy vizuálně zajímavého textu. Můžete například vytvořit <xref:System.Windows.Media.Geometry> objekt na základě obrysu textového řetězce.  
  
 ![Obrys textu s použitím štětce s lineárním přechodem](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Následující příklady ilustrují několik způsobů vytváření zajímavých vizuálních efektů úpravou tahu, výplně a zvýraznění převedeného textu.  
  
 ![Text s různými barvami pro výplň a tah](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Text s obrázkem štětce aplikovaný na tah](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Text s obrázkem štětce aplikovaný na tah a zvýraznění](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Když je text převeden na <xref:System.Windows.Media.Geometry> objekt, již není kolekcí znaků, nelze upravit znaky v textovém řetězci. Vzhled převedeného textu však můžete ovlivnit úpravou vlastností tahu a výplně. Tah odkazuje na obrys převedeného textu; Výplň odkazuje na oblast uvnitř obrysu převedeného textu. Další informace najdete v tématu [Vytvoření obrysového textu](how-to-create-outlined-text.md).  
  
 Můžete také převést formátovaný text na <xref:System.Windows.Media.PathGeometry> objekt a použít objekt pro zvýraznění textu. Například můžete použít animaci na <xref:System.Windows.Media.PathGeometry> objekt, aby animace vychází z obrysu formátovaného textu.  
  
 Následující příklad ukazuje formátovaný text, který byl převeden na <xref:System.Windows.Media.PathGeometry> objekt. Animovaná elipsa následuje po cestě k vykreslenému textu.  
  
 ![Koule následující po geometrii cesty textu](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Koule následující po geometrii cesty textu  
  
 Další informace najdete v tématu [jak: Vytvořte PathGeometry animaci pro text](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Po převedení na <xref:System.Windows.Media.PathGeometry> objekt můžete vytvořit další zajímavé způsoby použití formátovaného textu. Můžete například oříznout video, které se zobrazí v něm.  
  
 ![Video, které se zobrazuje v geometrii cesty textu](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migrace Win32  
 Funkce <xref:System.Windows.Media.FormattedText> pro kreslení textu jsou podobné funkcím [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] funkce DrawText. Pro vývojáře, kteří migrují [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] z rozhraní API, v následující tabulce [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] jsou uvedeny příznaky DrawText a přibližný [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ekvivalent v.  
  
|Příznak DrawText|Ekvivalent WPF|Poznámky|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Tuto <xref:System.Windows.Media.FormattedText.Height%2A> vlastnost použijte k výpočtu příslušné [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozice v poli DrawText ' y '.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Pomocí vlastností <xref:System.Windows.Media.FormattedText.Width%2A> a můžete vypočítat výstupní obdélník. <xref:System.Windows.Media.FormattedText.Height%2A>|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použijte vlastnost s hodnotou nastavenou na <xref:System.Windows.TextAlignment.Center>. <xref:System.Windows.Media.FormattedText.TextAlignment%2A>|  
|DT_EDITCONTROL|Žádný|Není nutné. Šířka prostoru a vykreslení posledního řádku jsou stejné jako v ovládacím prvku pro úpravy rozhraní.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použijte vlastnost s hodnotou <xref:System.Windows.TextTrimming.CharacterEllipsis>. <xref:System.Windows.Media.FormattedText.Trimming%2A><br /><br /> Použijte <xref:System.Windows.TextTrimming.WordEllipsis> k získání [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS s koncovými tečkami DT_WORD_ELIPSIS – v tomto případě se tři tečky vyskytují jenom na slovech, která se nevejdou na jeden řádek.|  
|DT_EXPAND_TABS|Žádný|Není nutné. Karty se automaticky rozšiřují, aby se zastavily každých 4 EMS, což je přibližně šířka znaků, které jsou nezávisle na jazyce.|  
|DT_EXTERNALLEADING|Žádný|Není nutné. Vnější přední prostor je vždy zahrnut v řádkování. Tuto <xref:System.Windows.Media.FormattedText.LineHeight%2A> vlastnost použijte k vytvoření uživatelem definovaného řádkování.|  
|DT_HIDEPREFIX|Žádné|Není podporováno. Před vytvořením <xref:System.Windows.Media.FormattedText> objektu odeberte z řetězce ' & '.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Toto je výchozí zarovnání textu. Použijte vlastnost s hodnotou nastavenou na <xref:System.Windows.TextAlignment.Left>. <xref:System.Windows.Media.FormattedText.TextAlignment%2A> (Jenom WPF)|  
|DT_MODIFYSTRING|Žádné|Není podporováno.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|K oříznutí dojde automaticky. Pokud chcete oříznout text, použijte <xref:System.Windows.Media.Visual.VisualClip%2A> vlastnost.|  
|DT_NOFULLWIDTHCHARBREAK|Žádný|Není podporováno.|  
|DT_NOPREFIX|Žádné|Není nutné. Znak ' & ' v řetězcích je vždy považován za běžný znak.|  
|DT_PATHELLIPSIS|Žádný|Použijte vlastnost s hodnotou <xref:System.Windows.TextTrimming.WordEllipsis>. <xref:System.Windows.Media.FormattedText.Trimming%2A>|  
|DT_PREFIX|Žádné|Není podporováno. Pokud chcete použít podtržítka pro text, jako je například klávesa akcelerátoru nebo propojení, použijte <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> metodu.|  
|DT_PREFIXONLY|Žádné|Není podporováno.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použijte vlastnost s hodnotou nastavenou na <xref:System.Windows.TextAlignment.Right>. <xref:System.Windows.Media.FormattedText.TextAlignment%2A> (Jenom WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Nastavte <xref:System.Windows.Media.FormattedText.FlowDirection%2A> vlastnost <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Žádný|Není nutné. <xref:System.Windows.Media.FormattedText>objekty se chovají jako ovládací prvek s jedním řádkem, pokud <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> není buď nastavena vlastnost, nebo text obsahuje znak pro návrat na začátek řádku (CR/LF).|  
|DT_TABSTOP|Žádné|Žádná podpora pro uživatelem definované pozice zarážek tabulátoru.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Není nutné. Hlavní odůvodnění je výchozí. Další hodnoty vertikálního umístění je možné definovat pomocí <xref:System.Windows.Media.FormattedText.Height%2A> vlastnosti k výpočtu příslušné [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozice v rámci jazyka DrawText "y".|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Tuto <xref:System.Windows.Media.FormattedText.Height%2A> vlastnost použijte k výpočtu příslušné [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozice v poli DrawText ' y '.|  
|DT_WORDBREAK|Žádné|Není nutné. K zalamování slov dochází <xref:System.Windows.Media.FormattedText> automaticky s objekty. Nemůžete ho zakázat.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použijte vlastnost s hodnotou <xref:System.Windows.TextTrimming.WordEllipsis>. <xref:System.Windows.Media.FormattedText.Trimming%2A>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.FormattedText>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Vytvoření obrysového textu](how-to-create-outlined-text.md)
- [Postupy: Vytvoření PathGeometry animace pro text](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
