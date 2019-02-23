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
ms.openlocfilehash: a4337eeb3db940b0000301465a6f912ed3ed5805
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748463"
---
# <a name="drawing-formatted-text"></a>Kreslení formátovaného textu
Toto téma obsahuje přehled funkce <xref:System.Windows.Media.FormattedText> objektu. Tento objekt lze podrobně pro kreslení textu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací.  
  
  
## <a name="technology-overview"></a>Přehled technologie  
 <xref:System.Windows.Media.FormattedText> Objekt umožňuje nakreslit více řádky textu, ve kterém každý znak v textu jednotlivě naformátovaná. Následující příklad ukazuje, text, který má několik formátů použit.  
  
 ![Text zobrazený pomocí objektu FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
Zobrazený text pomocí FormattedText – metoda  
  
> [!NOTE]
>  Pro tyto vývojáře migrace z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] rozhraní API tabulky [Win32 migrace](#win32_migration) části seznamy [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText příznaky a přibližný ekvivalent v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Důvody pro použití formátovaný Text  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnuje více ovládacích prvků pro vykreslení textu na obrazovce. Každý ovládací prvek je zacílený na jiný scénář a má svůj vlastní seznam funkcí a omezení. Obecně platí <xref:System.Windows.Controls.TextBlock> element by měl použít, pokud je text omezená podpora vyžadovat, například stručný větu v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> lze použít, když je nutné podporovat minimální text. Další informace najdete v tématu [dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 <xref:System.Windows.Media.FormattedText> Objekt, který poskytuje větší funkcí než formátování textu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] textových ovládacích prvků a může být užitečné v případech, ve které chcete použít jako prvek dekorativní text. Další informace najdete v části [převádění textu ve formátu pro geometrii](#converting_formatted_text).  
  
 Kromě toho <xref:System.Windows.Media.FormattedText> objektu je užitečné pro vytváření orientovaný text <xref:System.Windows.Media.DrawingVisual>-odvozené objekty. <xref:System.Windows.Media.DrawingVisual> je zjednodušené výkresu třídu, která se použije k vykreslení obrazce, Image nebo text. Další informace najdete v tématu [ukázka spuštění testu DrawingVisuals](https://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Pomocí objektu FormattedText  
 Chcete-li vytvořit formátovaný text, zavolejte <xref:System.Windows.Media.FormattedText.%23ctor%2A> konstruktor k vytvoření <xref:System.Windows.Media.FormattedText> objektu. Po vytvoření počáteční formátovaný řetězec, můžete použít celou řadu formátování styly.  
  
 Použití <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> vlastnost Omezit text na konkrétní šířku. Aby nedošlo k překročení nastavená šířka se automaticky zalomí text. Použití <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> vlastnost Omezit text na konkrétní výšce. Text se zobrazí tři tečky "..." pro text, který překračuje zadaný výška.  
  
 ![Text zobrazený pomocí objektu FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
Zobrazí text zobrazující zalamování řádků a tlačítko se třemi tečkami  
  
 Můžete změnit více styl na jeden nebo více znaků. Například lze zavolat i <xref:System.Windows.Media.FormattedText.SetFontSize%2A> a <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metody, chcete-li změnit formátování prvních pěti znaků v textu.  
  
 Následující příklad kódu vytvoří <xref:System.Windows.Media.FormattedText> objekt a potom nainstaluje několik stylů formátování textu.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Měrné jednotky velikosti písma  
 Stejně jako u jiných textových objektů v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací, <xref:System.Windows.Media.FormattedText> objekt pixelech nezávislých na zařízení používá jako měrné jednotky. Nicméně většina [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikací používají body jako měrné jednotky. Pokud chcete použít zobrazení textu v jednotkách, které body v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, musíte převést [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] do bodů. Následující příklad kódu ukazuje, jak provést tento převod.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Převod formátovaného textu pro geometrii  
 Můžete převést formátovaný text do <xref:System.Windows.Media.Geometry> objekty, které umožňuje vytvoření jiných typů vizuálně zajímavou text. Například můžete vytvořit <xref:System.Windows.Media.Geometry> objektu podle obrysu textového řetězce.  
  
 ![Text osnovy pomocí štětec lineárního přechodu](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Text osnovy pomocí štětec lineárního přechodu  
  
 Následující příklady znázorňují několik možností, jak vytvářet zajímavé vizuální efekty úpravou stroke, výplň a zvýraznit text převedený.  
  
 ![Text mají různé barvy výplně a stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Příklad nastavení tahu a výplně různé barvy  
  
 ![Text s obrázkový štětec u stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Příklad obrázkový štětec u tahu  
  
 ![Text s obrázkový štětec u stroke](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Příklad obrázkový štětec, který je použitý ke stroke a zvýraznění  
  
 Pokud je text převést na <xref:System.Windows.Media.Geometry> objektu, není již sadu znaků – nelze upravit znaků v textovém řetězci. Můžete však vliv na vzhled text převedený úpravou jeho vlastností tahu a výplně. Protože byl zdvih odkazuje na osnovy převedený textu. Výplň odkazuje na oblast uvnitř osnovy text převedený. Další informace najdete v tématu [vytvořit uvedených Text](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md).  
  
 Můžete také převést formátovaný text, který má <xref:System.Windows.Media.PathGeometry> objektu a použití objektu pro zvýraznění textu. Například můžete použít pro animaci <xref:System.Windows.Media.PathGeometry> objektu tak, aby se animace Následuje přehled formátovaný text.  
  
 Následující příklad ukazuje formátovaný text, který byl převeden na <xref:System.Windows.Media.PathGeometry> objektu. Animovaný elipsa sleduje cestu tahů vykresleného textu.  
  
 ![Sphere následující cestu geometrii textu](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.gif "TextPathGeometry01")  
Sphere následující cestu geometrii textu  
  
 Další informace najdete v tématu [jak: Vytvořit animaci PathGeometry textu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100)).  
  
 Jakmile se převedlo na můžete vytvořit další zajímavé způsoby využití formátovaný text <xref:System.Windows.Media.PathGeometry> objektu. Například můžete oříznout video k zobrazení dovnitř.  
  
 ![Zobrazení videa v geometrické cesty textu](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
Zobrazení videa v geometrické cesty textu  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migrace Win32  
 Funkce <xref:System.Windows.Media.FormattedText> pro kreslení textu jsou podobné funkce [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText funkce. Pro tyto vývojáře migrace z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] rozhraní API, následující tabulce jsou uvedeny [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText příznaky a přibližný ekvivalent v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Příznak DrawText|Ekvivalent WPF|Poznámky|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Použití <xref:System.Windows.Media.FormattedText.Height%2A> vlastnost pro výpočet odpovídající [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozice DrawText "y".|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Použití <xref:System.Windows.Media.FormattedText.Height%2A> a <xref:System.Windows.Media.FormattedText.Width%2A> vlastnosti pro výpočet výstupu obdélník.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použití <xref:System.Windows.Media.FormattedText.TextAlignment%2A> vlastnost nastavená na hodnotu <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Žádná|Není nutné. Šířka mezery a poslední řádek vykreslení jsou že stejné jako v rámci ovládacích prvků pro úpravy.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použití <xref:System.Windows.Media.FormattedText.Trimming%2A> vlastnost s hodnotou <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Použití <xref:System.Windows.TextTrimming.WordEllipsis> zobrazíte [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS s DT_WORD_ELIPSIS ukončit tlačítko se třemi tečkami – v takovém případě znak tlačítko se třemi tečkami dochází jenom na slova, která se nevejdou na jednom řádku.|  
|DT_EXPAND_TABS|Žádná|Není nutné. Karty jsou automaticky rozšíří na přestane každé 4 ems, což je přibližně šířku 8 znaků nezávislým na jazyku.|  
|DT_EXTERNALLEADING|Žádná|Není nutné. Externí nejlepší je vždy součástí mezer. Použití <xref:System.Windows.Media.FormattedText.LineHeight%2A> vlastnost vytvořit uživatelem definované mezer.|  
|DT_HIDEPREFIX|Žádná|Není podporováno. Odeberte 'a' z řetězce před sestavením <xref:System.Windows.Media.FormattedText> objektu.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Toto je výchozí zarovnání textu. Použití <xref:System.Windows.Media.FormattedText.TextAlignment%2A> vlastnost nastavená na hodnotu <xref:System.Windows.TextAlignment.Left>. (Pouze WPF)|  
|DT_MODIFYSTRING|Žádná|Není podporováno.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Výstřižek neprobíhá automaticky. Pokud chcete do Galerie textu, použijte <xref:System.Windows.Media.Visual.VisualClip%2A> vlastnost.|  
|DT_NOFULLWIDTHCHARBREAK|Žádná|Není podporováno.|  
|DT_NOPREFIX|Žádná|Není nutné. Znak '&' v řetězcích je vždy považován za normálních znaků.|  
|DT_PATHELLIPSIS|Žádná|Použití <xref:System.Windows.Media.FormattedText.Trimming%2A> vlastnost s hodnotou <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Žádná|Není podporováno. Pokud chcete použít podtržítka pro text, například klíče akcelerátoru nebo odkaz, použijte <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> metody.|  
|DT_PREFIXONLY|Žádná|Není podporováno.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použití <xref:System.Windows.Media.FormattedText.TextAlignment%2A> vlastnost nastavená na hodnotu <xref:System.Windows.TextAlignment.Right>. (Pouze WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Nastavte <xref:System.Windows.Media.FormattedText.FlowDirection%2A> vlastnost <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Žádná|Není nutné. <xref:System.Windows.Media.FormattedText> objekty se chovají jako ovládací prvek jeden řádek, pokud buď <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> je nastavena nebo text obsahuje návrat na začátek řádku vrátit/odřádkování (CR/LF).|  
|DT_TABSTOP|Žádná|Bez podpory pro uživatelem definované stop tabulátorů.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Není nutné. Začátek zarovnání do bloku je výchozí nastavení. Ostatní svislé umístění hodnoty lze definovat pomocí <xref:System.Windows.Media.FormattedText.Height%2A> vlastnost pro výpočet odpovídající [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozice DrawText "y".|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Použití <xref:System.Windows.Media.FormattedText.Height%2A> vlastnost pro výpočet odpovídající [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozice DrawText "y".|  
|DT_WORDBREAK|Žádná|Není nutné. Dělení slov se automaticky stane s <xref:System.Windows.Media.FormattedText> objekty. Nebudete je moct zakázat.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použití <xref:System.Windows.Media.FormattedText.Trimming%2A> vlastnost s hodnotou <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.FormattedText>
- [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
- [Typografie v rozhraní WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
- [Vytvoření obrysového textu](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)
- [Postupy: Vytvořit animaci PathGeometry pro Text](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms743610(v=vs.100))
