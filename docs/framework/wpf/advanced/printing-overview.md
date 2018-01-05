---
title: "Přehled tisku"
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
caps.latest.revision: "35"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91ccf1f98d9e1e2f5784246cf30995b689a0b94b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="printing-overview"></a>Přehled tisku
S [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], vývojáři aplikace pomocí [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] mít širokou škálu nového systému správy tisku a tiskového [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]. S [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], některé z těchto vylepšení tiskový systém jsou také k dispozici pro vývojáře vytváření [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikací a vývojáře, kteří používají nespravovaného kódu. Základem tato nová funkce je nové [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] formát souboru a [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] tiskové cestu.  
  
 Toto téma obsahuje následující části.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>O XPS  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]je formátu elektronických dokumentů, formát souboru pro zařazování a jazyk popis stránky. Je formátu otevřít dokument, který používá [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)]a další oborových standardů k vytvoření dokumentů napříč platformami. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]zjednodušuje proces, podle kterého digitální dokumenty jsou vytvořeny, sdílené, vytisknout, zobrazit a archivovat. Další informace o [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], najdete v článku [XPS webu](http://www.microsoft.com/xps).  
  
 Několik postupů pro tisk [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] na základě obsahu pomocí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je ukázán v [programové soubory XPS tiskových](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Možná bude vhodné, odkazují tyto ukázky během kontrolu obsahu, které jsou obsažené v tomto tématu. (Vývojáři nespravovaného kódu by měla naleznete v dokumentaci k [MXDC_ESCAPE funkce](https://msdn.microsoft.com/library/windows/desktop/dd162739.aspx). [!INCLUDE[TLA2#tla_winforms#initcap](../../../../includes/tla2sharptla-winformssharpinitcap-md.md)]Vývojáři musí použít [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] v <xref:System.Drawing.Printing> obor názvů, který nepodporuje kompletní [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] cesta pro tisk, ale nemá podporu tisku cestu hybridní GDI XPS. V tématu **cesta Architektura tisku** níže.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Cesta pro tisk XPS  
 [!INCLUDE[TLA#tla_metro](../../../../includes/tlasharptla-metro-md.md)] Je nová cesta pro tisk [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] funkce, která definuje nové zpracování tisk v [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)] aplikace. Protože [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] můžete nahradit jazyk prezentace dokumentů (například RTF), služba zařazování tisku formátu (například WMF) a jazyk popis stránky (například PCL nebo Postscript); nové tiskové cesta udržuje [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátu z aplikace publikace konečnému zpracování v ovladače tiskárny nebo zařízení.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Tiskové cesta je založena na [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] model ovladače tiskárny (XPSDrv), která poskytuje několik výhod pro vývojáře, jako [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] tisk, vylepšená podpora barev a významné zlepšení výkonu tisku. (Další informace o XPSDrv, najdete v článku [Windows Driver Development Kit](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
 Operaci služby zařazování tisku pro [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentů je v podstatě stejný jako v předchozích verzích [!INCLUDE[TLA2#tla_mswin](../../../../includes/tla2sharptla-mswin-md.md)]. Však se rozšířily na podporu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tiskové cesta kromě existující [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] tiskové cestu. Nová cesta tiskové nativně využívá [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] soubor tiskové fronty. Při napsaných pro předchozí verze ovladače tiskárny uživatelského režimu [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] budou nadále fungovat, [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ovladač tiskárny (XPSDrv) je potřebné k použití [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tiskové cestu.  
  
 Výhody [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tiskové cesta jsou důležité a zahrnují:  
  
-   [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)]Podpora tisku  
  
-   Nativní podpora profilů pokročilé barev, které zahrnují 32 bitů na kanál, CMYK, s názvem barvy, n barvy a nativní podporu průhlednosti a přechody.  
  
-   Zvýšení výkonu tiskového pro obě [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] a [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] aplikace založené na.  
  
-   Oborový standard [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátu.  
  
 Pro základní tiskové scénáře a jednoduché a intuitivní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] je k dispozici jeden vstupní bod pro uživatelské rozhraní, konfiguraci a úlohy odeslání. Pro pokročilé scénáře se má přidat další podporu pro [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] přizpůsobení (nebo žádné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vůbec), synchronní nebo asynchronní tisk a tisk funkcí služby batch. Obě možnosti tisku podporují v režimu úplné nebo částečné důvěryhodnosti.  
  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]byla vytvořena rozšiřitelnost v paměti. Pomocí rozhraní rozšiřitelnosti, funkce a možnosti lze přidat do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] modulární způsobem. Funkce rozšíření patří:  
  
-   Tisk schématu. Schéma veřejné se pravidelně aktualizuje a umožňuje rychlé rozšíření možnosti zařízení. (Viz **PrintTicket a PrintCapabilities** níže.)  
  
-   Kanál Extensible filtru. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Tiskárny ovladač (XPSDrv) filtru kanálu byl navržených k povolení přímé a škálovatelné tisk z [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumenty. (Vyhledávání "XPSDrv" v [Kit ovladačů systému Windows](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).)  
  
### <a name="print-path-architecture"></a>Architektura cesta tisku  
 I při [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)] aplikace podporují [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)], [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] aplikace používat [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] k [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] převod před vytvořením [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátovaný obsah pro [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ovladač tiskárny (XPSDrv). Tyto aplikace nemusí používat [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tiskových cestu a můžete dál používat [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] na základě tisku. Ale většina [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce a vylepšení, jsou dostupné jenom pro aplikace, které cílí [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tiskové cestu.  
  
 Povolit používání na základě XPSDrv tiskárny pomocí [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] aplikace, [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ovladač tiskárny (XPSDrv) podporuje počítačový převod [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] k [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátu. XPSDrv model také poskytuje převaděč pro [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] k [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formátu tak, aby [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace můžete vytisknout [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty. Pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace, převod [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] k [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] formátu probíhá automaticky <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> třídy vždy, když tiskové fronty cíl operace zápisu nemá. má XPSDrv ovladač. ([!INCLUDE[TLA2#tla_winforms#initcap](../../../../includes/tla2sharptla-winformssharpinitcap-md.md)] aplikace nelze tisknout [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumenty.)  
  
 Následující obrázek znázorňuje podsystém a definuje části poskytované [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]a části definované dodavatelé softwaru a hardwaru.  
  
 ![XPS tisku systému](../../../../docs/framework/wpf/advanced/media/xpsprint.PNG "XPSPrint")  
  
### <a name="basic-xps-printing"></a>Tisk základní XPS  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]Definuje i základní a rozšířená [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Pro tyto aplikace, které nevyžadují rozsáhlou tisk přizpůsobení nebo přístup k kompletní [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] sady funkcí základní tiskové podpora je k dispozici. Základní podpora tisku je k dispozici prostřednictvím ovládacího prvku tiskové dialogu, který vyžaduje minimální konfigurace a funkce známým [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Mnoho [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce jsou dostupné, pomocí tohoto modelu zjednodušené tisku.  
  
#### <a name="printdialog"></a>PrintDialog  
 <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Řízení poskytuje jeden vstupní bod pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguraci a [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] úlohy odeslání. Informace o tom, jak vytvořit a používat ovládací prvek najdete v tématu [vyvolat dialogové okno tisku](../../../../docs/framework/wpf/advanced/how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Pokročilé XPS tisk  
 Pro přístup k kompletní sadu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce Rozšířené print [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] se musí použít. Několik relevantní [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] jsou podrobně popsány v níže. Úplný seznam [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tiskové cesta [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], najdete v článku <xref:System.Windows.Xps> a <xref:System.Printing> odkazy na obor názvů.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket a PrintCapabilities  
 <xref:System.Printing.PrintTicket> a <xref:System.Printing.PrintCapabilities> třídy jsou základ pro rozšířené [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce. Oba typy objektů jsou [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] formátu struktury tiskové funkce, například kolace, oboustranný tisk, – sešívání atd. Tyto struktury jsou definované schéma tisku. A <xref:System.Printing.PrintTicket> dá pokyn tiskárnu, jak zpracovávat tiskové úlohy. <xref:System.Printing.PrintCapabilities> Třída definuje možnosti tiskárny. Pomocí dotazu na možnosti tiskárně, <xref:System.Printing.PrintTicket> lze vytvořit, je funkce podporované trvá všech výhod tiskárnu. Podobně se vyhnout nepodporované funkce.  
  
 Následující příklad ukazuje, jak dotazovat <xref:System.Printing.PrintCapabilities> tiskárny a vytvořte <xref:System.Printing.PrintTicket> pomocí kódu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](../../../../samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>Tiskový_server a tiskové fronty  
 <xref:System.Printing.PrintServer> Třída reprezentuje tiskového serveru sítě a <xref:System.Printing.PrintQueue> třída reprezentuje tiskárnu a výstupní fronty úloh s ním spojená. Společně tyto [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] povolit Rozšířená správa serveru tiskových úloh. A <xref:System.Printing.PrintServer>, nebo jeden z jejich odvozené třídy, se používá ke správě <xref:System.Printing.PrintQueue>. <xref:System.Printing.PrintQueue.AddJob%2A> Metoda slouží k vložení nové tiskové úlohy do fronty.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Printing.LocalPrintServer> a přístup k jeho výchozí <xref:System.Printing.PrintQueue> pomocí kódu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 <xref:System.Windows.Xps.XpsDocumentWriter>, S jeho mnoho <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody, se používá k zápisu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumenty k <xref:System.Printing.PrintQueue>. Například <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> metoda se používá k výstupu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentu a <xref:System.Printing.PrintTicket> synchronně. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> Metoda se používá k výstupu [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumentu a <xref:System.Printing.PrintTicket> asynchronně.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Xps.XpsDocumentWriter> pomocí kódu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 <xref:System.Printing.PrintQueue.AddJob%2A> Metody také poskytují možností tisku. V tématu [tisk prostřednictvím kódu programu XPS soubory](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md). Podrobnosti.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Cesta pro tisk GDI  
 Při [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace nativně podporují [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tiskové cesta [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] aplikace můžete také využít výhod některé [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce. [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Ovladač tiskárny (XPSDrv) můžete převést [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] na základě výstup do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] formátu. Složitější scénáře vlastní převod obsahu je podporováno pomocí [Microsoft XPS dokumentu převaděč (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx). Podobně [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace může také výstup do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] tiskové cestu mezi voláním <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> nebo <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter> třídy a určení tiskárny bez XpsDrv jako cíl tiskové fronty.  

Pro aplikace, které nevyžadují [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] funkce nebo podporu, aktuální [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] tiskové cesta zůstává beze změny.  
  
-   Pro odkaz na další informace o [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] tisku cestu a různé [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] najdete v části Možnosti převodu [Microsoft XPS dokumentu převaděč (MXDC)](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx) a "XPSDrv" v [Windows ovladač Kit](https://msdn.microsoft.com/library/windows/hardware/ff557573.aspx).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Model ovladače XPSDrv  
 [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] Tiskové cesta ke zlepšení efektivity zařazovací služby pomocí [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] jako formát nativní zařazování tisku při tisku na [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] -povolit tiskárnu nebo ovladač. Proces zjednodušené zařazených eliminuje potřebu generování zprostředkující zařazování souboru, například [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] datový soubor, než je zařazených dokumentu. Prostřednictvím menší velikost souborů zařazování [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] tiskové cestu můžete omezit přenos v síti a tiskové výkon.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)]je uzavřené formátu, který představuje výstupní aplikace jako řadu volání do [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] pro vykreslování služby. Na rozdíl od [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] zařazování formát představuje skutečný dokumentu bez nutnosti další výklad při výstup do [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)]– na základě ovladače tiskárny (XPSDrv). Ovladače mohou pracovat přímo na základě dat ve formátu. Tato funkce eliminuje data a barvu převody místo požadované při použití [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] soubory a [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]– na základě ovladačů tiskáren.  
  
 Velikosti souborů zařazování jsou omezeny obvykle při použití [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumenty cílených [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] ovladač tiskárny (XPSDrv) ve srovnání s jejich [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] ekvivalenty; existují však výjimky:  
  
-   Vektorové grafiky, který je velmi složité, víceúrovňová nebo neefektivnímu napsané může být větší než rastrové verze stejného obrázku.  
  
-   Pro účely zobrazení obrazovky soubory XPS vložení písma zařízení a také na počítači písem; zatímco soubory zařazování GDI není vložená zařízení písma. Ale oba typy písem podsady (viz níže) a ovladače tiskárny můžete odebrat písma zařízení před přenosem souboru na tiskárnu.  
  
 Zmenšení velikosti zařazování se provádí prostřednictvím několik mechanismů:  
  
-   **Vkládání písem**. Pouze znaky používaných v rámci skutečné dokumentu jsou uložené v [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] souboru.  
  
-   **Podpora grafiky rozšířené**. Nativní podpora pro průhlednost a přechodu primitiv zabraňuje rasterizační obsahu [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] dokumentu.  
  
-   **Identifikace běžných zdrojů**. Prostředky, které používá více časů (například obrázek, který představuje firemní logo) se považují za sdílené prostředky a jsou načteny pouze jednou.  
  
-   **Komprese ZIP**. Všechny [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] dokumenty komprimování ZIP.  
  
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
 [XPS](http://www.microsoft.com/xps)  
 [Serializace a úložiště dokumentů](../../../../docs/framework/wpf/advanced/document-serialization-and-storage.md)  
 [Převaděč (MXDC) modul dokumentů Microsoft XPS](https://msdn.microsoft.com/library/windows/desktop/ff686803.aspx)
