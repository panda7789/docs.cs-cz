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
ms.openlocfilehash: 1e82795afbdd5b1b0a05f95600ebdb92fc134b7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186568"
---
# <a name="drawing-formatted-text"></a>Kreslení formátovaného textu
Toto téma obsahuje přehled funkcí <xref:System.Windows.Media.FormattedText> objektu. Tento objekt poskytuje nízkoúrovňové řízení [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pro kreslení textu v aplikacích.  

## <a name="technology-overview"></a>Přehled technologií  
 Objekt <xref:System.Windows.Media.FormattedText> umožňuje nakreslit víceřádkový text, ve kterém může být každý znak v textu individuálně formátován. Následující příklad ukazuje text, který má několik formátů, které jsou použity na něj.  
  
 ![Text zobrazený pomocí objektu FormattedText](./media/typography-in-wpf/text-formatted-linear-gradient.jpg)  
  
> [!NOTE]
> Pro vývojáře migrující z rozhraní API Win32, tabulka v části [Migrace Win32](#win32_migration) uvádí Win32 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]DrawText příznaky a přibližný ekvivalent v .  
  
### <a name="reasons-for-using-formatted-text"></a>Důvody pro použití formátovaného textu  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsahuje více ovládacích prvků pro kreslení textu na obrazovku. Každý ovládací prvek je zaměřen na jiný scénář a má svůj vlastní seznam funkcí a omezení. Obecně by <xref:System.Windows.Controls.TextBlock> měl být prvek použit v případě, že je vyžadována omezená textová podpora, například stručná věta v rozhraní [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label>lze použít v případě, že je vyžadována minimální podpora textu. Další informace naleznete [v tématu Dokumenty v wpf](documents-in-wpf.md).  
  
 Objekt <xref:System.Windows.Media.FormattedText> poskytuje větší funkce formátování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] textu než ovládací prvky textu a může být užitečný v případech, kdy chcete použít text jako dekorativní prvek. Další informace naleznete v následující části [Převod formátovaného textu na geometrii](#converting_formatted_text).  
  
 Kromě toho <xref:System.Windows.Media.FormattedText> je objekt užitečný pro <xref:System.Windows.Media.DrawingVisual>vytváření objektů odvozených z hlediska textu. <xref:System.Windows.Media.DrawingVisual>je zjednodušená třída kreslení, která slouží k vykreslení obrazců, obrázků nebo textu. Další informace naleznete v [tématu Hit Test Using DrawingVisuals Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Visual%20Layer/DrawingVisual).  
  
## <a name="using-the-formattedtext-object"></a>Použití objektu FormattedText  
 Chcete-li vytvořit formátovaný <xref:System.Windows.Media.FormattedText.%23ctor%2A> text, zavolejte konstruktor u vytvořit <xref:System.Windows.Media.FormattedText> objekt. Po vytvoření počátečního formátovaného textového řetězce můžete použít řadu stylů formátování.  
  
 <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> Vlastností můžete omezit text na určitou šířku. Text se automaticky obtéká, aby nedošlo k překročení zadané šířky. <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> Vlastností můžete omezit text na určitou výšku. V textu se zobrazí tři tečky, "..." pro text, který přesahuje zadanou výšku.  
  
 ![Text zobrazený s wordwrap a tři tečky.](./media/drawing-formatted-text/formatted-text-wordwrap-ellipsis.png)
  
 U jednoho nebo více znaků můžete použít více stylů formátování. Můžete například volat metody <xref:System.Windows.Media.FormattedText.SetFontSize%2A> <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> a pro změnu formátování prvních pěti znaků v textu.  
  
 Následující příklad kódu <xref:System.Windows.Media.FormattedText> vytvoří objekt a potom na text použije několik stylů formátování.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Měrná jednotka velikosti písma  
 Stejně jako u [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jiných <xref:System.Windows.Media.FormattedText> textových objektů v aplikacích objekt používá jako měrnou jednotku pixely nezávislé na zařízení. Většina aplikací Win32 však používá body jako měrnou jednotku. Pokud chcete použít zobrazovaný text v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jednotkách bodů v aplikacích, je třeba převést jednotky nezávislé na zařízení (1/96 palce na jednotku) na body. Následující příklad kódu ukazuje, jak provést tento převod.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>
### <a name="converting-formatted-text-to-a-geometry"></a>Převod formátovaného textu na geometrii  
 Formátovaný text můžete <xref:System.Windows.Media.Geometry> převést na objekty, což vám umožní vytvářet další typy vizuálně zajímavého textu. Můžete například vytvořit <xref:System.Windows.Media.Geometry> objekt založený na obrysu textového řetězce.  
  
 ![Obrys textu pomocí stopy lineárního přechodu](./media/typography-in-wpf/text-outline-linear-gradient.jpg)
  
 Následující příklady ilustrují několik způsobů vytváření zajímavých vizuálních efektů úpravou tahu, výplně a zvýraznění převedeného textu.  
  
 ![Text s různými barvami pro výplň a tah](./media/typography-in-wpf/fill-stroke-text-effect.jpg)  
  
 ![Text s obrazovou stopou aplikovanou na tah](./media/typography-in-wpf/image-brush-application.jpg)
  
 ![Text s obrazovou stopou aplikovanou na tah a zvýraznění](./media/typography-in-wpf/image-brush-text-application.jpg)
  
 Když je text převeden <xref:System.Windows.Media.Geometry> na objekt, už se nejedná o kolekci znaků – znaky v textovém řetězci nelze měnit. Vzhled převedeného textu však můžete ovlivnit úpravou jeho vlastností tahu a výplně. Tah odkazuje na obrys převedeného textu; výplň odkazuje na oblast uvnitř obrysu převedeného textu. Další informace naleznete v [tématu Vytvoření textu s obrysy](how-to-create-outlined-text.md).  
  
 Formátovaný text můžete také <xref:System.Windows.Media.PathGeometry> převést na objekt a použít jej ke zvýraznění textu. Můžete například použít animaci <xref:System.Windows.Media.PathGeometry> na objekt tak, aby animace sledovala obrys formátovaného textu.  
  
 Následující příklad ukazuje formátovaný text, který <xref:System.Windows.Media.PathGeometry> byl převeden na objekt. Animovaná elipsa sleduje cestu tahů vykresleného textu.  
  
 ![Koule za geometrií cesty textu](./media/drawing-formatted-text/sphere-following-geometry-path.gif)  
Koule za geometrií cesty textu  
  
 Další informace naleznete v [tématu How to: Create a PathGeometry Animation for Text](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Po převodu na <xref:System.Windows.Media.PathGeometry> objekt můžete vytvořit další zajímavá použití pro formátovaný text. Můžete například oříznout video, které se zobrazí uvnitř.  
  
 ![Video zobrazené v geometrii cesty textu](./media/drawing-formatted-text/video-displaying-text-path-geometry.png)
  
<a name="win32_migration"></a>
## <a name="win32-migration"></a>Migrace ve win32  
 Funkce <xref:System.Windows.Media.FormattedText> pro kreslení textu jsou podobné funkcím funkce Win32 DrawText. Pro vývojáře migrující z rozhraní API Win32, v následující tabulce jsou uvedeny [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]win32 DrawText příznaky a přibližný ekvivalent v .  
  
|Příznak DrawText|WPF ekvivalent|Poznámky|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Pomocí <xref:System.Windows.Media.FormattedText.Height%2A> této vlastnosti můžete vypočítat příslušnou pozici Win32 DrawText 'y'.|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Pomocí <xref:System.Windows.Media.FormattedText.Height%2A> vlastností a <xref:System.Windows.Media.FormattedText.Width%2A> můžete vypočítat výstupní obdélník.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použijte <xref:System.Windows.Media.FormattedText.TextAlignment%2A> vlastnost s hodnotou <xref:System.Windows.TextAlignment.Center>nastavenou na .|  
|DT_EDITCONTROL|Žádný|Není vyžadováno. Šířka prostoru a vykreslování poslední holčicí čáry jsou stejné jako v ovládacím prvku úpravy architektury.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použijte <xref:System.Windows.Media.FormattedText.Trimming%2A> vlastnost s <xref:System.Windows.TextTrimming.CharacterEllipsis>hodnotou .<br /><br /> Slouží <xref:System.Windows.TextTrimming.WordEllipsis> k získání win32 DT_END_ELLIPSIS s DT_WORD_ELIPSIS koncem tři tečky – v tomto případě znak tři tečky dochází pouze na slova, která se nevejdou na jeden řádek.|  
|DT_EXPAND_TABS|Žádný|Není vyžadováno. Karty jsou automaticky rozbaleny na zastávky každých 4 ems, což je přibližně šířka 8 znaků nezávislých na jazyku.|  
|DT_EXTERNALLEADING|Žádný|Není vyžadováno. Externí proklad je vždy součástí řádkování. <xref:System.Windows.Media.FormattedText.LineHeight%2A> Vlastnost slouží k vytvoření uživatelem definovaných řádkování.|  
|DT_HIDEPREFIX|Žádný|Není podporováno. Před vytvořením <xref:System.Windows.Media.FormattedText> objektu odstraňte "&" z řetězce.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Toto je výchozí zarovnání textu. Použijte <xref:System.Windows.Media.FormattedText.TextAlignment%2A> vlastnost s hodnotou <xref:System.Windows.TextAlignment.Left>nastavenou na . (pouze WPF)|  
|DT_MODIFYSTRING|Žádný|Není podporováno.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Oříznutí se neprovádí automaticky. Pokud chcete oříznout text, <xref:System.Windows.Media.Visual.VisualClip%2A> použijte vlastnost.|  
|DT_NOFULLWIDTHCHARBREAK|Žádný|Není podporováno.|  
|DT_NOPREFIX|Žádný|Není vyžadováno. Znak "&" v řetězcích je vždy považován za normální znak.|  
|DT_PATHELLIPSIS|Žádný|Použijte <xref:System.Windows.Media.FormattedText.Trimming%2A> vlastnost s <xref:System.Windows.TextTrimming.WordEllipsis>hodnotou .|  
|DT_PREFIX|Žádný|Není podporováno. Pokud chcete použít podtržítka pro text, například klávesu akcelerátoru nebo odkaz, použijte metodu. <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A>|  
|DT_PREFIXONLY|Žádný|Není podporováno.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použijte <xref:System.Windows.Media.FormattedText.TextAlignment%2A> vlastnost s hodnotou <xref:System.Windows.TextAlignment.Right>nastavenou na . (pouze WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Nastavte <xref:System.Windows.Media.FormattedText.FlowDirection%2A> vlastnost <xref:System.Windows.FlowDirection.RightToLeft>na .|  
|DT_SINGLELINE|Žádný|Není vyžadováno. <xref:System.Windows.Media.FormattedText>objekty se chovají jako jeden řádkový ovládací prvek, pokud není <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> nastavena vlastnost nebo text neobsahuje posuv řádku vozíku (CR/LF).|  
|DT_TABSTOP|Žádný|Žádná podpora pro uživatelem definované pozice zarážky tabulátoru.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Není vyžadováno. Nejvyšší zarovnání je výchozí. Jiné hodnoty vertikálního polohování lze <xref:System.Windows.Media.FormattedText.Height%2A> definovat pomocí vlastnosti pro výpočet příslušné pozice Win32 DrawText 'y'.|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Pomocí <xref:System.Windows.Media.FormattedText.Height%2A> této vlastnosti můžete vypočítat příslušnou pozici Win32 DrawText 'y'.|  
|DT_WORDBREAK|Žádný|Není vyžadováno. Rozdělení slov se <xref:System.Windows.Media.FormattedText> u objektů automaticky děje. Nelze jej zakázat.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použijte <xref:System.Windows.Media.FormattedText.Trimming%2A> vlastnost s <xref:System.Windows.TextTrimming.WordEllipsis>hodnotou .|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.FormattedText>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Vytvoření obrysového textu](how-to-create-outlined-text.md)
- [Postup: Vytvoření animace PathGeometry pro text](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
