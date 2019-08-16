---
title: Přehled tisku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: be82b64581ee178b463950d4b8cdae1f98949161
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545300"
---
# <a name="printing-overview"></a>Přehled tisku
S Microsoft .NET Framework mají vývojáři aplikací pomocí Windows Presentation Foundation (WPF) bohatou novou sadu rozhraní API pro správu tisku a tiskového systému. U [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)]nástroje jsou některé z těchto vylepšení systému pro tisk k dispozici také [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vývojářům, kteří vytvářejí aplikace a vývojáře pomocí nespravovaného kódu. Základem této nové funkce je nový [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] formát souboru a cesta pro [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] tisk.  
  
 Toto téma obsahuje následující části.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>O formátu XPS  
 XPS je elektronický formát dokumentu, formát souboru zařazování a jazyk popisu stránky. Jedná se o otevřený formát dokumentu, který [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]používá konvence Open balení (OPC) a další oborové standardy k vytváření dokumentů pro různé platformy. XPS zjednodušuje proces, při kterém se vytvářejí, sdílí, tisknou, zobrazují a archivují digitální dokumenty. Další informace o XPS najdete v [dokumentu XPS](/windows/desktop/printdocs/documents).  
  
 Několik technik tisku obsahu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] založeného na XPS je znázorněné v [programovém tisku souborů XPS](how-to-programmatically-print-xps-files.md). Může být užitečné, aby na tyto ukázky odkazovala během revize obsahu obsaženého v tomto tématu. (Vývojáři nespravovaného kódu by si měli prohlédnout dokumentaci k [funkci MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Model Windows Forms vývojáři musí používat rozhraní API v <xref:System.Drawing.Printing> oboru názvů, který nepodporuje úplnou [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] cestu tisku, ale podporuje hybridní cestu k tisku pomocí formátu GDI. Viz **Architektura tisk cesty** níže.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Cesta tisku XPS  
 Cesta tisku XPS (XML Paper Specification) je nová [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] funkce, která předefinuje způsob zpracování tisku v aplikacích systému Windows. Vzhledem [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] k tomu, že může nahradit jazyk prezentace dokumentu (například RTF), formát zařazování tisku (například WMF) a jazyk popisu stránky (například PCL nebo PostScript); nová cesta tisku udržuje formát XPS z publikace aplikace do Konečné zpracování v ovladači tiskárny nebo zařízení.  
  
 Tisková cesta XPS je postavená na modelu XPSDrv (XPS Printer Driver Model), který poskytuje několik výhod pro vývojáře [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] , jako je tisk, vylepšená podpora barev a výrazně vyšší výkon tisku. (Další informace o XPSDrv najdete v [dokumentaci k sadě Windows Driver Kit](/windows-hardware/drivers/).)  
  
 Operace zařazování tisku pro dokumenty XPS je v podstatě stejná jako v předchozích verzích Windows. Kromě existující cesty pro tisk v rozhraní GDI se ale vylepšila podpora cesty k tisku XPS. Nová cesta pro tisk nativně spotřebovává soubor zařazování XPS. Přestože ovladače tiskárny v uživatelském režimu napsané pro předchozí verze [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] nástroje budou fungovat i nadále, je potřeba ovladač tiskárny XPS (XPSDrv), aby bylo možné použít cestu k tisku ve formátu XPS.  
  
 Výhody tiskové cesty XPS jsou významné a zahrnují:  
  
- [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)]Podpora tisku  
  
- Nativní podpora pokročilých barevných profilů, mezi které patří 32 bitů na kanál (bitů), CMYK, pojmenované barvy, n-tiskové a nativní podpora transparentnosti a přechodů.  
  
- Vylepšený výkon tisku pro .NET Framework [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] i aplikace založené na systému.  
  
- Standardní formát XPS v oboru.  
  
 Pro základní scénáře tisku je k dispozici jednoduché a intuitivní rozhraní API s jedním vstupním bodem pro uživatelské rozhraní, konfiguraci a odeslání úlohy. V případě pokročilých scénářů je další podpora přidána [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] k přizpůsobení (nebo [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vůbec ne všem), synchronnímu nebo asynchronnímu tisku a možnostem dávkového tisku. Obě možnosti poskytují podporu tisku v režimu úplného nebo částečného vztahu důvěryhodnosti.  
  
 XPS je navržený s ohledem na rozšiřitelnost. Pomocí architektury rozšiřitelnosti můžete funkce a možnosti Přidat do XPS modulárním způsobem. Mezi funkce rozšíření patří:  
  
- Tisk schématu. Veřejné schéma se pravidelně aktualizuje a umožňuje rychlé rozšíření možností zařízení. (Viz **PrintTicket a PrintCapabilities** níže.)  
  
- Kanál rozšiřitelného filtru. Kanál filtru XPS tiskárny (XPSDrv) byl navržen tak, aby umožňoval přímý i škálovatelný tisk dokumentů XPS. Další informace najdete v tématu [ovladače tiskáren XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Architektura cesty tisku  
 I [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] když aplikace .NET Framework podporují [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] XPS a model Windows Forms aplikace používají k převodu formátu XPS pro ovladač tiskárny XPS Formát GDI (XPSDrv). Tyto aplikace nejsou nutné k použití tiskové cesty XPS a můžou dál používat tisk založený na rozšířených metasouborech (EMF). Většina funkcí a vylepšení XPS je ale dostupná jenom pro aplikace, které cílí na tiskovou cestu XPS.  
  
 Aby bylo možné povolit používání tiskáren [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] založených na XPSDrv a aplikací model Windows Forms, ovladač tiskárny XPS (XPSDrv) podporuje převod GDI na formát XPS. Model XPSDrv také poskytuje převaděč pro formát XPS do formátu GDI, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] takže aplikace můžou dokumenty tisknout. [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] Pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace se převod formátu XPS na formát GDI provádí automaticky <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> pomocí metod <xref:System.Windows.Xps.XpsDocumentWriter> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> třídy vždy, když cílová tisková fronta operace zápisu nemá ovladač XPSDrv. (Model Windows Forms aplikace nemohou tisknout [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty.)  
  
 Následující obrázek znázorňuje podsystém tisku a definuje části, které [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]poskytuje, a části definované výrobci softwaru a hardwaru:  
  
 ![Snímek obrazovky ukazuje tiskový systém XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Základní tisk XPS  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]definuje základní i pokročilé rozhraní API. Pro aplikace, které nevyžadují rozsáhlé přizpůsobení tisku nebo přístup k kompletní sadě funkcí XPS, je k dispozici podpora základní tiskárny. Základní podpora tisku je dostupná prostřednictvím ovládacího prvku tiskového dialogu, který vyžaduje minimální konfiguraci a funkce [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], které jsou známé. K dispozici je mnoho funkcí XPS pomocí tohoto zjednodušeného tiskového modelu.  
  
#### <a name="printdialog"></a>PrintDialog  
 Ovládací prvek poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]odesílání, konfiguraci a odeslání úlohy ve formátu XPS. <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Informace o vytvoření instance a použití ovládacího prvku naleznete v tématu [vyvolání dialogového okna pro tisk](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Pokročilý tisk do XPS  
 Pro přístup k kompletní sadě funkcí XPS se musí použít pokročilé rozhraní API pro tisk. Několik relevantních rozhraní API je podrobněji popsáno níže. Úplný seznam rozhraní API pro tisk ve formátu XPS najdete v odkazech <xref:System.Printing> na <xref:System.Windows.Xps> obor názvů a.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket a PrintCapabilities  
 Třídy <xref:System.Printing.PrintTicket> a<xref:System.Printing.PrintCapabilities> jsou základem pokročilých funkcí XPS. Oba typy objektů jsou formátované [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] struktury funkcí orientovaných na tisk, jako jsou kolace, oboustranný tisk, sešívání atd. Tyto struktury jsou definovány schématem tisku. A <xref:System.Printing.PrintTicket> dává pokyn k tomu, jak zpracovat tiskovou úlohu. <xref:System.Printing.PrintCapabilities> Třída definuje možnosti tiskárny. Díky dotazování na možnosti tiskárny <xref:System.Printing.PrintTicket> je možné vytvořit, který plně využívá podporované funkce tiskárny. Podobně je možné vyhnout se nepodporovaným funkcím.  
  
 Následující příklad ukazuje, jak zadat dotaz na <xref:System.Printing.PrintCapabilities> tiskárnu a <xref:System.Printing.PrintTicket> vytvořit pomocí kódu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>Tiskový_server a tisková fronta  
 Třída představuje tiskový server sítě <xref:System.Printing.PrintQueue> a třída představuje tiskárnu a výstupní frontu úloh, která je k ní přidružená. <xref:System.Printing.PrintServer> Tato rozhraní API dohromady umožňují pokročilou správu tiskových úloh serveru. A <xref:System.Printing.PrintServer>, nebo jedna z jeho odvozených tříd, se používá ke <xref:System.Printing.PrintQueue>správě. <xref:System.Printing.PrintQueue.AddJob%2A> Metoda slouží k vložení nové tiskové úlohy do fronty.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Printing.LocalPrintServer> a přistupovat ke svému výchozímu <xref:System.Printing.PrintQueue> pomocí kódu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Spolu s <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> mnoha metodami <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a se používá k zápisu dokumentů XPS do <xref:System.Printing.PrintQueue>. <xref:System.Windows.Xps.XpsDocumentWriter> Například <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> metoda se používá pro výstup dokumentu XPS a <xref:System.Printing.PrintTicket> synchronně. Metoda se používá pro výstup dokumentu XPS a <xref:System.Printing.PrintTicket> asynchronně. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29>  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Xps.XpsDocumentWriter> kód pomocí kódu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Metody také poskytují způsoby tisku. Viz [programové tisk souborů XPS](how-to-programmatically-print-xps-files.md). , kde najdete podrobnosti.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Cesta pro tisk GDI  
 I [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] když aplikace nativně podporují tiskovou [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] cestu XPS a aplikace model Windows Forms mohou také využívat některé funkce XPS. Ovladač tiskárny XPS (XPSDrv) může převést výstup založený na GDI na formát XPS. V případě pokročilých scénářů se vlastní konverze obsahu podporuje pomocí [převaděče dokumentů Microsoft XPS (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Podobně aplikace mohou také výstup do cesty pro tisk GDI voláním jedné <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> z metod <xref:System.Windows.Xps.XpsDocumentWriter> třídy nebo <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> a určením, že XpsDrv tiskárna jako cílovou tiskovou frontu. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]  

U aplikací, které nevyžadují funkce a podporu XPS, zůstane aktuální cesta tisku GDI beze změny.  
  
- Další referenční materiály k tiskové cestě GDI a různým možnostem převodu XPS najdete v tématu [MXDC (Microsoft XPS Document Converter)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) a [XPSDrv ovladače tiskárny](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Model ovladače XPSDrv  
 Tisková cesta XPS zlepšuje efektivitu zařazování pomocí XPS jako nativního formátu zařazování tisku při tisku na tiskárnu nebo ovladač s podporou standardu XPS. Zjednodušený proces zařazování eliminuje nutnost vygenerovat soubor mezilehlého zařazování, jako je například datový soubor EMF, před zařazením dokumentu do fronty. V menších velikostech souborů zařazování může tisknout tiskovou cestu XPS snížit zatížení sítě a zvýšit výkon tisku.  
  
 EMF je zavřený formát, který představuje výstup aplikace jako řadu volání rozhraní GDI pro vykreslování služeb. Na rozdíl od formátu EMF představuje formát fronty XPS skutečný dokument bez nutnosti dalšího výkladu při výstupu do ovladače tiskárny založeného na formátu XPS (XPSDrv). Ovladače mohou pracovat přímo s daty ve formátu. Tato funkce eliminuje, že při použití souborů EMF a ovladačů tiskárny založených na rozhraní GDI se vyžadují převody datových prostorů a barev.  
  
 Velikosti souborů zařazování se obvykle zmenší při použití dokumentů XPS, které cílí na ovladač tiskárny XPS (XPSDrv), v porovnání s jejich ekvivalenty EMF; Existují však výjimky:  
  
- Vektorová grafika, která je velmi složitá nebo neefektivně vytvořená, může být větší než bitmapová verze stejného obrázku.  
  
- Pro účely zobrazení obrazovky soubory XPS vkládají písma zařízení a také písma založená na počítačích. vzhledem k tomu, že soubory pro zařazování GDI nevkládají písma zařízení. Ale oba druhy písem jsou subsetted (viz níže) a ovladače tiskárny mohou odebrat písma zařízení před tím, než se soubor přenáší do tiskárny.  
  
 Zmenšení velikosti fronty se provádí prostřednictvím několika mechanismů:  
  
- **PodNastavení písma** V souboru XPS jsou uloženy pouze znaky používané v rámci samotného dokumentu.  
  
- **Podpora pokročilých grafických prvků** Nativní podpora pro základní prvky transparentnosti a přechodu zabraňuje rastrování obsahu v [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentu.  
  
- **Identifikace běžných prostředků** Prostředky, které se používají několikrát (například obrázek reprezentující logo společnosti), se považují za sdílené prostředky a načtou se jenom jednou.  
  
- **Komprese ZIP**. Všechny dokumenty XPS používají kompresi ZIP.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Témata s postupy](printing-how-to-topics.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Dokumenty XPS](/windows/desktop/printdocs/documents)
- [Serializace a úložiště dokumentů](document-serialization-and-storage.md)
- [Převaděč dokumentů Microsoft XPS (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
