---
title: 'Optimalizace výkonu: Text'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rendering text [WPF]
- hyperlinks [WPF]
- formatted text [WPF]
- text [WPF], performance
- glyphs [WPF]
ms.assetid: 66b1b9a7-8618-48db-b616-c57ea4327b98
ms.openlocfilehash: 3e729458538353499f27f95ea2ca37fea1335238
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740351"
---
# <a name="optimizing-performance-text"></a>Optimalizace výkonu: Text

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahrnuje podporu pro prezentaci textu obsahu prostřednictvím použití ovládacích prvků s bohatou [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]í funkcí. Vykreslování textu můžete obecně rozdělit ve třech vrstvách:

1. Použití objektů <xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun> přímo.

2. Použití objektu <xref:System.Windows.Media.FormattedText>.

3. Použití ovládacích prvků na nejvyšší úrovni, například <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument> objektů.

Toto téma poskytuje doporučení pro výkon vykreslování textu.

<a name="Glyph_Level"></a>

## <a name="rendering-text-at-the-glyph-level"></a>Vykreslování textu na úrovni glyfů

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje rozšířenou podporu textu včetně značek na úrovni glyfů s přímým přístupem k <xref:System.Windows.Documents.Glyphs> pro zákazníky, kteří chtějí zachytit a uchovat text po formátování. Tyto funkce poskytují kritickou podporu pro různé požadavky na vykreslování textu v každém z následujících scénářů.

- Zobrazení dokumentů s pevným formátem

- Scénáře tisku.

  - [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] jako jazyk tiskárny zařízení.

  - Zapisovač dokumentů Microsoft XPS.

  - Předchozí ovladače tiskáren, výstup z aplikací Win32 do pevného formátu.

  - Formát zařazování tisku.

- Reprezentace dokumentu s pevným formátem, včetně klientů pro předchozí verze Windows a dalších výpočetních zařízení.

> [!NOTE]
> <xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun> jsou navržené pro scénáře informaování a tisku dokumentů s pevným formátováním. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje několik prvků pro obecné rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] scénáře, jako je například <xref:System.Windows.Controls.Label> a <xref:System.Windows.Controls.TextBlock>. Další informace o scénářích rozložení a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] najdete v tématu [Typografie v](typography-in-wpf.md)subsystému WPF.

Následující příklady ukazují, jak definovat vlastnosti pro objekt <xref:System.Windows.Documents.Glyphs> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Objekt <xref:System.Windows.Documents.Glyphs> představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. V příkladech se předpokládá, že písma Arial, Courier New a Times New Roman se nainstalují do složky **C:\WINDOWS\Fonts** v místním počítači.

[!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]

### <a name="using-drawglyphrun"></a>Použití DrawGlyphRun

