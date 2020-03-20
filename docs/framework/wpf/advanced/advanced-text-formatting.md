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
ms.openlocfilehash: 745d20e0bd4f877f9d4559f9fc7829b56689d35c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185932"
---
# <a name="advanced-text-formatting"></a>Upřesněné formátování textu
Windows Presentation Foundation (WPF) poskytuje robustní sadu api pro zahrnutí textu do aplikace. Rozložení [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] a rozhraní API, například <xref:System.Windows.Controls.TextBlock>, poskytují nejběžnější a obecné použití prvků pro textovou prezentaci. Kreslicí <xref:System.Windows.Media.GlyphRunDrawing> prostředí <xref:System.Windows.Media.FormattedText>API, například a , poskytují prostředky pro zahrnutí formátovaného textu do výkresů. Na nejpokročilejší úrovni wpf poskytuje rozšiřitelný modul formátování textu pro řízení každého aspektu textové prezentace, jako je například správa úložiště textu, správa formátování spouštění textu a správa vložených objektů.  
  
 Toto téma obsahuje úvod do formátování textu WPF. Zaměřuje se na implementaci klienta a použití wpf modulu pro formátování textu.  
  
> [!NOTE]
> Všechny příklady kódu v tomto dokumentu naleznete v [ukázce](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI/TextFormatting)formátování rozšířeného textu .  

<a name="prereq"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste obeznámeni s vyšší úrovní api používané pro textovou prezentaci. Většina uživatelských scénářů nebude vyžadovat rozhraní API pro formátování rozšířeného textu, která jsou popsána v tomto tématu. Úvod k různým textovým apim naleznete [v tématu Dokumenty v wpf](documents-in-wpf.md).  
  
<a name="section1"></a>
## <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Rozložení textu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] a ovládací prvky v wpf poskytují vlastnosti formátování, které umožňují snadno zahrnout formátovaný text v aplikaci. Tyto ovládací prvky vystavit řadu vlastností pro zpracování prezentace textu, který zahrnuje jeho písmo, velikost a barvu. Za běžných okolností tyto ovládací prvky můžete zpracovat většinu textové prezentace ve vaší aplikaci. Některé pokročilé scénáře však vyžadují kontrolu nad ukládáním textu i textovou prezentací. WPF poskytuje rozšiřitelný modul formátování textu pro tento účel.  
  
 Pokročilé funkce formátování textu, které se nacházejí v wpf, se skládají z modulu formátování textu, úložiště textu, spuštění textu a vlastností formátování. Modul formátování textu , <xref:System.Windows.Media.TextFormatting.TextFormatter>vytvoří řádky textu, které se použijí pro prezentaci. Toho je dosaženo zahájením procesu formátování linky a voláním <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>textu formátu . Formátformát textu načte text běží z úložiště textu <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> voláním metody úložiště. Objekty <xref:System.Windows.Media.TextFormatting.TextRun> jsou pak <xref:System.Windows.Media.TextFormatting.TextLine> vytvořeny do objektů formátovacím formátovacím formátem textu a dány vaší aplikaci pro kontrolu nebo zobrazení.  
  
