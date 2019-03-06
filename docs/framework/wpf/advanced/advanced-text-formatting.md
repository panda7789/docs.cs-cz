---
title: Upřesněné formátování textu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
ms.openlocfilehash: 7d2408104ee3cf206734c5a1904129c3b71f7229
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368230"
---
# <a name="advanced-text-formatting"></a>Upřesněné formátování textu
Windows Presentation Foundation (WPF) poskytuje robustní sadu [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] pro včetně textu ve vaší aplikaci. Rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], jako například <xref:System.Windows.Controls.TextBlock>zadejte nejběžnější a obecné použití prvků pro textové prezentaci. Kreslení [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], jako například <xref:System.Windows.Media.GlyphRunDrawing> a <xref:System.Windows.Media.FormattedText>, prostředkem pro zahrnutí do kreslení formátovaného textu. Nanejvýš pokročilé úrovni členství, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje formátování k řízení všech aspektů text prezentací, jako jsou Správa úložiště text, správa formátování textových spuštění a správa vložený objekt rozšiřitelné textu.  
  
 Toto téma obsahuje úvod do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formátování textu. Zaměřuje se na implementace klienta a použití [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formátování textu.  
  
> [!NOTE]
>  Všechny příklady kódu v tomto dokumentu najdete v [Advanced ukázka formátování textu](https://go.microsoft.com/fwlink/?LinkID=159965).  
  

  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že máte zkušenosti s vyšší úrovní [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] použit pro textové prezentaci. Většina uživatelských scénářích nebude vyžadovat formátování textu pokročilé [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] popsané v tomto tématu. Úvod do různých text [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], naleznete v tématu [dokumenty v platformě WPF](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Rozložení textu a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládacích prvků v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytnout vlastností formátování, které umožňují snadno zahrnout formátovaný text ve vaší aplikaci. Tyto ovládací prvky zveřejňují počet vlastností ke zpracování prezentace text, který zahrnuje jeho písmo, velikost a barvu. Za běžných okolností dokáže zpracovat tyto ovládací prvky většinou textové prezentaci ve vaší aplikaci. Některé pokročilé scénáře však vyžadují ovládacího prvku textové úložiště, stejně jako textové prezentaci. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsahuje formátování pro tento účel extensible textu.  
  
 Pokročilé funkce formátování textu v nalezen [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsahují text formátování modul, text úložiště, spuštění textu a formátování vlastnosti. Formátování, textu <xref:System.Windows.Media.TextFormatting.TextFormatter>, vytvoří řádků textu má být použit pro prezentaci. Toho dosáhnete pomocí Zahajování procesu formátování řádku a volání formátování textu <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. Formátování textu načte spuštění text ze svého úložiště text zavoláním obchodu <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody. <xref:System.Windows.Media.TextFormatting.TextRun> Objekty jsou pak uspořádané do <xref:System.Windows.Media.TextFormatting.TextLine> objekty podle formátování textu a vzhledem k aplikaci pro kontrolu nebo zobrazení.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Použití formátování textu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> je [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formátování textu motoru a poskytuje služby pro formátování a rozdělení řádky textu. Formátování textu dokáže zpracovat jiným textovým formátování a styly odstavec a zahrnuje podporu pro mezinárodní text rozložení.  
  
 Na rozdíl od tradičních text [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> komunikuje přes sadu metod zpětného volání klienta rozložení textu. Vyžaduje od klienta tyto metody v implementaci <xref:System.Windows.Media.TextFormatting.TextSource> třídy. Následující diagram znázorňuje interakci rozložení textu mezi klientskou aplikací a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta rozložení textu a objektu TextFormatter](./media/textformatter01.png "TextFormatter01")  
Interakce mezi aplikací a objektu TextFormatter  
  
 Formátování textu slouží k načtení řádky formátovaný text z textového úložiště, což je implementace <xref:System.Windows.Media.TextFormatting.TextSource>. To vytvořením první instance formátování textu pomocí provádí <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> metody. Tato metoda vytvoří instanci formátovacího modulu text a nastaví řádku maximální výšku a šířku. Jakmile je vytvořena instance formátování textu, proces vytváření řádek se spustí volání <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody. <xref:System.Windows.Media.TextFormatting.TextFormatter> zavolá zpět do zdroje textu k načtení textu a formátování parametry pro spuštění textu, které tvoří řádku.  
  
 V následujícím příkladu se zobrazí proces formátování textu úložiště. <xref:System.Windows.Media.TextFormatting.TextFormatter> Objektu se používá k načtení řádky textu z textového úložiště a pak formátovat řádek textu pro kreslení do <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementace Store Text klienta  
 Když rozšíříte modul formátování textu, jsou nutné k implementaci a správě všech aspektů úložišti text. Toto není jednoduchý úkol. Text úložiště zodpovídá za sledování spuštění vlastnosti, vlastnosti odstavce, vložené objekty a další podobné obsah textu. Poskytuje také formátování textu u jednotlivých <xref:System.Windows.Media.TextFormatting.TextRun> objekty, které text formátovací modul používá k vytvoření <xref:System.Windows.Media.TextFormatting.TextLine> objekty.  
  
 Pro zpracování virtualizace úložiště textu, textu úložiště musí být odvozen od <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource> definuje metodu, kterou používá formátování textu k načtení textu spuštění z úložiště text. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> je metoda používá formátování textu k načtení textu pracuje použitých ve formátování řádku. Volání <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> opakovaně provede nástroj formátování textu dokud nenastane některá z následujících podmínek:  
  
-   A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> nebo je vrácena podtřídy.  
  
-   Součet šířka textu spuštění překračuje maximální řádku šířce zadané ve volání vytvoření formátování textu nebo formátování textu volání <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metoda.  
  
-   A [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] sekvence znaku nového řádku, jako je například "CF", "LF" nebo "CRLF", je vrácena.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Toky poskytování textu  
 Základní proces formátování textu je interakce mezi úložiště textu a formátování textu. Implementace <xref:System.Windows.Media.TextFormatting.TextSource> poskytuje formátování textu s <xref:System.Windows.Media.TextFormatting.TextRun> objektů a vlastností, pomocí kterých se mají formátovat text běží. Tato interakce se zpracovává souborem <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody, které je voláno rozhraním formátování textu.  
  
 V následující tabulce jsou uvedeny některé z předdefinovaných <xref:System.Windows.Media.TextFormatting.TextRun> objekty.  
  
|TextRun Type|Použití|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Specializované text spustit slouží k předání reprezentace znaku glyfy formátování textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Spusťte slouží k poskytování obsahu v které měření, testování průchodu specializované text a vykreslování se provádí jako celek, jako je například tlačítko nebo obrázek v textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Specializované text spustit slouží k označení konce řádku.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Specializované text spustit slouží k označení konce odstavce.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Specializované text spustit používá k označení konce segmentu, například na konec rozsahu ovlivněny předchozí <xref:System.Windows.Media.TextFormatting.TextModifier> spustit.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Specializované text spustit slouží k označení rozsahu znaků skryté.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Specializované text spustit slouží k úpravě vlastností textu se spouští ve svém oboru. Rozsah rozšiřuje na další odpovídající <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> text spustit nebo další <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Kteroukoli z předdefinovaných <xref:System.Windows.Media.TextFormatting.TextRun> objekty mohou být rozčlenit do podtříd. Text zdroje k poskytování že formátování textu s textem spouští, včetně vlastních dat díky tomu.  
  
 Následující příklad ukazuje <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody. Vrátí toto úložiště text <xref:System.Windows.Media.TextFormatting.TextRun> objekty k formátování textu pro zpracování.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  V tomto příkladu text úložiště poskytuje stejné vlastnosti text pro veškerý text. Pokročilé text, který ukládá by bylo potřeba implementovat vlastní span management umožňuje mít různé vlastnosti jednotlivých znaků.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Zadání vlastnosti formátování  
 <xref:System.Windows.Media.TextFormatting.TextRun> objekty jsou formátovány pomocí vlastnosti poskytované třídou úložiště text. Tyto vlastnosti se dělí na dva typy <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> a <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> zpracovat odstavec včetně vlastnosti, jako <xref:System.Windows.TextAlignment> a <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties> jsou vlastnosti, které mohou být různé pro každý text spouštět v rámci odstavce, jako jsou štětce popředí <xref:System.Windows.Media.Typeface>a velikost písma. K implementaci vlastních odstavec a spustit typy vlastností vlastního textu, musí aplikace vytvořit třídy, které jsou odvozeny z <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> a <xref:System.Windows.Media.TextFormatting.TextRunProperties> v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:
- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
