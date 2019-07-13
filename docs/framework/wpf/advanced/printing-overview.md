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
ms.openlocfilehash: acfc252708bf8be7abacb1adc2968122501315a0
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860201"
---
# <a name="printing-overview"></a>Přehled tisku
Pomocí rozhraní Microsoft .NET Framework aplikace vývojářům, kteří používají Windows Presentation Foundation (WPF) mají nové bohatou tisku a tisk rozhraní API pro správu systému. S [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], některé z těchto vylepšení tiskovém systému jsou také k dispozici pro vývojáře vytvářející [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace a vývojáře, kteří používají nespravovaný kód. V jádru služby tato nová funkce je nový [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] formát souboru a [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] cesta tisku.  
  
 Toto téma obsahuje následující části.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>O XPS  
 XPS je ve formátu elektronických dokumentů, formát souboru pro zařazování a jazyk pro popis stránky. Je ve formátu otevřít dokument, který používá [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]a další oborové standardy pro vytváření multiplatformních dokumentů. XPS zjednodušuje proces, podle kterého digitální dokumenty jsou vytvořené sdílené, vytisknout, zobrazit a archivovat. Další informace o XPS, naleznete v tématu [dokumenty XPS](/windows/desktop/printdocs/documents).  
  
 Několik postupů pro tisk na základě XPS obsahu pomocí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je ukázán v [programově tisk souborů XPS z](how-to-programmatically-print-xps-files.md). Možná bude užitečné odkazují tyto ukázky během kontroly obsahu obsažené v tomto tématu. (Vývojáři nespravovaného kódu by měla najdete v dokumentaci [MXDC_ESCAPE funkce](/windows/desktop/printdocs/mxdc-escape). Windows Forms musí vývojáři v rozhraní API <xref:System.Drawing.Printing> obor názvů, který nepodporuje kompletní [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] cesta tisku, ale podporuje cesta tisku GDI XPS hybridní. Zobrazit **architektura cesta tisku** níže.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Cesta tisku XPS  
 Cesta tisku XML Paper Specification (XPS) je nová [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] funkce, které předefinuje zpracování tisku v aplikacích Windows. Protože [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] můžete nahradit jazyk prezentace dokumentu (například ve formátu RTF), formát zařazování tisku (například WMF) a jazyk pro popis stránky (jako je například PCL nebo Postscript); nové cesta tisku udržuje formátu XPS z publikace aplikace konečné zpracování v ovladače tiskárny nebo zařízení.  
  
 Cesta tisku XPS je postavené na model ovladače tiskárny XPS (XPSDrv), který poskytuje několik výhod pro vývojáře, jako [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] tisk, vylepšená podpora barvu a výrazně vyšší výkon tisku. (Další informace o XPSDrv, najdete v článku [dokumentace ke službě Windows Driver Kit](/windows-hardware/drivers/).)  
  
 Operace služby zařazování tisku pro dokumenty XPS je v podstatě stejný jako v předchozích verzích Windows. Nicméně je vylepšená pro podporu cesta tisku XPS kromě existující [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] cesta tisku. Nová cesta tisku nativně využívá soubor ve formátu XPS zařazování. Zatímco napsané pro předchozí verze ovladače tiskárny uživatelského režimu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] budou nadále fungovat, je potřeba, abyste mohli používat cesta tisku XPS ovladači tiskárny XPS (XPSDrv).  
  
 Výhody cesta tisku XPS jsou významné a zahrnují:  
  
- [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] Podpora tisku  
  
- Nativní podpora profilů pokročilé barev, mezi které patří 32 bitů na kanál, CMYK, pojmenované barvy, barvy n a nativní podporu transparentnosti a přechody.  
  
- Zvýšení výkonu tisku pro obě rozhraní .NET Framework a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikací založených na.  
  
- Standardní XPS formát.  
  
 Pro základní scénáře, tisku jednoduchý a intuitivní rozhraní API je k dispozici s jedním vstupním bodem pro odeslání uživatelského rozhraní, konfigurace a úlohy. Pro pokročilé scénáře, přidá se další podporu pro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] přizpůsobení (nebo vůbec žádné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vůbec), synchronní nebo asynchronní tisku a tisk funkcí služby batch. V obou variantách nabízí podpora tisku v režimu plné nebo částečné důvěryhodnosti.  
  
 XPS byla navržena s rozšíření v úvahu. S použitím rozhraní rozšiřitelnosti, funkce a možnosti můžete přidat do XPS modulární způsobem. Rozšíření funkce:  
  