Pokud máte vlastní ovládací prvek a chcete vykreslit glyfy, použijte metodu <xref:System.Windows.Media.DrawingContext.DrawGlyphRun%2A>.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také poskytuje služby nižší úrovně pro vlastní formátování textu prostřednictvím použití objektu <xref:System.Windows.Media.FormattedText>. Nejúčinnější způsob vykreslování textu v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je vygenerování textového obsahu na úrovni glyfu pomocí <xref:System.Windows.Documents.Glyphs> a <xref:System.Windows.Media.GlyphRun>. Náklady na tuto efektivitu však představují ztrátu snadno použitelného formátování textu, což jsou integrované funkce [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ch ovládacích prvků, jako jsou <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument>.

<a name="FormattedText_Object"></a>

## <a name="formattedtext-object"></a>Objekt FormattedText

Objekt <xref:System.Windows.Media.FormattedText> umožňuje nakreslit víceřádkový text, ve kterém je každý znak v textu možné formátovat individuálně. Další informace najdete v tématu [Kreslení formátovaného textu](drawing-formatted-text.md).

Chcete-li vytvořit formátovaný text, zavolejte konstruktor <xref:System.Windows.Media.FormattedText.%23ctor%2A> pro vytvoření objektu <xref:System.Windows.Media.FormattedText>. Po vytvoření počátečního formátovaného textového řetězce můžete použít rozsah stylů formátování. Pokud vaše aplikace chce implementovat své vlastní rozložení, je objekt <xref:System.Windows.Media.FormattedText> lepší volbou, než použití ovládacího prvku, jako je například <xref:System.Windows.Controls.TextBlock>. Další informace o objektu <xref:System.Windows.Media.FormattedText> najdete v tématu [Kreslení formátovaného textu](drawing-formatted-text.md) .

Objekt <xref:System.Windows.Media.FormattedText> poskytuje možnost formátování textu na nízké úrovni. Můžete použít více stylů formátování na jeden nebo více znaků. Například můžete zavolat metody <xref:System.Windows.Media.FormattedText.SetFontSize%2A> a <xref:System.Windows.Media.FormattedText.SetForegroundBrush%2A> a změnit tak formátování prvních pět znaků v textu.

Následující příklad kódu vytvoří objekt <xref:System.Windows.Media.FormattedText> a vykreslí ho.

[!code-csharp[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/FormattedTextSnippets/CSharp/Window1.xaml.cs#formattedtextsnippets1)]
[!code-vb[formattedtextsnippets#FormattedTextSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FormattedTextSnippets/visualbasic/window1.xaml.vb#formattedtextsnippets1)]

<a name="FlowDocument_TextBlock_Label"></a>

## <a name="flowdocument-textblock-and-label-controls"></a>Ovládací prvky FlowDocument, TextBlock a Label

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje několik ovládacích prvků pro vykreslení textu na obrazovku. Každý ovládací prvek je zaměřený na jiný scénář a má svůj vlastní seznam funkcí a omezení.

### <a name="flowdocument-impacts-performance-more-than-textblock-or-label"></a>FlowDocument má dopad na výkon větší než TextBlock nebo popisek

Obecně platí, že element <xref:System.Windows.Controls.TextBlock> by měl být použit, pokud je vyžadována podpora omezeného textu, jako je například krátká věta v [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. <xref:System.Windows.Controls.Label> lze použít, pokud je požadována minimální podpora textu. Element <xref:System.Windows.Documents.FlowDocument> je kontejner pro znovu natékáné dokumenty, které podporují bohatou prezentaci obsahu, a proto má větší dopad na výkon než při použití ovládacích prvků <xref:System.Windows.Controls.TextBlock> nebo <xref:System.Windows.Controls.Label>.

Další informace o <xref:System.Windows.Documents.FlowDocument>najdete v tématu [Přehled dokumentů Flow](flow-document-overview.md).

### <a name="avoid-using-textblock-in-flowdocument"></a>Nepoužívejte TextBlock v FlowDocument

Element <xref:System.Windows.Controls.TextBlock> je odvozen od <xref:System.Windows.UIElement>. Element <xref:System.Windows.Documents.Run> je odvozen od <xref:System.Windows.Documents.TextElement>, což je méně nákladné pro použití než objekt odvozený <xref:System.Windows.UIElement>. Pokud je to možné, použijte <xref:System.Windows.Documents.Run> místo <xref:System.Windows.Controls.TextBlock> pro zobrazení textového obsahu v <xref:System.Windows.Documents.FlowDocument>.

Následující ukázka kódu znázorňuje dva způsoby nastavení textového obsahu v rámci <xref:System.Windows.Documents.FlowDocument>:

[!code-xaml[Performance#PerformanceSnippet13](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/FlowDocument.xaml#performancesnippet13)]

### <a name="avoid-using-run-to-set-text-properties"></a>Nepoužívejte rutinu Run k nastavení vlastností textu

Obecně platí, že použití <xref:System.Windows.Documents.Run> v rámci <xref:System.Windows.Controls.TextBlock> je vyšší výkon, než když vůbec nepoužíváte explicitní <xref:System.Windows.Documents.Run> objekt. Pokud používáte <xref:System.Windows.Documents.Run> pro nastavení vlastností textu, nastavte tyto vlastnosti přímo na <xref:System.Windows.Controls.TextBlock> místo toho.

Následující ukázka kódu znázorňuje tyto dva způsoby nastavení vlastnosti text, v tomto případě vlastnost <xref:System.Windows.Controls.TextBlock.FontWeight%2A>:

[!code-xaml[Performance#PerformanceSnippet12](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml#performancesnippet12)]

V následující tabulce jsou uvedeny náklady na zobrazení 1000 <xref:System.Windows.Controls.TextBlock> objektů s explicitním <xref:System.Windows.Documents.Run>a bez něj.

|**Typ TextBlock**|**Čas vytvoření (MS)**|**Čas vykreslování (MS)**|
|------------------------|------------------------------|----------------------------|
|Vlastnosti textu pro nastavení spuštění|146|540|
|Vlastnosti textu nastavení TextBlock|43|453|

### <a name="avoid-databinding-to-the-labelcontent-property"></a>Vyhněte se vazbě na vlastnost Label. Content.

Představte si situaci, kdy máte objekt <xref:System.Windows.Controls.Label>, který se často aktualizuje ze zdroje <xref:System.String>. Když data sváže vlastnost <xref:System.Windows.Controls.ContentControl.Content%2A> elementu <xref:System.Windows.Controls.Label> ke zdrojovému objektu <xref:System.String>, může docházet ke špatnému výkonu. Pokaždé, když se aktualizuje zdrojový <xref:System.String>, starý objekt <xref:System.String> se zahodí a nové <xref:System.String> se znovu vytvoří, protože objekt <xref:System.String> je neměnný a nedá se změnit. Tím dojde k tomu, že <xref:System.Windows.Controls.ContentPresenter> objektu <xref:System.Windows.Controls.Label> zahodí původní obsah a znovu vygeneruje nový obsah pro zobrazení nového <xref:System.String>.

Řešení tohoto problému je jednoduché. Pokud <xref:System.Windows.Controls.Label> není nastavena na hodnotu vlastní <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>, nahraďte <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBlock> a data sváže jeho vlastnost <xref:System.Windows.Controls.TextBlock.Text%2A> se zdrojovým řetězcem.

|**Vlastnost vázaná na data**|**Čas aktualizace (MS)**|
|-----------------------------|----------------------------|
|Label.Content|835|
|TextBlock. text|242|

<a name="Hyperlink"></a>

## <a name="hyperlink"></a>Hypertextový odkaz

Objekt <xref:System.Windows.Documents.Hyperlink> je element obsahu toku na úrovni inline, který umožňuje hostovat hypertextové odkazy v rámci obsahu toku.

### <a name="combine-hyperlinks-in-one-textblock-object"></a>Kombinování hypertextových odkazů v jednom objektu TextBlock

Můžete optimalizovat použití více <xref:System.Windows.Documents.Hyperlink> prvků seskupením do stejného <xref:System.Windows.Controls.TextBlock>. To pomáhá minimalizovat počet objektů, které vytvoříte v aplikaci. Například můžete chtít zobrazit více hypertextových odkazů, například následující:

MSN domů &#124; můj MSN

Následující příklad kódu ukazuje více <xref:System.Windows.Controls.TextBlock> prvků, které slouží k zobrazení hypertextových odkazů:

[!code-xaml[Performance#PerformanceSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet9)]

Následující příklad kódu ukazuje efektivnější způsob zobrazení hypertextových odkazů, tentokrát pomocí jednoho <xref:System.Windows.Controls.TextBlock>:

[!code-xaml[Performance#PerformanceSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet10)]

### <a name="showing-underlines-on-hyperlinks-only-on-mouseenter-events"></a>Zobrazení podtržení na hypertextových odkazech pouze u událostí MouseEnter

Objekt <xref:System.Windows.TextDecoration> je vizuální ozdobné, které lze přidat do textu; může však být náročné na výkon při vytváření instancí. Pokud provedete rozsáhlé použití <xref:System.Windows.Documents.Hyperlink> prvků, zvažte zobrazení podtržení pouze při aktivaci události, jako je například událost <xref:System.Windows.ContentElement.MouseEnter>. Další informace najdete v tématu [určení, zda je hypertextový odkaz podtržený](how-to-specify-whether-a-hyperlink-is-underlined.md).

Následující obrázek ukazuje, jak událost MouseEnter aktivuje podtržený hypertextový odkaz:

![Hypertextové odkazy zobrazující TextDecorations](./media/how-to-specify-whether-a-hyperlink-is-underlined/text-decorations-hyperlinks.png)

Následující ukázka kódu ukazuje <xref:System.Windows.Documents.Hyperlink> definována s podtržením a bez něj:

[!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]

V následující tabulce jsou uvedeny náklady na výkon při zobrazení 1000 <xref:System.Windows.Documents.Hyperlink> prvků s podtržením a bez něj.

|**Cíl**|**Čas vytvoření (MS)**|**Čas vykreslování (MS)**|
|-------------------|------------------------------|----------------------------|
|S podtržením|289|1130|
|Bez podtržení|299|776|

<a name="Text_Formatting_Features"></a>

## <a name="text-formatting-features"></a>Funkce formátování textu

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje služby formátování formátovaného textu, například automatické dělení slov. Tyto služby mohou ovlivnit výkon aplikace a měly by být použity pouze v případě potřeby.

### <a name="avoid-unnecessary-use-of-hyphenation"></a>Vyhnout se zbytečnému použití dělení slov

Automatické dělení slov najde zarážky spojovníků pro řádky textu a umožňuje další pozice zalomení řádků v <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Documents.FlowDocument>ch objektů. Ve výchozím nastavení je funkce Automatické dělení slov v těchto objektech zakázaná. Tuto funkci můžete povolit nastavením vlastnosti IsHyphenationEnabled objektu na `true`. Povolení této funkce však způsobí, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zahájí interoperabilitu modelu objektu komponenty (COM), což může mít vliv na výkon aplikace. Doporučuje se, abyste automatické dělení nepoužívali, pokud ho nepotřebujete.

### <a name="use-figures-carefully"></a>Pečlivě používejte obrázky

Element <xref:System.Windows.Documents.Figure> představuje část obsahu toku, která může být absolutně umístěna v rámci stránky obsahu. V některých případech může <xref:System.Windows.Documents.Figure> způsobit, že se celá stránka automaticky přeformátuje, pokud její poloha koliduje s obsahem, který už je stanovený. Můžete minimalizovat možnost zbytečného přeformátování buď seskupením <xref:System.Windows.Documents.Figure> prvků vedle sebe, nebo jejich deklaraci v blízkosti horního okraje obsahu ve scénáři s pevnou velikostí stránky.

### <a name="optimal-paragraph"></a>Optimální odstavec

Funkce optimálního odstavce objektu <xref:System.Windows.Documents.FlowDocument> stanoví odstavce tak, aby prázdné znaky byly co nejblíže rozmístěné. Ve výchozím nastavení je funkce optimálního odstavce zakázána. Tuto funkci můžete povolit nastavením vlastnosti <xref:System.Windows.Documents.FlowDocument.IsOptimalParagraphEnabled%2A> objektu na `true`. Povolení této funkce však ovlivní výkon aplikace. Doporučuje se, abyste funkci optimálních odstavců nepoužívali, pokud ji nepotřebujete.

## <a name="see-also"></a>Viz také:

- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
