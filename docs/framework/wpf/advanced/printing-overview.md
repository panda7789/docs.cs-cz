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
ms.openlocfilehash: 902d51341850b5245b9fa6410b1954b2ab373bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187204"
---
# <a name="printing-overview"></a>Přehled tisku
S rozhraním Microsoft .NET Framework mají vývojáři aplikací používající windows presentation foundation (WPF) bohatou novou sadu rozhraní API pro správu tisku a tiskových systémů. V systému Windows Vista jsou některá z těchto vylepšení tiskového systému k dispozici také vývojářům, kteří vytvářejí aplikace pro Windows Forms, a vývojářům používajícím nespravovaný kód. Jádrem této nové funkce je nový formát souboru XML Paper Specification (XPS) a cesta k tisku XPS.  
  
 Toto téma obsahuje tyto části:  
  
<a name="introduction_to_XPS"></a>
## <a name="about-xps"></a>O společnosti XPS  
 XPS je formát elektronického dokumentu, formát souboru cívky a jazyk popisu stránky. Jedná se o otevřený formát dokumentu, který používá XML, otevřené konvence balení (OPC) a další oborové standardy k vytváření dokumentů pro různé platformy. Xps zjednodušuje proces vytváření, sdílení, tisku, prohlížení a archivace digitálních dokumentů. Další informace o systému XPS naleznete v [tématu XPS Documents](/windows/desktop/printdocs/documents).  
  
 Několik technik pro tisk obsahu založeného na systému XPS pomocí WPF je demonstrováno v [programově tisku xps souborů](how-to-programmatically-print-xps-files.md). Může být užitečné odkazovat na tyto ukázky během kontroly obsahu obsaženého v tomto tématu. (Vývojáři nespravovaného kódu by měli vidět dokumentaci pro [funkci MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Vývojáři windows forms musí <xref:System.Drawing.Printing> používat rozhraní API v oboru názvů, který nepodporuje úplnou cestu tisku XPS, ale podporuje hybridní cestu tisku GDI-XPS. Viz **Architektura cesty tisku** níže.)  
  
<a name="XPS_print_path_intro"></a>
## <a name="xps-print-path"></a>Cesta k tisku XPS  
 Cesta k tisku specifikace papíru XML (XPS) je nová funkce systému Windows, která nově definuje způsob zpracování tisku v aplikacích systému Windows. Vzhledem k tomu, že systém XPS může nahradit jazyk prezentace dokumentu (například RTF), formát zařazování tisku (například WMF) a jazyk popisu stránky (například PCL nebo Postscript); nová cesta k tisku udržuje formát XPS od publikace aplikace až po konečné zpracování v tiskovém ovladači nebo zařízení.  
  
 Tisková cesta XPS je postavena na modelu ovladače tiskárny XPS (XPSDrv), který poskytuje vývojářům několik výhod, jako je například tisk "to, co vidíte, je to, co získáte" (WYSIWYG), vylepšená podpora barev a výrazně vyšší výkon tisku. (Další informace o notebooku XPSDrv naleznete v [dokumentaci k sadě ovladačů systému Windows](/windows-hardware/drivers/).)  
  
 Provoz služby zařazování tisku pro dokumenty XPS je v podstatě stejný jako v předchozích verzích systému Windows. Byla však rozšířena tak, aby podporovala cestu tisku XPS kromě existující cesty tisku GDI. Nová cesta tisku nativně spotřebovává soubor zařazování XPS. Zatímco ovladače tiskárny v uživatelském režimu napsané pro předchozí verze systému Windows budou i nadále fungovat, k použití tiskové cesty XPS je nutný ovladač tiskárny XPS (XPSDrv).  
  
 Výhody tiskové cesty XPS jsou významné a zahrnují:  
  
- Podpora tisku WYSIWYG  
  
- Nativní podpora pokročilých profilů barev, které zahrnují 32 bitů na kanál (bpc), CMYK, pojmenované barvy, n-inkousty a nativní podporu průhlednosti a přechodů.  
  
- Zlepšený výkon tisku pro aplikace založené na rozhraní .NET Framework i Win32.  
  
- Standardní formát XPS.  
  
 Pro základní tiskové scénáře je k dispozici jednoduché a intuitivní rozhraní API s jediným vstupním bodem pro uživatelské rozhraní, konfiguraci a odeslání úlohy. Pro pokročilé scénáře je přidána [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] další podpora [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pro přizpůsobení (nebo vůbec žádné), synchronní nebo asynchronní tisk a možnosti dávkového tisku. Obě možnosti poskytují podporu tisku v režimu úplné nebo částečné důvěryhodnosti.  
  
 Systém XPS byl navržen s ohledem na rozšiřitelnost. Pomocí rozhraní rozšiřitelnosti lze funkce a možnosti přidat do systému XPS modulárním způsobem. Funkce rozšiřitelnosti zahrnují:  
  
- Schéma tisku. Veřejné schéma je pravidelně aktualizováno a umožňuje rychlé rozšíření možností zařízení. (Viz **PrintTicket a PrintCapabilities** níže.)  
  
- Rozšiřitelný kanál filtru. Kanál filtru ovladače tiskárny XPS (XPSDrv) byl navržen tak, aby umožňoval přímý i škálovatelný tisk dokumentů XPS. Další informace naleznete [v tématu Ovladače tiskáren XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).
  
### <a name="print-path-architecture"></a>Architektura tiskových cest  
 Zatímco aplikace Win32 i .NET Framework podporují aplikace XPS, Win32 a Windows Forms, používají převod GDI na XPS za účelem vytvoření obsahu ve formátu XPS pro ovladač tiskárny XPS (XPSDrv). Tyto aplikace nejsou nutné k použití cesty tisku XPS a mohou nadále používat rozšířený metafile (EMF) založený na tisku. Většina funkcí a vylepšení systému XPS je však k dispozici pouze aplikacím, které cílí na cestu tisku XPS.  
  
 Chcete-li povolit použití tiskáren založených na technologii XPSDrv aplikacemi Win32 a Windows Forms, podporuje ovladač tiskárny XPS (XPSDrv) převod formátu GDI na formát XPS. Model XPSDrv také poskytuje převodník pro formát XPS do GDI, takže aplikace Win32 mohou tisknout dokumenty XPS. U aplikací WPF se převod formátu XPS na GDI provádí automaticky <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> metodami a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metodami <xref:System.Windows.Xps.XpsDocumentWriter> třídy, kdykoli cílová tisková fronta operace zápisu nemá ovladač XPSDrv. (Aplikace Windows Forms nemohou tisknout dokumenty XPS.)  
  
 Následující obrázek znázorňuje tiskový subsystém a definuje části poskytované společností Microsoft a části definované dodavateli softwaru a hardwaru:  
  
 ![Snímek obrazovky ukazuje tiskový systém XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Základní tisk XPS  
 WPF definuje základní i pokročilé rozhraní API. Pro aplikace, které nevyžadují rozsáhlé přizpůsobení tisku nebo přístup k kompletní sadě funkcí XPS, je k dispozici základní podpora tisku. Základní podpora tisku je vystavena prostřednictvím ovládacího prvku [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]tiskového dialogu, který vyžaduje minimální konfiguraci a obsahuje známé . Pomocí tohoto zjednodušeného tiskového modelu je k dispozici mnoho funkcí XPS.  
  
#### <a name="printdialog"></a>PrintDialog  
 Ovládací <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> prvek poskytuje jeden [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]vstupní bod pro , konfigurace a XPS odeslání úlohy. Informace o vytvoření instance a použití ovládacího prvku naleznete v [tématu Invoke a Print Dialog](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Pokročilý tisk XPS  
 Pro přístup k úplné sadě funkcí XPS je nutné použít rozšířené rozhraní API pro tisk. Několik relevantních API je podrobněji popsáno níže. Úplný seznam souborů API cesty k tisku <xref:System.Windows.Xps> xps naleznete v odkazech a <xref:System.Printing> odkazech na obor názvů.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket a PrintCapabilities  
 <xref:System.Printing.PrintTicket> Třídy <xref:System.Printing.PrintCapabilities> a jsou základem pokročilých funkcí XPS. Oba typy objektů jsou struktury funkcí orientovaných na tisk ve formátu XML, jako je řazení, oboustranný tisk, sešívání atd. Tyto struktury jsou definovány schématem tisku. A <xref:System.Printing.PrintTicket> pokyn tiskárny, jak zpracovat tiskovou úlohu. Třída <xref:System.Printing.PrintCapabilities> definuje možnosti tiskárny. Dotazem na možnosti tiskárny <xref:System.Printing.PrintTicket> lze vytvořit a plně využít výhod podporovaných funkcí tiskárny. Podobně se lze vyhnout nepodporovaným funkcím.  
  
 Následující příklad ukazuje, jak <xref:System.Printing.PrintCapabilities> dotaz tiskárny a <xref:System.Printing.PrintTicket> vytvořit pomocí kódu.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer a tisková fronta  
 Třída <xref:System.Printing.PrintServer> představuje síťový tiskový server <xref:System.Printing.PrintQueue> a třída představuje tiskárnu a výstupní frontu úloh, která je k ní přidružena. Tato řešení API společně umožňují pokročilou správu tiskových úloh serveru. A <xref:System.Printing.PrintServer>nebo jeden z jeho odvozené třídy, se používá ke správě <xref:System.Printing.PrintQueue>. Metoda <xref:System.Printing.PrintQueue.AddJob%2A> se používá k vložení nové tiskové úlohy do fronty.  
  
 Následující příklad ukazuje, jak <xref:System.Printing.LocalPrintServer> vytvořit a <xref:System.Printing.PrintQueue> získat přístup k jeho výchozí pomocí kódu.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 An <xref:System.Windows.Xps.XpsDocumentWriter>, s <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> jeho <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> mnoha a metody, se používá <xref:System.Printing.PrintQueue>k zápisu XPS dokumenty . Metoda se <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> například používá k výstupu dokumentu <xref:System.Printing.PrintTicket> XPS a synchronně. Metoda <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> se používá k výstupu dokumentu <xref:System.Printing.PrintTicket> XPS a asynchronně.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Xps.XpsDocumentWriter> vytvořit pomocí kódu.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Metody <xref:System.Printing.PrintQueue.AddJob%2A> také poskytují způsoby tisku. Viz [Programově tisk souborů XPS](how-to-programmatically-print-xps-files.md). podrobnosti.  
  
<a name="GDI_Print_Path_intro"></a>
## <a name="gdi-print-path"></a>Cesta k tisku GDI  
 Zatímco aplikace WPF nativně podporují cestu tisku XPS, aplikace Win32 a Windows Forms mohou také využívat některé funkce XPS. Ovladač tiskárny XPS (XPSDrv) může převést výstup založený na GDI do formátu XPS. U pokročilých scénářů je vlastní převod obsahu podporován pomocí [převaděče dokumentů Microsoft XPS (MXDC).](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) Podobně wpf aplikace mohou také výstup na cestu tisku GDI <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> voláním <xref:System.Windows.Xps.XpsDocumentWriter> jedné z <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> nebo metody třídy a označení non-XpsDrv tiskárny jako cílové tiskové fronty.  

U aplikací, které nevyžadují funkce nebo podporu systému XPS, zůstane aktuální cesta k tisku GDI nezměněna.  
  
- Další referenční materiál na cestě k tisku GDI a různé možnosti převodu XPS naleznete v tématech [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) a [XPSDrv Printer Drivers](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>
## <a name="xpsdrv-driver-model"></a>Model ovladače XPSDrv  
 Tisková cesta XPS zvyšuje efektivitu zařazování pomocí systému XPS jako nativního formátu zařazování tisku při tisku do tiskárny nebo ovladače s podporou systému XPS. Zjednodušený proces zařazování eliminuje potřebu generovat zprostředkující soubor zařazování, například datový soubor EMF, před zařazováním dokumentu. Díky menším velikostem souborů zařazování může tisková cesta XPS snížit zatížení sítě a zlepšit výkon tisku.  
  
 EMF je uzavřený formát, který představuje výstup aplikace jako řadu volání do GDI pro vykreslování služeb. Na rozdíl od EMF představuje formát zařazování XPS skutečný dokument bez nutnosti další interpretace při výstupu do ovladače tiskárny založené na notebooku XPS (XPSDrv). Ovladače mohou pracovat přímo na datech ve formátu. Tato funkce eliminuje převody dat a barevného prostoru požadované při použití souborů EMF a tiskových ovladačů založených na GDI.  
  
 Velikost souborů zařazuje se obvykle snižuje, když používáte dokumenty XPS, které cílí na ovladač tiskárny XPS (XPSDrv) ve srovnání s jejich ekvivalenty EMF; existují však výjimky:  
  
- Vektorová grafika, která je velmi složitá, vícevrstvá nebo neefektivně napsaná, může být větší než bitmapovaná verze stejné grafiky.  
  
- Pro účely zobrazení obrazovky, XPS soubory vložit zařízení písma, stejně jako počítač-založené písma; vzhledem k tomu, že soubory zařazovacího zařízení GDI nevsousávají písma zařízení. Ale oba druhy písem jsou podsety (viz níže) a ovladače tiskárny mohou odstranit písma zařízení před přenosem souboru do tiskárny.  
  
 Snížení velikosti cívky se provádí pomocí několika mechanismů:  
  
- **Podmnožina písma**. V souboru XPS jsou uloženy pouze znaky použité v rámci skutečného dokumentu.  
  
- **Pokročilá podpora grafiky**. Nativní podpora pro transparentnost a základní přechod zabraňuje rastrování obsahu v dokumentu XPS.  
  
- **Identifikace společných zdrojů**. Prostředky, které se používají vícekrát (například obrázek, který představuje firemní logo) jsou považovány za sdílené prostředky a jsou načteny pouze jednou.  
  
- **Komprese ZIP**. Všechny dokumenty XPS používají kompresi ZIP.  
  
## <a name="see-also"></a>Viz také

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
- [Serializace a úložiště dokumentu](document-serialization-and-storage.md)
- [Microsoft XPS Převaděč dokumentů (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
