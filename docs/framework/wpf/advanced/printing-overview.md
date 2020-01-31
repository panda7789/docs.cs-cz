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
ms.openlocfilehash: de9f4b5c0a817d010c7510395b4e5c09ed0a9865
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794283"
---
# <a name="printing-overview"></a>Přehled tisku
S Microsoft .NET Framework mají vývojáři aplikací pomocí Windows Presentation Foundation (WPF) bohatou novou sadu rozhraní API pro správu tisku a tiskového systému. V systému Windows Vista jsou některá z těchto vylepšení systému pro tisk také k dispozici vývojářům vytvářejícím model Windows Forms aplikací a vývojářů pomocí nespravovaného kódu. Základem této nové funkce je nový formát souboru XPS (XML Paper Specification) a cesta k tisku XPS.  
  
 Toto téma obsahuje následující části.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>O formátu XPS  
 XPS je elektronický formát dokumentu, formát souboru zařazování a jazyk popisu stránky. Jedná se o otevřený formát dokumentu, který používá XML, konvence pro otevření balíčku (OPC) a další oborové standardy k vytváření dokumentů pro různé platformy. XPS zjednodušuje proces, při kterém se vytvářejí, sdílí, tisknou, zobrazují a archivují digitální dokumenty. Další informace o XPS najdete v [dokumentu XPS](/windows/desktop/printdocs/documents).  
  
 Několik postupů pro tisk obsahu založeného na XPS pomocí WPF je znázorněno v [programovém tisku souborů XPS](how-to-programmatically-print-xps-files.md). Může být užitečné, aby na tyto ukázky odkazovala během revize obsahu obsaženého v tomto tématu. (Vývojáři nespravovaného kódu by měli vidět dokumentaci k [funkci MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Model Windows Forms vývojáři musí používat rozhraní API v oboru názvů <xref:System.Drawing.Printing>, který nepodporuje úplnou cestu k tisku v rámci XPS, ale podporuje hybridní cestu k tisku typu GDI. Viz **Architektura tisk cesty** níže.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Cesta tisku XPS  
 Cesta tisku XPS (XML Paper Specification) je nová funkce systému Windows, která mění definici způsobu zpracování tisku v aplikacích systému Windows. Vzhledem k tomu, že XPS může nahradit jazyk prezentace dokumentu (jako je RTF), formát zařazování tisku (například WMF) a jazyk popisu stránky (například PCL nebo PostScript); Nová cesta tisku uchovává formát XPS z publikace aplikace do konečného zpracování v ovladači tiskárny nebo zařízení.  
  
 Cesta k tisku ve formátu XPS je postavená na modelu XPSDrv (XPS Printer Driver Model), který poskytuje několik výhod pro vývojáře, jako je například "co vidíte" (WYSIWYG), vylepšená podpora barev a výrazně Vylepšený výkon tisku. (Další informace o XPSDrv najdete v [dokumentaci k sadě Windows Driver Kit](/windows-hardware/drivers/).)  
  
 Operace zařazování tisku pro dokumenty XPS je v podstatě stejná jako v předchozích verzích Windows. Kromě existující cesty pro tisk v rozhraní GDI se ale vylepšila podpora cesty k tisku XPS. Nová cesta pro tisk nativně spotřebovává soubor zařazování XPS. I když budou ovladače tiskáren v uživatelském režimu napsané pro předchozí verze Windows i nadále fungovat, vyžaduje se ovladač tiskárny XPS (XPSDrv), aby bylo možné použít tiskovou cestu XPS.  
  
 Výhody tiskové cesty XPS jsou významné a zahrnují:  
  
- Podpora tisku v režimu WYSIWYG  
  
- Nativní podpora pokročilých barevných profilů, mezi které patří 32 bitů na kanál (bitů), CMYK, pojmenované barvy, n-tiskové a nativní podpora transparentnosti a přechodů.  
  
- Vylepšený výkon tisku pro .NET Framework i aplikace založené na Win32.  
  
- Standardní formát XPS v oboru.  
  
 Pro základní scénáře tisku je k dispozici jednoduché a intuitivní rozhraní API s jedním vstupním bodem pro uživatelské rozhraní, konfiguraci a odeslání úlohy. V případě pokročilých scénářů je přidána další podpora pro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] přizpůsobení (nebo žádné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vůbec), synchronní nebo asynchronní tisk a možnosti dávkového tisku. Obě možnosti poskytují podporu tisku v režimu úplného nebo částečného vztahu důvěryhodnosti.  
  
 XPS je navržený s ohledem na rozšiřitelnost. Pomocí architektury rozšiřitelnosti můžete funkce a možnosti Přidat do XPS modulárním způsobem. Mezi funkce rozšíření patří:  
  
- Tisk schématu. Veřejné schéma se pravidelně aktualizuje a umožňuje rychlé rozšíření možností zařízení. (Viz **PrintTicket a PrintCapabilities** níže.)  
  
- Kanál rozšiřitelného filtru. Kanál filtru XPS tiskárny (XPSDrv) byl navržen tak, aby umožňoval přímý i škálovatelný tisk dokumentů XPS. Další informace najdete v tématu [ovladače tiskáren XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Architektura cesty tisku  
 I když aplikace Win32 i .NET Framework podporují XPS, Win32 a aplikace model Windows Forms k vytvoření obsahu XPS pro ovladač tiskáren XPS (XPSDrv) používá rozhraní GDI pro převod na formát XPS. Tyto aplikace nejsou nutné k použití tiskové cesty XPS a můžou dál používat tisk založený na rozšířených metasouborech (EMF). Většina funkcí a vylepšení XPS je ale dostupná jenom pro aplikace, které cílí na tiskovou cestu XPS.  
  
 Aby bylo možné povolit používání XPSDrv tiskáren v aplikacích Win32 a model Windows Forms, podporuje ovladač tiskárny XPS (XPSDrv) převod GDI do formátu XPS. Model XPSDrv také poskytuje převaděč pro formát XPS do formátu GDI, takže aplikace Win32 mohou tisknout dokumenty XPS. Pro aplikace WPF je převod formátu XPS na formát GDI proveden automaticky pomocí <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody třídy <xref:System.Windows.Xps.XpsDocumentWriter> vždy, když cílová tisková fronta operace zápisu nemá ovladač XPSDrv. (Model Windows Forms aplikace nemůžou tisknout dokumenty XPS.)  
  
 Následující obrázek znázorňuje podsystém tisku a definuje části poskytované společností Microsoft a části definované výrobci softwaru a hardwaru:  
  
 ![Snímek obrazovky ukazuje tiskový systém XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Základní tisk XPS  
 WPF definuje základní i pokročilé rozhraní API. Pro aplikace, které nevyžadují rozsáhlé přizpůsobení tisku nebo přístup k kompletní sadě funkcí XPS, je k dispozici podpora základní tiskárny. Základní podpora tisku se zveřejňuje prostřednictvím ovládacího prvku tiskového dialogu, který vyžaduje minimální konfiguraci a nabízí známý [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. K dispozici je mnoho funkcí XPS pomocí tohoto zjednodušeného tiskového modelu.  
  
#### <a name="printdialog"></a>PrintDialog  
 Ovládací prvek <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguraci a odeslání úlohy ve formátu XPS. Informace o vytvoření instance a použití ovládacího prvku naleznete v tématu [vyvolání dialogového okna pro tisk](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Pokročilý tisk do XPS  
 Pro přístup k kompletní sadě funkcí XPS se musí použít pokročilé rozhraní API pro tisk. Několik relevantních rozhraní API je podrobněji popsáno níže. Úplný seznam rozhraní API pro tisk ve formátu XPS najdete v odkazech na obor názvů <xref:System.Windows.Xps> a <xref:System.Printing>.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket a PrintCapabilities  
 Třídy <xref:System.Printing.PrintTicket> a <xref:System.Printing.PrintCapabilities> jsou základem pokročilých funkcí XPS. Oba typy objektů jsou XML formátované struktury funkcí orientovaných na tisk, jako jsou kolace, oboustranný tisk, sešívání atd. Tyto struktury jsou definovány schématem tisku. <xref:System.Printing.PrintTicket> instruuje tiskárnu, jak zpracovat tiskovou úlohu. Třída <xref:System.Printing.PrintCapabilities> definuje možnosti tiskárny. Díky dotazování na možnosti tiskárny je možné vytvořit <xref:System.Printing.PrintTicket>, která plně využívá podporované funkce tiskárny. Podobně je možné vyhnout se nepodporovaným funkcím.  
  
 Následující příklad ukazuje, jak zadat dotaz na <xref:System.Printing.PrintCapabilities> tiskárny a vytvořit <xref:System.Printing.PrintTicket> pomocí kódu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>Tiskový_server a tisková fronta  
 Třída <xref:System.Printing.PrintServer> představuje tiskový server sítě a třída <xref:System.Printing.PrintQueue> představuje tiskárnu a výstupní frontu úloh, která je k ní přidružená. Tato rozhraní API dohromady umožňují pokročilou správu tiskových úloh serveru. Pro správu <xref:System.Printing.PrintQueue>se používá <xref:System.Printing.PrintServer>nebo jedna z jeho odvozených tříd. Metoda <xref:System.Printing.PrintQueue.AddJob%2A> slouží k vložení nové tiskové úlohy do fronty.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Printing.LocalPrintServer> a přistupovat ke svému výchozímu <xref:System.Printing.PrintQueue> pomocí kódu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter>s mnoha metodami <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> se používá k zápisu dokumentů XPS do <xref:System.Printing.PrintQueue>. Například metoda <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> se používá pro výstup dokumentu XPS a <xref:System.Printing.PrintTicket> synchronně. Metoda <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> se používá pro výstup dokumentu XPS a <xref:System.Printing.PrintTicket> asynchronně.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Xps.XpsDocumentWriter> pomocí kódu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Metody <xref:System.Printing.PrintQueue.AddJob%2A> také poskytují způsoby tisku. Viz [programové tisk souborů XPS](how-to-programmatically-print-xps-files.md). , kde najdete podrobnosti.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Cesta pro tisk GDI  
 I když aplikace WPF nativně podporují tiskovou cestu XPS, Win32 a model Windows Forms aplikace mohou také využívat některé funkce XPS. Ovladač tiskárny XPS (XPSDrv) může převést výstup založený na GDI na formát XPS. V případě pokročilých scénářů se vlastní konverze obsahu podporuje pomocí [převaděče dokumentů Microsoft XPS (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Podobně aplikace WPF mohou také výstup do cesty tisku GDI voláním jedné z <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> nebo <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod třídy <xref:System.Windows.Xps.XpsDocumentWriter> a určením XpsDrv tiskárny jako cílové tiskové fronty.  

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
  
- **Podpora pokročilých grafických prvků** Nativní podpora pro základní prvky transparentnosti a přechodu zabraňuje rastrování obsahu v dokumentu XPS.  
  
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
- [Postupy](printing-how-to-topics.md)
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Dokumenty XPS](/windows/desktop/printdocs/documents)
- [Serializace a úložiště dokumentů](document-serialization-and-storage.md)
- [Převaděč dokumentů Microsoft XPS (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
