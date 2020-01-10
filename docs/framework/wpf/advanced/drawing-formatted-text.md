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
ms.openlocfilehash: c786137a471e0199a8ac60f8d82b4ce440e33b7e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740394"
---
# <a name="drawing-formatted-text"></a>Kreslení formátovaného textu
Toto téma obsahuje přehled funkcí objektu <xref:System.Windows.Media.FormattedText>. Tento objekt poskytuje ovládací prvky nízké úrovně pro vykreslování textu v aplikacích [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

## <a name="technology-overview"></a>Přehled technologie  
 Objekt <xref:System.Windows.Media.FormattedText> umožňuje nakreslit víceřádkový text, ve kterém je každý znak v textu možné formátovat individuálně. Následující příklad ukazuje text, který obsahuje několik formátů, které jsou na něj aplikovány.  
  
 ![Text zobrazený pomocí objektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Pro vývojáře, kteří migrují z Win32 API, tabulka v oddílu [migrace do Win32](#win32_migration) uvádí příznaky Win32 DrawText a přibližný ekvivalent v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Důvody pro použití formátovaného textu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje několik ovládacích prvků pro vykreslení textu na obrazovku. Každý ovládací prvek je zaměřený na jiný scénář a má svůj vlastní seznam funkcí a omezení. Obecně platí, že element <xref:System.Windows.Controls.TextBlock> by měl být použit, pokud je vyžadována podpora omezeného textu, jako je například krátká věta v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> lze použít, pokud je požadována minimální podpora textu. Další informace najdete v tématu [dokumenty v WPF](documents-in-wpf.md).  
  
 Objekt <xref:System.Windows.Media.FormattedText> poskytuje větší funkce formátování textu než ovládací prvky [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] textu a může být užitečné v případech, kdy chcete text použít jako dekorativní prvek. Další informace naleznete v následující části [převedení formátovaného textu na geometrii](#converting_formatted_text).  
  
 Kromě toho objekt <xref:System.Windows.Media.FormattedText> je užitečný pro vytváření objektů odvozených <xref:System.Windows.Media.DrawingVisual>m orientovaném na text. <xref:System.Windows.Media.DrawingVisual> je zjednodušená třída pro kreslení, která se používá k vykreslování tvarů, obrázků nebo textu. Další informace najdete v tématu [test přístupů pomocí DrawingVisuals Sample](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Použití objektu FormattedText  
 Chcete-li vytvořit formátovaný text, zavolejte konstruktor <xref:System.Windows.Media.FormattedText.%23ctor%2A> pro vytvoření objektu <xref:System.Windows.Media.FormattedText>. Po vytvoření počátečního formátovaného textového řetězce můžete použít rozsah stylů formátování.  
  
 Vlastnost <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> slouží k omezení textu na konkrétní šířku. Text se automaticky zalomí, aby nedošlo k překročení zadané šířky. Chcete-li omezit text na určitou výšku, použijte vlastnost <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A>. V textu se zobrazí tři tečky, "..." pro text, který překračuje zadanou výšku.  
  
 ![Text zobrazený pomocí WordWrap a tři tečky](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)    
  
 Můžete použít více stylů formátování na jeden nebo více znaků. Například můžete zavolat metody <xref:System.Windows.Media.FormattedText.SetFontSize%2A> a <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> a změnit tak formátování prvních pět znaků v textu.  
  
 Následující příklad kódu vytvoří objekt <xref:System.Windows.Media.FormattedText> a poté použije pro text několik stylů formátování.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Měrná jednotka velikosti písma  
 Stejně jako u jiných textových objektů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ch aplikacích používá objekt <xref:System.Windows.Media.FormattedText> jako měrnou jednotku pixely nezávislé na zařízení. Většina aplikací Win32 však jako měrnou jednotku používá body. Pokud chcete v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ch aplikacích použít text zobrazený v jednotkách bodů, je nutné převést jednotky nezávislé na zařízení (1/1/96 palce na jednotku) na body. Následující příklad kódu ukazuje, jak provést tento převod.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Převod formátovaného textu na geometrii  
 Formátovaný text můžete převést na <xref:System.Windows.Media.Geometry> objekty, což vám umožní vytvořit další typy vizuálně zajímavého textu. Můžete například vytvořit objekt <xref:System.Windows.Media.Geometry> na základě obrysu textového řetězce.  
  
 ![Obrys textu s použitím štětce s lineárním přechodem](./media/typography-in-wpf/text-outline-linear-gradient.jpg)    
  
 Následující příklady ilustrují několik způsobů vytváření zajímavých vizuálních efektů úpravou tahu, výplně a zvýraznění převedeného textu.  
  
 ![Text s různými barvami pro výplň a tah](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Text s obrázkem štětce aplikovaný na tah](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Text s obrázkem štětce aplikovaný na tah a zvýraznění](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Když je text převeden na objekt <xref:System.Windows.Media.Geometry>, již není kolekcí znaků, nelze upravit znaky v textovém řetězci. Vzhled převedeného textu však můžete ovlivnit úpravou vlastností tahu a výplně. Tah odkazuje na obrys převedeného textu; Výplň odkazuje na oblast uvnitř obrysu převedeného textu. Další informace najdete v tématu [Vytvoření obrysového textu](how-to-create-outlined-text.md).  
  
 Můžete také převést formátovaný text na objekt <xref:System.Windows.Media.PathGeometry> a použít objekt pro zvýraznění textu. Například můžete použít animaci na objekt <xref:System.Windows.Media.PathGeometry> tak, aby animace vychází z obrysu formátovaného textu.  
  
 Následující příklad ukazuje formátovaný text, který byl převeden na objekt <xref:System.Windows.Media.PathGeometry>. Animovaná elipsa následuje po cestě k vykreslenému textu.  
  
 ![Koule následující po geometrii cesty textu](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Koule následující po geometrii cesty textu  
  
 Další informace najdete v tématu [Postup: vytvoření PathGeometry animace pro text](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Po převedení na objekt <xref:System.Windows.Media.PathGeometry> můžete pro formátovaný text vytvořit další zajímavá použití. Můžete například oříznout video, které se zobrazí v něm.  
  
 ![Video, které se zobrazuje v geometrii cesty textu](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migrace Win32  
 Funkce <xref:System.Windows.Media.FormattedText> pro kreslení textu jsou podobné funkcím funkce Win32 DrawText. Pro vývojáře, kteří migrují z Win32 API, v následující tabulce jsou uvedeny příznaky Win32 DrawText a přibližný ekvivalent v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Příznak DrawText|Ekvivalent WPF|Poznámky|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Vlastnost <xref:System.Windows.Media.FormattedText.Height%2A> použijte k výpočtu vhodné pozice y v systému Win32 DrawText.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Pomocí vlastností <xref:System.Windows.Media.FormattedText.Height%2A> a <xref:System.Windows.Media.FormattedText.Width%2A> můžete vypočítat výstupní obdélník.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použijte vlastnost <xref:System.Windows.Media.FormattedText.TextAlignment%2A> s hodnotou nastavenou na hodnotu <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Žádné|Není nutné. Šířka prostoru a vykreslení posledního řádku jsou stejné jako v ovládacím prvku pro úpravy rozhraní.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použijte vlastnost <xref:System.Windows.Media.FormattedText.Trimming%2A> s hodnotou <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Použití <xref:System.Windows.TextTrimming.WordEllipsis> k získání DT_END_ELLIPSIS Win32 se třemi tečkami DT_WORD_ELIPSIS – v tomto případě se tři tečky vyskytují jenom na slovech, která se nevejdou na jeden řádek.|  
|DT_EXPAND_TABS|Žádné|Není nutné. Karty se automaticky rozšiřují, aby se zastavily každých 4 EMS, což je přibližně šířka znaků, které jsou nezávisle na jazyce.|  
|DT_EXTERNALLEADING|Žádné|Není nutné. Vnější přední prostor je vždy zahrnut v řádkování. Vlastnost <xref:System.Windows.Media.FormattedText.LineHeight%2A> slouží k vytvoření uživatelem definovaného řádkování.|  
|DT_HIDEPREFIX|Žádné|Není podporováno. Před vytvořením objektu <xref:System.Windows.Media.FormattedText> z řetězce odeberte ' & '.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Toto je výchozí zarovnání textu. Použijte vlastnost <xref:System.Windows.Media.FormattedText.TextAlignment%2A> s hodnotou nastavenou na hodnotu <xref:System.Windows.TextAlignment.Left>. (Jenom WPF)|  
|DT_MODIFYSTRING|Žádné|Není podporováno.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|K oříznutí dojde automaticky. Pokud chcete oříznout text, použijte vlastnost <xref:System.Windows.Media.Visual.VisualClip%2A>.|  
|DT_NOFULLWIDTHCHARBREAK|Žádné|Není podporováno.|  
|DT_NOPREFIX|Žádné|Není nutné. Znak ' & ' v řetězcích je vždy považován za běžný znak.|  
|DT_PATHELLIPSIS|Žádné|Použijte vlastnost <xref:System.Windows.Media.FormattedText.Trimming%2A> s hodnotou <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Žádné|Není podporováno. Pokud chcete použít podtržítka pro text, jako je například klávesa akcelerátoru nebo propojení, použijte metodu <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>.|  
|DT_PREFIXONLY|Žádné|Není podporováno.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použijte vlastnost <xref:System.Windows.Media.FormattedText.TextAlignment%2A> s hodnotou nastavenou na hodnotu <xref:System.Windows.TextAlignment.Right>. (Jenom WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Nastavte <xref:System.Windows.Media.FormattedText.FlowDirection%2A> vlastnost <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Žádné|Není nutné. <xref:System.Windows.Media.FormattedText> objektů se chová jako ovládací prvek s jedním řádkem, pokud není nastavena vlastnost <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> nebo text obsahuje znak návratu nebo řádku pro návrat na začátek řádku (CR/LF).|  
|DT_TABSTOP|Žádné|Žádná podpora pro uživatelem definované pozice zarážek tabulátoru.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Není nutné. Hlavní odůvodnění je výchozí. Další hodnoty vertikálního umístění je možné definovat pomocí vlastnosti <xref:System.Windows.Media.FormattedText.Height%2A> k výpočtu vhodné pozice y v systému Win32 DrawText.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Vlastnost <xref:System.Windows.Media.FormattedText.Height%2A> použijte k výpočtu vhodné pozice y v systému Win32 DrawText.|  
|DT_WORDBREAK|Žádné|Není nutné. K zalamování slov dochází automaticky <xref:System.Windows.Media.FormattedText> objekty. Nemůžete ho zakázat.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použijte vlastnost <xref:System.Windows.Media.FormattedText.Trimming%2A> s hodnotou <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.FormattedText>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Vytvoření obrysového textu](how-to-create-outlined-text.md)
- [Postupy: vytvoření PathGeometry animace pro text](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
