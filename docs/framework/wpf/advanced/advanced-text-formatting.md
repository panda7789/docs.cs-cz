---
title: "Upřesněné formátování textu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bb2664b267301fdf1e3a67e385595a5d28212bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-text-formatting"></a>Upřesněné formátování textu
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] Poskytuje výkonnou sadu [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] pro včetně textu ve vaší aplikaci. Rozložení a [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], jako například <xref:System.Windows.Controls.TextBlock>zadejte nejobvyklejší a obecné použít elementy pro prezentaci text. Kreslení [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], jako například <xref:System.Windows.Media.GlyphRunDrawing> a <xref:System.Windows.Media.FormattedText>, umožňují pro včetně formátovaný text v kresby. Nejvýše pokročilé úrovni [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje formátování modul řídit všechny aspekty text prezentací, jako je Správa textových úložiště, správy formátování textu spustit a správa vložený objekt rozšiřitelné textu.  
  
 Toto téma obsahuje úvod do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formátování textu. Zaměřuje se na implementace klienta a použití [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] modul formátování textu.  
  
> [!NOTE]
>  Všechny příklady kódu v tomto dokumentu najdete v [Advanced ukázka formátování textu](http://go.microsoft.com/fwlink/?LinkID=159965).  
  

  
<a name="prereq"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že jste obeznámeni s vyšší úrovní [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] používá pro prezentaci text. Většina scénářů uživatelů nebudou vyžaduje formátování pokročilé textu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] popsané v tomto tématu. Úvod do různých text [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], najdete v části [dokumenty v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md).  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>Upřesněné formátování textu  
 Rozložení textu a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ovládacích prvků do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zadejte formátování vlastnosti, které vám umožní snadno formátovaný text do aplikace zahrnout. Tyto ovládací prvky vystavit počet vlastností pro zpracování prezentaci textu, což zahrnuje jeho řez písma, velikosti a barvy. Za běžných okolností může zpracovávat tyto ovládací prvky Většina textu prezentace v aplikaci. Ale některé pokročilé scénáře vyžadovat kontrolu nad úložiště text a také text prezentace. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]poskytuje text na extensible formátování modul pro tento účel.  
  
 Najít pokročilých funkcí formátování textu v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsahují text formátování modul, text úložiště, spustí textu a formátování vlastnosti. Text formátování modul, <xref:System.Windows.Media.TextFormatting.TextFormatter>, vytvoří řádků textu, který se má použít pro prezentaci. Toho se dosáhne Zahajování procesu formátování řádku a volání formátování textu <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>. Formátování textu načte spustí text z textového store voláním úložiště <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metoda. <xref:System.Windows.Media.TextFormatting.TextRun> Objekty jsou pak vytvořen do <xref:System.Windows.Media.TextFormatting.TextLine> objekty podle formátování textu a přidělený k aplikaci pro kontroly nebo zobrazení.  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>Pomocí formátování textu  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>je [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] formátování textu, modul a poskytuje služby pro formátování a nejnovější řádky textu. Formátování textu může zpracovávat jiné textových formátů znak a styly odstavce a zahrnuje podporu pro rozložení mezinárodní textu.  
  
 Na rozdíl od tradičních text [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)], <xref:System.Windows.Media.TextFormatting.TextFormatter> komunikuje s klientem rozložení textu pomocí sady metody zpětného volání. Vyžaduje klienta k poskytování těchto metod v implementaci <xref:System.Windows.Media.TextFormatting.TextSource> třídy. Následující diagram znázorňuje interakci rozložení textu mezi klientská aplikace a <xref:System.Windows.Media.TextFormatting.TextFormatter>.  
  
 ![Diagram klienta rozložení textu a objektu TextFormatter](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
Interakce mezi aplikací a objektu TextFormatter  
  
 Formátování textu slouží k načtení řádků formátovaný text z textového úložiště, který je implementací <xref:System.Windows.Media.TextFormatting.TextSource>. K tomu je potřeba první vytvoření instance formátování textu s použitím <xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A> metoda. Tato metoda vytvoří instanci formátování textu a nastaví maximální řádku hodnoty výškou a šířkou. Jakmile je vytvořena instance formátování textu, se spustí proces tvorby v řádku volání <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metoda. <xref:System.Windows.Media.TextFormatting.TextFormatter>zavolá zpátky ke zdroji textu k načtení textu a formátování parametry pro spuštění textu Tato forma řádku.  
  
 V následujícím příkladu se zobrazí proces formátování textu úložiště. <xref:System.Windows.Media.TextFormatting.TextFormatter> Objekt se používá k načtení řádků textu z obchodu text a pak naformátovat řádku textu pro kreslení do <xref:System.Windows.Media.DrawingContext>.  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>Implementace úložiště Text klienta  
 Když rozšíříte modul formátování textu, musíte implementovat a spravovat všechny aspekty text úložiště. Toto není jednoduchý úkol. Text úložiště je zodpovědná za sledování spustit vlastnosti, vlastnosti odstavce, vložené objekty a další podobné obsah textu. Poskytuje také formátování textu u jednotlivých <xref:System.Windows.Media.TextFormatting.TextRun> objekty, které text formátovací modul používá k vytvoření <xref:System.Windows.Media.TextFormatting.TextLine> objekty.  
  
 Pro zpracování virtualizace úložiště text, úložišti textu musí být odvozen od <xref:System.Windows.Media.TextFormatting.TextSource>. <xref:System.Windows.Media.TextFormatting.TextSource>definuje metodu, kterou formátování textu používá k načtení textu spustí z obchodu text. <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>je způsob, jímž formátování textu k načtení textu, spustí použité při formátování řádku. Volání <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> je opakovaně provedené při formátování textu, dokud nenastane některá z následujících podmínek:  
  
-   A <xref:System.Windows.Media.TextFormatting.TextEndOfLine> nebo je vrácena podtřídy.  
  
-   Akumulovaná šířku textu spustí překračuje maximální řádku šířce zadané ve volání vytvoření formátování textu nebo formátování textu volání <xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A> metoda.  
  
-   A [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] pořadí nového řádku, jako je například "CR", "LF" nebo "Line FEED", je vrácena.  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>Poskytnutí textu běží  
 Základní proces formátování textu je interakce mezi formátování textu a úložišti text. Vaši implementaci <xref:System.Windows.Media.TextFormatting.TextSource> poskytuje formátování textu s <xref:System.Windows.Media.TextFormatting.TextRun> objektů a vlastností, pomocí kterých k formátování textu běží. Tato interakce se zpracovává souborem <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metodu, která je volána metodou formátování textu.  
  
 V následující tabulce jsou uvedeny některé z předdefinovaných <xref:System.Windows.Media.TextFormatting.TextRun> objekty.  
  
|Typ TextRun|Použití|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|Specializované text spustit používá ke znázornění znak glyfů předat zpět formátování textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|Specializované text spusťte používaných k poskytování obsahu, ve které měření, testování průchodu a kreslení se provádí v celé, jako je tlačítko nebo bitové kopie v rámci textu.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|Specializované text spustit použité konec řádku.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|Specializované text spustit použité konec odstavce.|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|Specializované text spustit používá se k označení konec segmentu, například na konec oboru vliv na předchozí <xref:System.Windows.Media.TextFormatting.TextModifier> spustit.|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|Specializované text spustit používané k označení rozsah skrytá znaků.|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|Specializované text spustit použít k úpravě vlastností textu běží ve svém oboru. Obor rozšiřuje na další odpovídající <xref:System.Windows.Media.TextFormatting.TextEndOfSegment> text spustit nebo další <xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>.|  
  
 Některý z předdefinovaných <xref:System.Windows.Media.TextFormatting.TextRun> může být rozčlenění objekty. To umožňuje vaší text zdrojem pro poskytování spouští formátování textu s textem, které zahrnují vlastní data.  
  
 Následující příklad ukazuje <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A> metoda. Toto úložiště text vrátí <xref:System.Windows.Media.TextFormatting.TextRun> objekty, které se formátování textu pro zpracování.  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  V tomto příkladu úložišti text poskytuje stejné vlastnosti textu k veškerý text. Pokročilé text, který ukládá by bylo potřeba implementovat vlastní rozsah správy povolíte jednotlivé znaky má jiné vlastnosti.  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>Zadání vlastnosti formátování  
 <xref:System.Windows.Media.TextFormatting.TextRun>objekty jsou formátovaná pomocí vlastností poskytované úložišti text. Tyto vlastnosti mají dva typy <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> a <xref:System.Windows.Media.TextFormatting.TextRunProperties>. <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>například zpracovat odstavce včetně vlastnosti <xref:System.Windows.TextAlignment> a <xref:System.Windows.FlowDirection>. <xref:System.Windows.Media.TextFormatting.TextRunProperties>jsou vlastnosti, které mohou být různé pro každý text spustit v rámci odstavce, jako je například popředí štětce <xref:System.Windows.Media.Typeface>a velikost písma. Chcete-li implementovat vlastní odstavec a vlastní text spustit typy vlastností, musíte vytvořit aplikace třídy, které jsou odvozeny od <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> a <xref:System.Windows.Media.TextFormatting.TextRunProperties> v uvedeném pořadí.  
  
## <a name="see-also"></a>Viz také  
 [Typografie v rozhraní WPF](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
