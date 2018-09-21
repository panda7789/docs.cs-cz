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
ms.openlocfilehash: 04ea64f0e6563012a3b272306df6be4575ed7659
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46478705"
---
# <a name="printing-overview"></a>Přehled tisku
Rozhraní Microsoft .NET Framework aplikace vývojářům, kteří používají Windows Presentation Foundation (WPF) mají nové bohatou Správa systému tisku a tisk [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. S [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], některé z těchto vylepšení tiskovém systému jsou také k dispozici pro vývojáře vytvářející [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace a vývojáře, kteří používají nespravovaný kód. V jádru služby tato nová funkce je nový [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] formát souboru a [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] cesta tisku.  
  
 Toto téma obsahuje následující části.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>O XPS  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] je ve formátu elektronických dokumentů, formát souboru pro zařazování a jazyk pro popis stránky. Je ve formátu otevřít dokument, který používá [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]a další oborové standardy pro vytváření multiplatformních dokumentů. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] zjednodušuje proces, podle kterého digitální dokumenty jsou vytvořené sdílené, vytisknout, zobrazit a archivovat. Další informace o [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], najdete v článku [XPS webu](https://www.microsoft.com/xps).  
  
 Několik postupů pro tisk [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] na základě obsahu použitím [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je ukázán v [programově tisk souborů XPS z](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Možná bude užitečné odkazují tyto ukázky během kontroly obsahu obsažené v tomto tématu. (Vývojáři nespravovaného kódu by měla najdete v dokumentaci [MXDC_ESCAPE funkce](https://msdn.microsoft.com/library/windows/desktop/dd162739.aspx). Musíte použít Windows Forms vývojáři [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] v <xref:System.Drawing.Printing> obor názvů, který nepodporuje kompletní [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] cesta tisku, ale podporuje cesta tisku GDI XPS hybridní. Zobrazit **architektura cesta tisku** níže.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Cesta tisku XPS  
 [!INCLUDE[TLA#tla_metro](../../../../includes/tlasharptla-metro-md.md)] Je nová cesta tisku [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] funkce, které předefinuje zpracování tisku v aplikacích Windows. Protože [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] můžete nahradit jazyk prezentace dokumentu (například ve formátu RTF), formát zařazování tisku (například WMF) a jazyk pro popis stránky (jako je například PCL nebo Postscript); udržuje nová cesta tisku [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátu z aplikace publikování do konečné zpracování v ovladače tiskárny nebo zařízení.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Cesta tisku je postavena [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] model ovladače tiskárny (XPSDrv), který poskytuje několik výhod pro vývojáře, jako [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] tisku, vylepšená podpora barvu a výrazně vyšší výkon tiskového. (Další informace o XPSDrv, najdete v článku [Windows Driver Development Kit](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
 Operace služby zařazování tisku pro [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentů je v podstatě stejný jako v předchozích verzích Windows. Nicméně je vylepšená pro podporu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] cesta tisku kromě existující [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] cesta tisku. Nová cesta tisku nativně využívá [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] soubor tiskové fronty. Při uživatelském režimu ovladače tiskárny napsané pro předchozí verze [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] budou nadále fungovat, [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ovladače tiskárny (XPSDrv) potřebné k použití [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] cesta tisku.  
  
 Výhody [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] cesta tisku jsou významné a zahrnují:  
  
-   [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] Podpora tisku  
  
-   Nativní podpora profilů pokročilé barev, mezi které patří 32 bitů na kanál, CMYK, pojmenované barvy, barvy n a nativní podporu transparentnosti a přechody.  
  
-   Zvýšení výkonu tisku pro obě rozhraní .NET Framework a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikací založených na.  
  
-   Standardní [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátu.  
  
 Pro základní scénáře, tisku a jednoduché a intuitivní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] je k dispozici s jedním vstupním bodem pro odeslání uživatelského rozhraní, konfigurace a úlohy. Pro pokročilé scénáře, přidá se další podporu pro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] přizpůsobení (nebo vůbec žádné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vůbec), synchronní nebo asynchronní tisku a tisk funkcí služby batch. V obou variantách nabízí podpora tisku v režimu plné nebo částečné důvěryhodnosti.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] byla navržena s rozšíření v úvahu. S použitím rozhraní rozšiřitelnosti, funkcí a možností lze přidat do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] modulární způsobem. Rozšíření funkce:  
  
-   Tisk schématu. Veřejné schématu se pravidelně aktualizuje a umožňuje rychlé rozšíření funkcí zařízení. (Viz **funkce PrintTicket a printcapabilities –** níže.)  
  
-   Rozšiřitelné filtr kanálu. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Tiskárny ovladač (XPSDrv) filtr kanálu byl navržených tak, aby s přímým přístupem a škálovatelné tisk [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumenty. (Vyhledávání "XPSDrv" v [Windows Driver Kit](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
### <a name="print-path-architecture"></a>Cesta tisku architektury  
 Přestože obě [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a aplikace rozhraní .NET Framework podporují [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a používání aplikací modelu Windows Forms [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] k [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] převod, chcete-li vytvořit [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátovaný obsah pro [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]ovladače tiskárny (XPSDrv). Tyto aplikace nemusí používat [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] cesta tisku a můžete dál používat [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] na základě tisk. Ale většina [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce a vylepšení jsou dostupné jenom pro aplikace, které se zaměřují [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] cesta tisku.  
  
 Povolit používání tiskárny založené na XPSDrv podle [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a aplikace Windows Forms [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ovladače tiskárny (XPSDrv) podporuje počítačový převod [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] k [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátu. XPSDrv model také poskytuje převaděč pro [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] k [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formátu tak, aby [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikací můžete vytisknout [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty. Pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací, převod [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] k [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formát se automaticky pomocí provádí <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> třídy pokaždé, když tiskové fronty cíl operace zápisu, nemají ovladač XPSDrv. (Aplikace Windows Forms nelze tisknout [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty.)  
  
 Následující obrázek znázorňuje tisku subsystému a definuje části poskytované [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]a části určené dodavatelé softwaru a hardwaru.  
  
 ![Tisk XPS systému](../../../../docs/framework/wpf/advanced/media/xpsprint.PNG "XPSPrint")  
  
### <a name="basic-xps-printing"></a>Tisk základní XPS  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Definuje i základní a rozšířená [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Pro tyto aplikace, které nevyžadují rozsáhlou vytisknout přizpůsobení nebo přístup ke kompletní [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sadu funkcí, podpora tisku na úrovni basic je k dispozici. Základní podpora tisku je k dispozici prostřednictvím dialogového okna Tisk ovládací prvek, který vyžaduje minimální konfiguraci a funkcích známým [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Mnoho [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce jsou k dispozici prostřednictvím tohoto modelu zjednodušené tisku.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Řízení poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguraci a [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] úlohy odeslání. Informace o tom, jak vytvořit instanci a pomocí ovládacího prvku, naleznete v tématu [vyvolání dialogového okna Tisk](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Pokročilé XPS tisku  
 Pro přístup k úplné sadě [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce, pokročilé tisk [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] musí být použita. Několik relevantní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] jsou popsány podrobněji níže. Úplný seznam [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] cesta tisku [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], najdete v článku <xref:System.Windows.Xps> a <xref:System.Printing> odkazy na obor názvů.  
  
#### <a name="printticket-and-printcapabilities"></a>Funkce PrintTicket a printcapabilities –  
 <xref:System.Printing.PrintTicket> a <xref:System.Printing.PrintCapabilities> třídy jsou základem pro pokročilé [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce. Oba typy objektů jsou [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ve formátu struktury tisk objektově orientovaný funkcí, jako je třeba kolace oboustranný tisk, připojování, atd. Tyto struktury jsou definovaná pomocí schématu rozhraní tisku. A <xref:System.Printing.PrintTicket> tiskárnu dává pokyn, jak zpracovávat tiskové úlohy. <xref:System.Printing.PrintCapabilities> Třída definuje možnosti tiskárny. Pomocí dotazu na možnosti tiskárny <xref:System.Printing.PrintTicket> je možné vytvořit, že přijímá naplno využít tiskárny na podporované funkce. Podobně se lze vyvarovat nepodporované funkce.  
  
 Následující příklad ukazuje, jak provádět dotazy <xref:System.Printing.PrintCapabilities> tiskárny a vytvořit <xref:System.Printing.PrintTicket> pomocí kódu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](../../../../samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer a tisková fronta  
 <xref:System.Printing.PrintServer> Třída představuje síť tiskového serveru a <xref:System.Printing.PrintQueue> třída reprezentuje tiskárnu a výstupní fronty úloh s ním spojená. Společně tyto [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] umožňují pokročilé funkce správy serveru tiskových úloh. A <xref:System.Printing.PrintServer>, nebo jednu z odvozených tříd, se používá ke správě <xref:System.Printing.PrintQueue>. <xref:System.Printing.PrintQueue.AddJob%2A> Metody slouží k vložení nové tiskové úlohy do fronty.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Printing.LocalPrintServer> a přístup k jeho výchozí <xref:System.Printing.PrintQueue> pomocí kódu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter>, S jeho: n <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody, se používá k zápisu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumenty <xref:System.Printing.PrintQueue>. Například <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> metoda se používá pro výstup [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentu a <xref:System.Printing.PrintTicket> synchronně. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> Metoda se používá pro výstup [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentu a <xref:System.Printing.PrintTicket> asynchronně.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Xps.XpsDocumentWriter> pomocí kódu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Metody poskytují také způsoby, jak vytisknout. Zobrazit [tisk souborů XPS z programu](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Další informace.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Cesta tisku GDI  
 Zatímco [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace nativně podporují [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] cesta tisku [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a aplikace Windows Forms můžete taky využít výhod některé [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Ovladače tiskárny (XPSDrv) můžete převést [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] výstup na základě [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátu. Pro pokročilé scénáře se podporuje vlastní převod obsahu pomocí [Microsoft XPS dokumentu převaděč (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx). Obdobně [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikací můžete také výstup na [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] cesta tisku voláním jedné z <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> nebo <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> třídy a jako cíl s vyznačením bez XpsDrv tiskárny, tiskové fronty.  

Pro aplikace, které nevyžadují [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce nebo podporu, aktuální [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] cesta tisku zůstane beze změny.  
  
-   Pro další referenční materiál o [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] tisk cestu a různých [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] naleznete v tématu Možnosti převodu [Microsoft XPS dokumentu převaděč (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx) a "XPSDrv" v [Windows Driver Kit](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Model ovladače XPSDrv  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Cesta tisku zvyšuje efektivitu zařazování pomocí [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátu nativní zařazování tisku při tisku [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] -povoleno tiskárnu nebo ovladač. Zjednodušené zařazování procesu eliminuje nutnost vytvoření souboru zprostředkující zařazování, například [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] datový soubor, předtím, než je zařazení dokumentu. Prostřednictvím menší velikost souborů zařazování [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] cesta tisku můžete omezit přenos v síti a zlepšit výkon tisku.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] je uzavřené formátu, který představuje výstup aplikace jako řadu objektů zavolá [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] služby vykreslování. Na rozdíl od [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formát zařazování představuje skutečný dokument bez nutnosti další interpretaci výstupu do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]– na základě ovladače tiskárny (XPSDrv). Ovladače lze pracovat přímo s daty ve formátu. Tato funkce eliminuje požadováno, když použijete místo převody dat a barvu [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] soubory a [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]– na základě ovladačů tiskáren.  
  
 Velikosti souborů pro zařazování snižují obvykle použijete [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumenty, které se zaměřují [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ovladače tiskárny (XPSDrv) ve srovnání s jejich [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] ekvivalenty; však existují výjimky:  
  
-   Vektorové grafiky, která je velmi složité, propracovat vícevrstvý nebo neefektivně písemné může být větší než rastrovými obrázky verze stejného obrázku.  
  
-   Pro účely zobrazení obrazovky soubory XPS vložení písma zařízení i počítače písma; zatímco soubory zařazování GDI Nevkládat písma zařízení. Ale oba druhy písma jsou podsady (viz níže) a ovladače tiskárny můžete odebrat písma zařízení před odesláním souborů na tiskárnu.  
  
 Zmenšení velikosti zařazování se provádí prostřednictvím několika mechanismů:  
  
-   **Písem**. Jsou uloženy pouze znaky použít v rámci skutečné dokumentu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] souboru.  
  
-   **Přidává rozšířenou podporu grafiky**. Nativní podpora pro primitiv transparentnost a přechodu se vyhnete rasterizační obsah [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentu.  
  
-   **Identifikace běžných zdrojů**. Prostředky, které jsou používány více než jednou (například obrázek), který představuje firemní logo, které jsou považovány za sdílené prostředky a jsou načteny pouze jednou.  
  
-   **Komprese ZIP**. Všechny [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumenty pomocí komprese formátu ZIP.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.PrintDialog>  
 <xref:System.Windows.Xps.XpsDocumentWriter>  
 <xref:System.Windows.Xps.Packaging.XpsDocument>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.PrintQueue>  
 [Témata s postupy](../../../../docs/framework/wpf/advanced/printing-how-to-topics.md)  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [XPS](https://www.microsoft.com/xps)  
 [Serializace a úložiště dokumentů](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)  
 [Převaděč (MXDC) dokumentů Microsoft XPS](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx)
