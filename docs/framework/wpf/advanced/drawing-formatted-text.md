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
ms.openlocfilehash: 978c97b8cae24bff4ebdea8f4e56a940e5907fa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="drawing-formatted-text"></a>Kreslení formátovaného textu
Toto téma obsahuje přehled funkce <xref:System.Windows.Media.FormattedText> objektu. Tento objekt poskytuje nízké úrovně řízení pro kreslení textu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace.  
  
  
## <a name="technology-overview"></a>Přehled technologie  
 <xref:System.Windows.Media.FormattedText> Objekt umožňuje kreslení víceřádkový text, ve kterém lze jednotlivé znaky v textu jednotlivě formátovat. Následující příklad ukazuje, text, který má několik formáty použité k němu.  
  
 ![Text zobrazený pomocí objektu FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext01.jpg "FormattedText01")  
Pomocí metody FormattedText zobrazovaného textu  
  
> [!NOTE]
>  Pro tyto vývojáře migrace z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] rozhraní API, v tabulce v [Win32 migrace](#win32_migration) části seznamy [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText příznaky a přibližný ekvivalent v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
### <a name="reasons-for-using-formatted-text"></a>Důvody pro použití formátovaný Text  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje více ovládacích prvků pro kreslení textu na obrazovce. Každý ovládací prvek je zaměřena na jiný scénář a má svou vlastní seznam funkcí a omezení. Obecně <xref:System.Windows.Controls.TextBlock> element byste měli použít, pokud text omezenou podporu vyžadovat, například stručný věty v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> můžete použít, když je potřebná podpora minimální text. Další informace najdete v tématu [dokumenty v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
 <xref:System.Windows.Media.FormattedText> Objekt poskytuje větší funkcí než formátování textu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ovládacích prvků textu a může být užitečné v případech, ve které chcete použít jako element dekorativní text. Další informace najdete v následující části [převod formátu textu na objekt Geometry](#converting_formatted_text).  
  
 Kromě toho <xref:System.Windows.Media.FormattedText> objektu je užitečné pro vytváření orientované na text <xref:System.Windows.Media.DrawingVisual>-odvozené objekty. <xref:System.Windows.Media.DrawingVisual> je lightweight kreslení třídu, která se použije k vykreslení tvarů, Image nebo text. Další informace najdete v tématu [ukázka průchodu testu DrawingVisuals](http://go.microsoft.com/fwlink/?LinkID=159994).  
  
## <a name="using-the-formattedtext-object"></a>Pomocí objektu FormattedText  
 Chcete-li vytvořit formátovaný text, zavolejte <xref:System.Windows.Media.FormattedText.%23ctor%2A> konstruktor k vytvoření <xref:System.Windows.Media.FormattedText> objektu. Po vytvoření počáteční formátovaný textový řetězec, můžete použít řadu formátování stylů.  
  
 Použití <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> vlastnost Omezit text konkrétní šířky. Aby nedošlo k překročení nastavená šířka budou automaticky zahrnovat text. Použití <xref:System.Windows.Media.FormattedText.MaxTextHeight%2A> vlastnost Omezit text, který se určité výšky. Text se zobrazí třemi tečkami "..." pro text, který je delší než zadaná výška.  
  
 ![Text zobrazený pomocí objektu FormattedText](../../../../docs/framework/wpf/advanced/media/formattedtext02.png "FormattedText02")  
Zobrazí text zobrazující zalamování řádků a třemi tečkami  
  
 Více formátování styly můžete aplikovat na jeden nebo více znaků. Například může volat i <xref:System.Windows.Media.FormattedText.SetFontSize%2A> a <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> metody pro změnu formátování prvních 5 znaků v textu.  
  
 Následující příklad kódu vytvoří <xref:System.Windows.Media.FormattedText> objektu a pak použije několik formátování stylů na text.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]  
  
### <a name="font-size-unit-of-measure"></a>Měrné jednotky velikosti písma  
 Stejně jako u jiných objektů text v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, <xref:System.Windows.Media.FormattedText> objektu používá jako měrné jednotky nezávislé na zařízení pixelů. Ale většina [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikace používají body jako měrné jednotky. Pokud chcete použít zobrazovaný text v jednotkách body v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace, musíte převést [!INCLUDE[TLA#tla_dipixel#plural](../../../../includes/tlasharptla-dipixelsharpplural-md.md)] do bodů. Následující příklad kódu ukazuje, jak provést tento převod.  
  
 [!code-csharp[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets2)]
 [!code-vb[FormattedTextSnippets#FormattedTextSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets2)]  
  
<a name="converting_formatted_text"></a>   
### <a name="converting-formatted-text-to-a-geometry"></a>Převádění formátovaného textu geometrie  
 Formátovaný text do můžete převést <xref:System.Windows.Media.Geometry> objekty, umožňuje vytvářet jiné typy zajímavé vizuální text. Například můžete vytvořit <xref:System.Windows.Media.Geometry> objektu podle obrys textového řetězce.  
  
 ![Osnova text použití štětce přechodu lineární](../../../../docs/framework/wpf/advanced/media/outlinedtext02.jpg "OutlinedText02")  
Osnova text použití lineární štětce přechodu  
  
 Následující příklady ilustrují několik způsobů vytvoření zajímavé vizuální efekty úpravou tahu, výplň a zvýraznění převedený textu.  
  
 ![Text pomocí různých barev pro výplně a tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext03.jpg "OutlinedText03")  
Příklad nastavení tahu a vyplňte pro různé barev  
  
 ![Text s štětce bitové kopie u tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext04.jpg "OutlinedText04")  
Příklad štětce bitové kopie u tahu  
  
 ![Text s štětce bitové kopie u tahu](../../../../docs/framework/wpf/advanced/media/outlinedtext05.jpg "OutlinedText05")  
Příklad štětce obrázku použita pro tahu a zvýraznění  
  
 Když se text bude převeden na <xref:System.Windows.Media.Geometry> objektu je již kolekce znaků – nelze upravit znaků v textovém řetězci. Však může ovlivnit vzhled text převedený změnou vlastností tahu a výplně. Tahu odkazuje na obrys text převedený; výplně odkazuje na oblasti uvnitř obrys text převedený. Další informace najdete v tématu [vytvořit uvedených Text](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md).  
  
 Formátovaný text, který lze převést <xref:System.Windows.Media.PathGeometry> objektu a použít objekt pro zvýraznění textu. Například může použít animace <xref:System.Windows.Media.PathGeometry> objektu tak, aby animace následuje obrys formátovaný text.  
  
 Následující příklad ukazuje formátovaný text, který byl převeden na <xref:System.Windows.Media.PathGeometry> objektu. Animovaný elipsy sleduje cestu tahy vykreslené textu.  
  
 ![Následující cesta geometrie textu oblasti](../../../../docs/framework/wpf/advanced/media/textpathgeometry01.gif "TextPathGeometry01")  
Oblasti následující cesta geometrie textu  
  
 Další informace najdete v tématu [postupy: vytvoření PathGeometry animace textu](http://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67).  
  
 Jakmile byl převeden na můžete vytvořit další zajímavé použití pro formátovaný text <xref:System.Windows.Media.PathGeometry> objektu. Můžete například oříznutí video, které zobrazí uvnitř ho.  
  
 ![Grafické zobrazení v geometrické cesta textu](../../../../docs/framework/wpf/advanced/media/videotextdemo01.png "VideoTextDemo01")  
Grafické zobrazení v geometrické cesta textu  
  
<a name="win32_migration"></a>   
## <a name="win32-migration"></a>Migrace Win32  
 Funkce <xref:System.Windows.Media.FormattedText> pro kreslení textu jsou podobné funkce [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText funkce. Pro tyto vývojáře migraci z [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] rozhraní API, následující tabulka uvádí [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DrawText příznaky a přibližný ekvivalent v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
|Příznak DrawText|Ekvivalentní WPF|Poznámky|  
|-------------------|--------------------|-----------|  
|DT_BOTTOM|<xref:System.Windows.Media.FormattedText.Height%2A>|Použití <xref:System.Windows.Media.FormattedText.Height%2A> vlastnost k výpočtu odpovídající [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozice DrawText "y".|  
|DT_CALCRECT|<xref:System.Windows.Media.FormattedText.Height%2A>, <xref:System.Windows.Media.FormattedText.Width%2A>|Použití <xref:System.Windows.Media.FormattedText.Height%2A> a <xref:System.Windows.Media.FormattedText.Width%2A> vlastnosti, které chcete vypočítat rámeček výstup.|  
|DT_CENTER|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použití <xref:System.Windows.Media.FormattedText.TextAlignment%2A> vlastnost nastavená na hodnotu <xref:System.Windows.TextAlignment.Center>.|  
|DT_EDITCONTROL|Žádné|Není požadováno. Šířka mezery a poslední řádek vykreslování jsou že stejné jako v rámci ovládacích prvků pro úpravy.|  
|DT_END_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použití <xref:System.Windows.Media.FormattedText.Trimming%2A> vlastnosti s hodnotou <xref:System.Windows.TextTrimming.CharacterEllipsis>.<br /><br /> Použití <xref:System.Windows.TextTrimming.WordEllipsis> získat [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] DT_END_ELLIPSIS s DT_WORD_ELIPSIS ukončení třemi tečkami – v takovém případě znaku tří teček dochází pouze na slova, která se nevejdou na jeden řádek.|  
|DT_EXPAND_TABS|Žádné|Není požadováno. Karty jsou automaticky rozšířena do zastaví každé 4 ems, což je přibližně šířku 8 znaků nezávislé na jazyku.|  
|DT_EXTERNALLEADING|Žádné|Není požadováno. Externí úvodní je vždy součástí mezery mezi řádky. Použití <xref:System.Windows.Media.FormattedText.LineHeight%2A> vlastnost vytvořit uživatelem definované mezer.|  
|DT_HIDEPREFIX|Žádné|Není podporováno. Před vytvořením odeberte 'a' z řetězce <xref:System.Windows.Media.FormattedText> objektu.|  
|DT_LEFT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Toto je výchozí zarovnání textu. Použití <xref:System.Windows.Media.FormattedText.TextAlignment%2A> vlastnost nastavená na hodnotu <xref:System.Windows.TextAlignment.Left>. (Jenom WPF)|  
|DT_MODIFYSTRING|Žádné|Není podporováno.|  
|DT_NOCLIP|<xref:System.Windows.Media.Visual.VisualClip%2A>|Výstřižek neprobíhá automaticky. Pokud chcete klip textu, použijte <xref:System.Windows.Media.Visual.VisualClip%2A> vlastnost.|  
|DT_NOFULLWIDTHCHARBREAK|Žádné|Není podporováno.|  
|DT_NOPREFIX|Žádné|Není požadováno. 'A' znaků v řetězcích vždy považuje za normální znak.|  
|DT_PATHELLIPSIS|Žádné|Použití <xref:System.Windows.Media.FormattedText.Trimming%2A> vlastnosti s hodnotou <xref:System.Windows.TextTrimming.WordEllipsis>.|  
|DT_PREFIX|Žádné|Není podporováno. Pokud chcete použít podtržítka pro text, například klávesa akcelerátoru nebo odkaz, použijte <xref:System.Windows.Media.FormattedText.SetTextDecorations%2A> metoda.|  
|DT_PREFIXONLY|Žádné|Není podporováno.|  
|DT_RIGHT|<xref:System.Windows.Media.FormattedText.TextAlignment%2A>|Použití <xref:System.Windows.Media.FormattedText.TextAlignment%2A> vlastnost nastavená na hodnotu <xref:System.Windows.TextAlignment.Right>. (Jenom WPF)|  
|DT_RTLREADING|<xref:System.Windows.Media.FormattedText.FlowDirection%2A>|Nastavte <xref:System.Windows.Media.FormattedText.FlowDirection%2A> vlastnost <xref:System.Windows.FlowDirection.RightToLeft>.|  
|DT_SINGLELINE|Žádné|Není požadováno. <xref:System.Windows.Media.FormattedText> objekty chovat jako ovládací prvek jeden řádek, pokud buď <xref:System.Windows.Media.FormattedText.MaxTextWidth%2A> je nastavena nebo text obsahuje znak vrátit/odřádkování (CR/LF).|  
|DT_TABSTOP|Žádné|Žádná podpora pro uživatelem definované karta zastavení pozic.|  
|DT_TOP|<xref:System.Windows.Media.FormattedText.Height%2A>|Není požadováno. Horní zarovnání do bloku je výchozí. Ostatní svislé umístění hodnoty lze definovat pomocí <xref:System.Windows.Media.FormattedText.Height%2A> vlastnost k výpočtu odpovídající [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozice DrawText "y".|  
|DT_VCENTER|<xref:System.Windows.Media.FormattedText.Height%2A>|Použití <xref:System.Windows.Media.FormattedText.Height%2A> vlastnost k výpočtu odpovídající [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pozice DrawText "y".|  
|DT_WORDBREAK|Žádné|Není požadováno. Rozdělování slov se automaticky stane s <xref:System.Windows.Media.FormattedText> objekty. Nelze zakázat ho.|  
|DT_WORD_ELLIPSIS|<xref:System.Windows.Media.FormattedText.Trimming%2A>|Použití <xref:System.Windows.Media.FormattedText.Trimming%2A> vlastnosti s hodnotou <xref:System.Windows.TextTrimming.WordEllipsis>.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.FormattedText>  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Typografie v rozhraní WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Vytvoření obrysového textu](../../../../docs/framework/wpf/advanced/how-to-create-outlined-text.md)  
 [Postupy: vytvoření animace PathGeometry pro Text](http://msdn.microsoft.com/library/29f8051e-798a-463f-a926-a099a99e9c67)
