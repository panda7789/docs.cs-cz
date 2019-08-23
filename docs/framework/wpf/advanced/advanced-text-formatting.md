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
ms.openlocfilehash: 469c62691ff38a8c5a01bec3ddfd7b324bab7eca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969071"
---
# <a name="advanced-text-formatting"></a>Upřesněné formátování textu
Windows Presentation Foundation (WPF) poskytuje robustní sadu rozhraní API pro zahrnutí textu do aplikace. Rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]rozhraní API, <xref:System.Windows.Controls.TextBlock>například, poskytují nejběžnější a obecné prvky použití pro textovou prezentaci. Kreslicí rozhraní API, například <xref:System.Windows.Media.GlyphRunDrawing> a <xref:System.Windows.Media.FormattedText>, poskytují způsob, jak zahrnout formátovaný text do kreseb. Na nejvyšší úrovni [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje nástroj rozšiřitelné formátování textu pro řízení všech aspektů textové prezentace, jako je Správa úložiště textu, Správa formátování textových běhů a Správa vložených objektů.  
  
 Toto téma poskytuje Úvod do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formátování textu. Zaměřuje se na implementaci klienta a používání [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroje formátování textu.  
  
> [!NOTE]
> Všechny příklady kódu v tomto dokumentu najdete v [ukázce Rozšířené formátování textu](https://go.microsoft.com/fwlink/?LinkID=159965).  

<a name="prereq"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že máte zkušenosti s rozhraními API vyšší úrovně použitými pro textovou prezentaci. Většina uživatelských scénářů nebude vyžadovat rozhraní API pro rozšířené formátování textu popsané v tomto tématu. Úvod do různých textových rozhraní API naleznete [v tématu dokumenty v WPF](documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Rozložení textu a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládací prvky v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroji poskytují vlastnosti formátování umožňující snadné zahrnutí formátovaného textu do aplikace. Tyto ovládací prvky zpřístupňují několik vlastností, které umožňují zpracování prezentace textu, včetně řezu písma, velikosti a barvy. V běžných případech tyto ovládací prvky mohou ve vaší aplikaci zpracovat většinu textových prezentací. Některé pokročilé scénáře však vyžadují řízení ukládání textu a prezentaci textu. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]poskytuje nástroj rozšiřitelného formátování textu pro tento účel.  
  
 Funkce Rozšířené formátování textu, které se [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nacházejí v nástroji, se skládají z nástroje formátování textu, textového úložiště, textu se spouští a formátování vlastností. Modul <xref:System.Windows.Media.TextFormatting.TextFormatter>formátování textu vytvoří řádky textu, které se mají použít pro prezentaci. Toho je dosaženo inicializací procesu formátování řádku a voláním formátovacího <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>modulu textu. Formátování textu načte text spouštěný z vašeho textového úložiště voláním <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metody Storu. Objekty se pak <xref:System.Windows.Media.TextFormatting.TextLine> vytvoří pomocí formátovacího modulu textu a přidělí se vaší aplikaci pro kontrolu nebo zobrazení. <xref:System.Windows.Media.TextFormatting.TextRun>  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Použití formátovacího textu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>je modul formátování textu a poskytuje služby pro formátování a zalamování textových řádků. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Formátování textu může zpracovávat různé formáty textových znaků a odstavcové styly a zahrnuje podporu pro mezinárodní rozložení textu.  
  
 Na <xref:System.Windows.Media.TextFormatting.TextFormatter> rozdíl od tradičního textového rozhraní API komunikuje s klientem rozložení textu prostřednictvím sady metod zpětného volání. Vyžaduje, aby klient poskytoval tyto metody v implementaci <xref:System.Windows.Media.TextFormatting.TextSource> třídy. Následující diagram znázorňuje interakci rozložení textu mezi klientskou aplikací a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta rozložení textu a TextFormatter](./media/advanced-text-formatting/text-layout-textformatter-interaction.png)  
  
 Formátování textu se používá k načtení formátovaných textových řádků z úložiště textu, což je implementace <xref:System.Windows.Media.TextFormatting.TextSource>. To se provádí tak, že nejprve vytvoříte instanci formátování textu pomocí <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> metody. Tato metoda vytvoří instanci formátování textu a nastaví maximální hodnoty výšky a šířky čáry. Jakmile je vytvořena instance formátování textu, je proces vytvoření řádku spuštěn voláním <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody. <xref:System.Windows.Media.TextFormatting.TextFormatter>zavolá zpět do zdroje textu a načte text a formátovací parametry pro spuštění textu, který tvoří čáru.  
  
 V následujícím příkladu se zobrazuje proces formátování textového úložiště. Objekt se používá k načtení textových řádků z úložiště textu a následnému formátování řádku textu pro kreslení <xref:System.Windows.Media.DrawingContext>do. <xref:System.Windows.Media.TextFormatting.TextFormatter>  
  
 [!code-csharp[TextFormatterExample#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementace úložiště textu klienta  
 Když rozšíříte modul formátování textu, je nutné implementovat a spravovat všechny aspekty v úložišti textu. Nejedná se o triviální úlohu. Úložiště textu zodpovídá za sledování vlastností běhu textu, vlastností odstavce, vložených objektů a dalšího podobného obsahu. Poskytuje také formátování textu pro jednotlivé <xref:System.Windows.Media.TextFormatting.TextRun> objekty, které formátovací modul textu používá k vytvoření <xref:System.Windows.Media.TextFormatting.TextLine> objektů.  
  
 Aby bylo možné zpracovat virtualizaci textového úložiště, musí být úložiště textu odvozeno z <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource>definuje metodu, kterou formátovací modul textu používá k načtení textových běhů z úložiště textu. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>je metoda používaná formátovacím textem k načtení textových běhů používaných při formátování čáry. Volání <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> je opakovaně provedeno pomocí formátovacího modulu textu, dokud nedojde k jedné z následujících podmínek:  
  
- Vrátí se podtřída nebo. <xref:System.Windows.Media.TextFormatting.TextEndOfLine>  
  
- Kumulovaná šířka textu je větší než maximální tloušťka čáry zadaná v volání pro vytvoření formátovacího textu nebo volání <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metody formátování textu.  
  
- Vrátí se sekvence nového řádku, například "CF", "LF" nebo "CRLF". [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Poskytování textových běhů  
 Základem procesu formátování textu je interakce mezi formátováním textu a úložištěm textu. Vaše implementace <xref:System.Windows.Media.TextFormatting.TextSource> poskytuje formátování textu <xref:System.Windows.Media.TextFormatting.TextRun> s objekty a vlastnostmi, pomocí kterých se má formátovat text. Tato interakce je zpracována <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metodou, která je volána formátovacím modulem textu.  
  
 V následující tabulce jsou uvedeny některé předdefinované <xref:System.Windows.Media.TextFormatting.TextRun> objekty.  
  
|Typ TextRun|Použití|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Specializovaný text, který se používá k předání reprezentace znaků glyfů zpátky do formátovacího modulu textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Specializovaný text, který se používá k poskytnutí obsahu při měření, testování přístupů a vykreslování, se provádí v celém rozsahu, jako je například tlačítko nebo obrázek v rámci textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Slouží ke spuštění specializovaného textu k označení konce řádku.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Slouží ke spuštění specializovaného textu, který označuje konec odstavce.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Slouží ke spuštění specializovaného textu, který označuje konec segmentu, například k ukončení rozsahu ovlivněného předchozím <xref:System.Windows.Media.TextFormatting.TextModifier> spuštěním.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Pomocí specializovaného textu lze označit rozsah skrytých znaků.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Použití specializovaného textu, který slouží k úpravě vlastností textu, se spouští ve svém rozsahu. Rozsah se rozšíří na další shodný <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> běh textu nebo na další. <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|  
  
 Jakýkoli z předdefinovaných <xref:System.Windows.Media.TextFormatting.TextRun> objektů může být podtříd. To umožňuje, aby zdroj textu poskytoval textovou formátovací zprávu s textovými běhy, které obsahují vlastní data.  
  
 Následující příklad ukazuje <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metodu. Toto úložiště textu vrátí <xref:System.Windows.Media.TextFormatting.TextRun> objekty do formátovacího modulu textu pro zpracování.  
  
 [!code-csharp[TextFormatterExample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
> V tomto příkladu ukládá textové úložiště do celého textu stejné vlastnosti textu. Rozšířené úložiště textu by muselo implementovat vlastní správu rozsahu, aby jednotlivé znaky mohly mít různé vlastnosti.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Určení vlastností formátování  
 <xref:System.Windows.Media.TextFormatting.TextRun>objekty jsou formátovány pomocí vlastností poskytovaných v úložišti textu. Tyto vlastnosti jsou dva typy, <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> a. <xref:System.Windows.Media.TextFormatting.TextRunProperties> <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>Zpracujte vlastnosti <xref:System.Windows.TextAlignment> odstavce včetně a <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties>jsou vlastnosti, které se mohou lišit pro každý text spouštěný v rámci odstavce, jako je například <xref:System.Windows.Media.Typeface>štětec popředí, a velikost písma. Chcete-li implementovat vlastní odstavcový a vlastní typy vlastností spuštění textu, musí vaše aplikace vytvořit třídy, <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> které <xref:System.Windows.Media.TextFormatting.TextRunProperties> jsou odvozeny z a v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také:

- [Typografie v rozhraní WPF](typography-in-wpf.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
