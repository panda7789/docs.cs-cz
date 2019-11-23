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
ms.openlocfilehash: 2c120c6d71cb22bc38909f980b2f6faf2b5c3663
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395221"
---
# <a name="advanced-text-formatting"></a>Upřesněné formátování textu
Windows Presentation Foundation (WPF) poskytuje robustní sadu rozhraní API pro zahrnutí textu do aplikace. Rozhraní API pro rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], jako je například <xref:System.Windows.Controls.TextBlock>, poskytují nejběžnější a obecné prvky použití pro textovou prezentaci. Kreslicí rozhraní API, například <xref:System.Windows.Media.GlyphRunDrawing> a <xref:System.Windows.Media.FormattedText>, poskytují způsob, jak zahrnout formátovaný text do kreseb. Na nejvyšší úrovni [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje nástroj rozšiřitelného formátování textu pro řízení všech aspektů textové prezentace, jako je Správa úložiště textu, Správa formátování textových běhů a Správa vložených objektů.  
  
 Toto téma poskytuje Úvod do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formátování textu. Zaměřuje se na implementaci klienta a použití nástroje pro formátování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ho textu.  
  
> [!NOTE]
> Všechny příklady kódu v tomto dokumentu najdete v [ukázce Rozšířené formátování textu](https://go.microsoft.com/fwlink/?LinkID=159965).  

<a name="prereq"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že máte zkušenosti s rozhraními API vyšší úrovně použitými pro textovou prezentaci. Většina uživatelských scénářů nebude vyžadovat rozhraní API pro rozšířené formátování textu popsané v tomto tématu. Úvod do různých textových rozhraní API naleznete [v tématu dokumenty v WPF](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Ovládací prvky rozložení textu a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytují vlastnosti formátování, které umožňují snadno zahrnout formátovaný text do aplikace. Tyto ovládací prvky zpřístupňují několik vlastností, které umožňují zpracování prezentace textu, včetně řezu písma, velikosti a barvy. V běžných případech tyto ovládací prvky mohou ve vaší aplikaci zpracovat většinu textových prezentací. Některé pokročilé scénáře však vyžadují řízení ukládání textu a prezentaci textu. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje pro tento účel nástroj rozšiřitelného formátování textu.  
  
 Funkce Rozšířené formátování textu nalezené v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sestávají z modulu formátování textu, textového úložiště, textu a vlastností formátování. Modul formátování textu, <xref:System.Windows.Media.TextFormatting.TextFormatter>, vytvoří řádky textu, které se mají použít pro prezentaci. Toho je dosaženo inicializací procesu formátování řádku a voláním <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>formátovacího modulu textu. Formátování textu načte text spouštěný z vašeho textového úložiště voláním metody <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> Storu. Objekty <xref:System.Windows.Media.TextFormatting.TextRun> jsou poté vytvořeny do <xref:System.Windows.Media.TextFormatting.TextLine> objektů pomocí formátovacího modulu textu a dány vaší aplikaci pro kontrolu nebo zobrazení.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Použití formátovacího textu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter> je modul pro formátování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] textu a poskytuje služby pro formátování a zalamování textových řádků. Formátování textu může zpracovávat různé formáty textových znaků a odstavcové styly a zahrnuje podporu pro mezinárodní rozložení textu.  
  
 Na rozdíl od tradičního textového rozhraní API <xref:System.Windows.Media.TextFormatting.TextFormatter> komunikuje s klientem rozložení textu prostřednictvím sady metod zpětného volání. Vyžaduje, aby klient poskytoval tyto metody v implementaci třídy <xref:System.Windows.Media.TextFormatting.TextSource>. Následující diagram znázorňuje interakci rozložení textu mezi klientskou aplikací a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta rozložení textu a TextFormatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Formátování textu se používá k načtení formátovaných textových řádků z úložiště textu, což je implementace <xref:System.Windows.Media.TextFormatting.TextSource>. To se provádí tak, že nejprve vytvoříte instanci formátování textu pomocí metody <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>. Tato metoda vytvoří instanci formátování textu a nastaví maximální hodnoty výšky a šířky čáry. Jakmile je vytvořena instance formátování textu, je proces vytvoření řádku spuštěn voláním metody <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. <xref:System.Windows.Media.TextFormatting.TextFormatter> volání zpět do zdroje textu pro načtení textu a formátovacích parametrů pro spuštění textu, který tvoří čáru.  
  
 V následujícím příkladu se zobrazuje proces formátování textového úložiště. Objekt <xref:System.Windows.Media.TextFormatting.TextFormatter> slouží k načtení textových řádků z úložiště textu a následnému formátování řádku textu pro kreslení do <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementace úložiště textu klienta  
 Když rozšíříte modul formátování textu, je nutné implementovat a spravovat všechny aspekty v úložišti textu. Nejedná se o triviální úlohu. Úložiště textu zodpovídá za sledování vlastností běhu textu, vlastností odstavce, vložených objektů a dalšího podobného obsahu. Poskytuje také formátovací text s jednotlivými <xref:System.Windows.Media.TextFormatting.TextRun> objekty, které formátovací modul textu používá k vytvoření <xref:System.Windows.Media.TextFormatting.TextLine> objektů.  
  
 Aby bylo možné zpracovat virtualizaci textového úložiště, musí být úložiště textu odvozeno od <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource> definuje metodu, kterou formátovací modul textu používá k načtení textových běhů z úložiště textu. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> je metoda, kterou formátovací modul textu používá k načtení textových běhů používaných při formátování čáry. Volání <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> je opakovaně provedeno pomocí formátovacího modulu textu, dokud nedojde k jedné z následujících podmínek:  
  
- Vrátí <xref:System.Windows.Media.TextFormatting.TextEndOfLine> nebo podtřídu.  
  
- Kumulovaná šířka textu je větší než maximální tloušťka čáry zadaná v volání pro vytvoření formátovacího textu nebo volání metody formátování textu <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>.  
  
- Vrátí se sekvence nového řádku Unicode, například "CF", "LF" nebo "CRLF".  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Poskytování textových běhů  
 Základem procesu formátování textu je interakce mezi formátováním textu a úložištěm textu. Vaše implementace <xref:System.Windows.Media.TextFormatting.TextSource> poskytuje formátování textu pomocí objektů <xref:System.Windows.Media.TextFormatting.TextRun> a vlastností, které mají formátovat text. Tato interakce je zpracována metodou <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>, která je volána pomocí formátovacího modulu textu.  
  
 V následující tabulce jsou uvedeny některé z předdefinovaných <xref:System.Windows.Media.TextFormatting.TextRun> objektů.  
  
|Typ TextRun|Využití|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Specializovaný text, který se používá k předání reprezentace znaků glyfů zpátky do formátovacího modulu textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Specializovaný text, který se používá k poskytnutí obsahu při měření, testování přístupů a vykreslování, se provádí v celém rozsahu, jako je například tlačítko nebo obrázek v rámci textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Slouží ke spuštění specializovaného textu k označení konce řádku.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Slouží ke spuštění specializovaného textu, který označuje konec odstavce.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Slouží ke spuštění specializovaného textu k označení konce segmentu, například k ukončení rozsahu ovlivněného předchozí <xref:System.Windows.Media.TextFormatting.TextModifier> spuštění.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Pomocí specializovaného textu lze označit rozsah skrytých znaků.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Použití specializovaného textu, který slouží k úpravě vlastností textu, se spouští ve svém rozsahu. Rozsah se rozšíří na další vyhovující <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> text, nebo na další <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Kterýkoli z předdefinovaných <xref:System.Windows.Media.TextFormatting.TextRun> objektů může být podtříd. To umožňuje, aby zdroj textu poskytoval textovou formátovací zprávu s textovými běhy, které obsahují vlastní data.  
  
 Následující příklad ukazuje metodu <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>. Toto úložiště textu vrátí <xref:System.Windows.Media.TextFormatting.TextRun> objekty do formátovacího modulu textu pro zpracování.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> V tomto příkladu ukládá textové úložiště do celého textu stejné vlastnosti textu. Rozšířené úložiště textu by muselo implementovat vlastní správu rozsahu, aby jednotlivé znaky mohly mít různé vlastnosti.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Určení vlastností formátování  
 objekty <xref:System.Windows.Media.TextFormatting.TextRun> jsou formátovány pomocí vlastností poskytovaných v úložišti textu. Tyto vlastnosti jsou dva typy <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> a <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> zpracovat všechny vlastnosti odstavce včetně <xref:System.Windows.TextAlignment> a <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties> jsou vlastnosti, které se mohou lišit pro každý text spouštěný v rámci odstavce, jako je například štětec popředí, <xref:System.Windows.Media.Typeface>a velikost písma. Chcete-li implementovat vlastní odstavcový a vlastní typy vlastností spuštění textu, musí vaše aplikace vytvořit třídy, které jsou odvozeny od <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> a <xref:System.Windows.Media.TextFormatting.TextRunProperties> v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