- Tisk schématu. Veřejné schématu se pravidelně aktualizuje a umožňuje rychlé rozšíření funkcí zařízení. (Viz **funkce PrintTicket a printcapabilities –** níže.)  
  
- Rozšiřitelné filtr kanálu. Filtr kanálu XPS tiskárny ovladač (XPSDrv) je navržená k povolení přímé a škálovatelné tisk dokumentů XPS. Další informace najdete v tématu [ovladače tiskárny XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Cesta tisku architektury  
 Přestože obě [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a aplikace rozhraní .NET Framework podporují XPS, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a používání aplikací modelu Windows Forms [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] do XPS převod, chcete-li vytvořit XPS formátovaný obsah ovladače tiskárny XPS (XPSDrv). Tyto aplikace nemusí používat cesta tisku XPS a můžete dál používat [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] na základě tisk. Ale většina XPS funkce a vylepšení jsou k dispozici pouze aplikace, které cílová cesta tisku XPS.  
  
 Povolit používání tiskárny založené na XPSDrv podle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a aplikace Windows Forms, ovladač tiskárny XPS (XPSDrv) podporuje počítačový převod [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formátu XPS. XPSDrv model také poskytuje převaděč pro XPS k [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formátu tak, aby [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikací můžete vytisknout [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty. Pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací, převod XPS k [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formát se automaticky pomocí provádí <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> třídy pokaždé, když tiskové fronty cíl operace zápisu není k dispozici ovladač XPSDrv. (Aplikace Windows Forms nelze tisknout [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty.)  
  
 Následující obrázek znázorňuje tisku subsystému a definuje části poskytované [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]a části určené dodavatelé softwaru a hardwaru:  
  
 ![Snímek obrazovky ukazuje, že systému tisk XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Tisk základní XPS  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Definuje i základní a rozšířená [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. U aplikací, které nevyžadují rozsáhlá přizpůsobení tisku nebo přístup k funkci kompletní XPS nastaveno, základní podpora tisku je k dispozici. Základní podpora tisku je k dispozici prostřednictvím dialogového okna Tisk ovládací prvek, který vyžaduje minimální konfiguraci a funkcích známým [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Mnoho funkcí XPS jsou k dispozici pomocí tohoto modelu zjednodušené tisku.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Řízení poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfigurace a odeslání úlohy XPS. Informace o tom, jak vytvořit instanci a pomocí ovládacího prvku, naleznete v tématu [vyvolání dialogového okna Tisk](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Pokročilé XPS tisku  
 Pro přístup k kompletní sadu funkcí XPS, musí využívat pokročilé tisku rozhraní API. Několik relevantní rozhraní API jsou popsány podrobněji níže. Úplný seznam cesta tisku XPS rozhraní API, najdete v článku <xref:System.Windows.Xps> a <xref:System.Printing> odkazy na obor názvů.  
  
#### <a name="printticket-and-printcapabilities"></a>Funkce PrintTicket a printcapabilities –  
 <xref:System.Printing.PrintTicket> a <xref:System.Printing.PrintCapabilities> třídy jsou základem pro pokročilé funkce XPS. Oba typy objektů jsou [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ve formátu struktury tisk objektově orientovaný funkcí, jako je třeba kolace oboustranný tisk, připojování, atd. Tyto struktury jsou definovaná pomocí schématu rozhraní tisku. A <xref:System.Printing.PrintTicket> tiskárnu dává pokyn, jak zpracovávat tiskové úlohy. <xref:System.Printing.PrintCapabilities> Třída definuje možnosti tiskárny. Pomocí dotazu na možnosti tiskárny <xref:System.Printing.PrintTicket> je možné vytvořit, že přijímá naplno využít tiskárny na podporované funkce. Podobně se lze vyvarovat nepodporované funkce.  
  
 Následující příklad ukazuje, jak provádět dotazy <xref:System.Printing.PrintCapabilities> tiskárny a vytvořit <xref:System.Printing.PrintTicket> pomocí kódu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer a tisková fronta  
 <xref:System.Printing.PrintServer> Třída představuje síť tiskového serveru a <xref:System.Printing.PrintQueue> třída reprezentuje tiskárnu a výstupní fronty úloh s ním spojená. Tato rozhraní API společně umožňují pokročilé funkce správy serveru tiskových úloh. A <xref:System.Printing.PrintServer>, nebo jednu z odvozených tříd, se používá ke správě <xref:System.Printing.PrintQueue>. <xref:System.Printing.PrintQueue.AddJob%2A> Metody slouží k vložení nové tiskové úlohy do fronty.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Printing.LocalPrintServer> a přístup k jeho výchozí <xref:System.Printing.PrintQueue> pomocí kódu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter>, S jeho: n <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody, se používá k zápisu dokumentů XPS <xref:System.Printing.PrintQueue>. Například <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> metoda se používá k výstupní dokument XPS a <xref:System.Printing.PrintTicket> synchronně. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> Metoda se používá k výstupní dokument XPS a <xref:System.Printing.PrintTicket> asynchronně.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Xps.XpsDocumentWriter> pomocí kódu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Metody poskytují také způsoby, jak vytisknout. Zobrazit [tisk souborů XPS z programu](how-to-programmatically-print-xps-files.md). Další informace.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Cesta tisku GDI  
 Zatímco [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace nativně podporují cesta tisku XPS [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a aplikace Windows Forms můžete také využít některé funkce XPS. Ovladač tiskárny XPS (XPSDrv) můžete převést [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] na základě výstup do formátu XPS. Pro pokročilé scénáře se podporuje vlastní převod obsahu pomocí [Microsoft XPS dokumentu převaděč (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). Obdobně [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací můžete také výstup na [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] cesta tisku voláním jedné z <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> nebo <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> třídy a jako cíl s vyznačením bez XpsDrv tiskárny, tiskové fronty.  

Pro aplikace, které nevyžadují XPS funkce nebo podporu, aktuální [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] cesta tisku zůstane beze změny.  
  
- Pro další referenční materiál o [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] vytisknout cestu a různé možnosti převodu XPS, naleznete v tématu [Microsoft XPS dokumentu převaděč (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) a [ovladače tiskárny XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Model ovladače XPSDrv  
 Cesta tisku XPS zvyšuje efektivitu zařazování pomocí XPS formátu nativní zařazování tisku při tisku XPS – povolené tiskárnu nebo ovladače. Zjednodušené zařazování procesu eliminuje nutnost vytvoření souboru zprostředkující zařazování, například [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] datový soubor, předtím, než je zařazení dokumentu. Cesta tisku XPS můžete prostřednictvím menší velikost souborů pro zařazování omezit přenos v síti a výkon tiskového.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] je uzavřené formátu, který představuje výstup aplikace jako řadu objektů zavolá [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] služby vykreslování. Na rozdíl od [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], formát zařazování XPS představuje skutečný dokument bez nutnosti další interpretaci výstupu ovladači tiskárny na základě XPS (XPSDrv). Ovladače lze pracovat přímo s daty ve formátu. Tato funkce eliminuje požadováno, když použijete místo převody dat a barvu [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] soubory a [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]– na základě ovladačů tiskáren.  
  
 Velikosti souborů pro zařazování snižují obvykle použijete XPS – dokumenty, které cílí ovladači tiskárny XPS (XPSDrv) ve srovnání s jejich [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] ekvivalenty; však existují výjimky:  
  
- Vektorové grafiky, která je velmi složité, propracovat vícevrstvý nebo neefektivně písemné může být větší než rastrovými obrázky verze stejného obrázku.  
  
- Pro účely zobrazení obrazovky soubory XPS vložení písma zařízení i počítače písma; zatímco soubory zařazování GDI Nevkládat písma zařízení. Ale oba druhy písma jsou podsady (viz níže) a ovladače tiskárny můžete odebrat písma zařízení před odesláním souborů na tiskárnu.  
  
 Zmenšení velikosti zařazování se provádí prostřednictvím několika mechanismů:  
  
- **Písem**. Pouze znaky použité v rámci skutečné dokumentu jsou uložené v souboru XPS.  
  
- **Přidává rozšířenou podporu grafiky**. Nativní podpora pro primitiv transparentnost a přechodu se vyhnete rasterizační obsah [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentu.  
  
- **Identifikace běžných zdrojů**. Prostředky, které jsou používány více než jednou (například obrázek), který představuje firemní logo, které jsou považovány za sdílené prostředky a jsou načteny pouze jednou.  
  
- **Komprese ZIP**. Všechny dokumenty XPS pomocí komprese formátu ZIP.  
  
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
- [XPS – dokumenty](/windows/desktop/printdocs/documents)
- [Serializace a úložiště dokumentů](document-serialization-and-storage.md)
- [Převaděč (MXDC) dokumentů Microsoft XPS](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