<a name="section2"></a>
## <a name="using-the-text-formatter"></a>Použití formátovatevač textu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>je modul formátování textu WPF a poskytuje služby pro formátování a rozdělení řádků textu. Formátovací modul textu může zpracovat různé formáty znaků textu a odstavcové styly a zahrnuje podporu pro mezinárodní rozložení textu.  
  
 Na rozdíl od tradičního textového <xref:System.Windows.Media.TextFormatting.TextFormatter> rozhraní API interaguje s klientem rozložení textu prostřednictvím sady metod zpětného volání. Vyžaduje, aby klient poskytnout tyto metody <xref:System.Windows.Media.TextFormatting.TextSource> v implementaci třídy. Následující diagram znázorňuje interakci rozložení textu <xref:System.Windows.Media.TextFormatting.TextFormatter>mezi klientskou aplikací a aplikací .  
  
 ![Diagram klienta rozložení textu a textformatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Formátovací modul textu se používá k načtení formátovaných řádků textu <xref:System.Windows.Media.TextFormatting.TextSource>z úložiště textu, což je implementace aplikace . To se provádí nejprve vytvořením instance formátovace textu pomocí <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> metody. Tato metoda vytvoří instanci formátatele textu a nastaví maximální hodnoty výšky a šířky čáry. Jakmile je vytvořena instance formátač textu, proces vytvoření řádku je <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> spuštěn voláním metody. <xref:System.Windows.Media.TextFormatting.TextFormatter>volá zpět do zdroje textu k načtení textu a parametrů formátování pro spuštění textu, které tvoří řádek.  
  
 V následujícím příkladu je zobrazen proces formátování úložiště textu. Objekt <xref:System.Windows.Media.TextFormatting.TextFormatter> se používá k načtení řádků textu z úložiště textu a <xref:System.Windows.Media.DrawingContext>následnému formátování řádku textu pro kreslení do .  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>
## <a name="implementing-the-client-text-store"></a>Implementace úložiště textu klienta  
 Při rozšíření modulu formátování textu, budete muset implementovat a spravovat všechny aspekty úložiště textu. To není triviální úkol. Úložiště textu je zodpovědné za sledování vlastností spuštění textu, vlastností odstavce, vložených objektů a dalšího podobného obsahu. Poskytuje také formátanový formát <xref:System.Windows.Media.TextFormatting.TextRun> textu s jednotlivými objekty, které formátformátformáttextu textu používá k vytvoření <xref:System.Windows.Media.TextFormatting.TextLine> objektů.  
  
 Pro zpracování virtualizace úložiště textu musí být úložiště textu <xref:System.Windows.Media.TextFormatting.TextSource>odvozeno od . <xref:System.Windows.Media.TextFormatting.TextSource>definuje metodu, kterou formátmodul textu používá k načtení schodů textu z úložiště textu. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>je metoda používaná formátovacím formátovacím formátem textu k načtení schráží textu používaných při formátování řádků. Volání <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> je opakovaně provádí formátací textu, dokud nedojde k jedné z následujících podmínek:  
  
- A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> nebo podtřída je vrácena.  
  
- Akumulovaná šířka spuštěného textu překračuje maximální šířku řádku zadanou v volání k vytvoření formátovače textu nebo volání <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody formátovače textu.  
  
- Je vrácena nová sekvence unicode, například "CF", "LF" nebo "CRLF".  
  
<a name="section4"></a>
## <a name="providing-text-runs"></a>Poskytování spuštění textu  
 Jádrem procesu formátování textu je interakce mezi formátovacím formátovacím formátem textu a úložištěm textu. Implementace <xref:System.Windows.Media.TextFormatting.TextSource> poskytuje formátovací modul text <xref:System.Windows.Media.TextFormatting.TextRun> s objekty a vlastnosti, s nimiž se formátovat text spustí. Tato interakce je <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> zpracována metodou, která je volána formátovat text.  
  
 V následující tabulce jsou uvedeny některé předdefinované <xref:System.Windows.Media.TextFormatting.TextRun> objekty.  
  
|TextSpustit typ|Využití|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Spustit specializovaný text slouží k předání reprezentace znakových glyfů zpět do formátovaní textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Spuštění specializovaného textu slouží k poskytování obsahu, ve kterém se provádí měření, testování přístupů a kreslení v celku, například tlačítko nebo obrázek v textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Spuštění specializovaného textu slouží k označení konce řádku.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Spuštění specializovaného textu slouží k označení konce odstavce.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Spuštění specializovaného textu slouží k označení konce segmentu, například k <xref:System.Windows.Media.TextFormatting.TextModifier> ukončení oboru ovlivněného předchozím spuštěním.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Spuštění specializovaného textu slouží k označení rozsahu skrytých znaků.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Spuštění specializovaného textu používaného k úpravě vlastností textu běží v jeho oboru. Obor se rozšíří na <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> další odpovídající text <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>spustit nebo další .|  
  
 Kterýkoli z předdefinovaných <xref:System.Windows.Media.TextFormatting.TextRun> objektů lze podřadit. To umožňuje zdroj textu poskytnout formátanový modul textu s textem spustí, které obsahují vlastní data.  
  
 Následující příklad ukazuje <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metodu. Toto úložiště <xref:System.Windows.Media.TextFormatting.TextRun> textu vrátí objekty formátovací modul pro zpracování.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> V tomto příkladu poskytuje úložiště textu stejné vlastnosti textu pro všechny text. Úložiště rozšířeného textu by bylo nutné implementovat vlastní správu rozsahu, aby jednotlivé znaky měly různé vlastnosti.  
  
<a name="section5"></a>
## <a name="specifying-formatting-properties"></a>Určení vlastností formátování  
 <xref:System.Windows.Media.TextFormatting.TextRun>objekty jsou formátovány pomocí vlastností poskytovaných úložištěm textu. Tyto vlastnosti jsou <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> dodávány ve dvou typech a <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>zpracování odstavce včetně <xref:System.Windows.TextAlignment> vlastností, jako jsou a <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties>jsou vlastnosti, které se mohou lišit pro každý text spuštěný v odstavci, například stopa <xref:System.Windows.Media.Typeface>popředí a velikost písma. Chcete-li implementovat vlastní odstavec a vlastní text spustit <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> <xref:System.Windows.Media.TextFormatting.TextRunProperties> typy vlastností, aplikace musí vytvořit třídy, které jsou odvozeny od a respektive.  
  
## <a name="see-also"></a>Viz také

- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
