---
title: 'Postupy: Tisk souborů XPS pomocí programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: 6642fad7d20e60a8b92e5860b763511f4fc0be72
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169172"
---
# <a name="how-to-programmatically-print-xps-files"></a>Postupy: Tisk souborů XPS pomocí programu
<xref:System.Printing.PrintQueue.AddJob%2A> Můžete použít jedno přetížení metody k tisku [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] souborů bez otevírání <xref:System.Windows.Controls.PrintDialog> nebo, v zásadě [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] všechny najednou.  
  
 Můžete také tisknout [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] soubory pomocí řady <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod <xref:System.Windows.Xps.XpsDocumentWriter>. Další informace o [tisku dokumentu XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).  
  
 Dalším způsobem tisku [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] je <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> použít <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> metody<xref:System.Windows.Controls.PrintDialog> nebo ovládacího prvku. Viz [vyvolání dialogového okna pro tisk](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro použití metody se třemi parametry <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> jsou následující. V následujícím příkladu jsou uvedeny podrobnosti.  
  
1. Zjistěte, jestli je tiskárna XPSDrv tiskárnou. (Další informace o XPSDrv najdete v tématu [Přehled tisku](printing-overview.md) .)  
  
2. Pokud tiskárna není XPSDrv tiskárna, nastavte objekt Apartment vlákna na jedno vlákno.  
  
3. Vytvoření instance tiskového serveru a objektu tiskové fronty.  
  
4. Zavolejte metodu, určete název úlohy, soubor k vytištění a <xref:System.Boolean> příznak označující, zda se jedná o tiskárnu XPSDrv.  
  
 Následující příklad ukazuje, jak Batch vytisknout všechny [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] soubory v adresáři. I když aplikace vyzve uživatele k zadání adresáře, metoda <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]tří parametrů nevyžaduje. Dá se použít v jakékoli cestě kódu, kde máte [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] název souboru a cestu, kterou můžete předat.  
  
 Pokud je <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> <xref:System.Boolean> parametr <xref:System.Printing.PrintQueue.AddJob%2A> ,kterýsemusínacházetvpřípadě,žesepoužívájinánežXPSDrvtiskárna,musísepřetěžovat`false`se třemi parametry. Výchozí stav objektu apartment pro rozhraní .NET je však více vláken. Tato výchozí hodnota musí být obrácená, protože příklad předpokládá, že tiskárna není XPSDrv.  
  
 Existují dva způsoby, jak změnit výchozí nastavení. Jedním ze <xref:System.STAThreadAttribute> způsobů je jednoduše přidat (tj. "`[System.STAThreadAttribute()]`") těsně nad první `Main` řádek metody aplikace (obvykle "`static void Main(string[] args)`"). Mnoho aplikací `Main` však vyžaduje, aby metoda měla stav s více vlákny, takže existuje druhá metoda: <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> volání do samostatného vlákna, jehož <xref:System.Threading.Thread.SetApartmentState%2A>stav Apartment je nastaven na <xref:System.Threading.ApartmentState.STA> . Následující příklad používá tuto druhou techniku.  
  
 Proto příklad začíná vytvořením instance <xref:System.Threading.Thread> objektu a předáním metody **PrintXPS** jako <xref:System.Threading.ThreadStart> parametru. (Metoda **PrintXPS** je definována později v příkladu.) V dalším vlákně je vlákno nastaveno na jeden objekt Apartment. Jediný zbývající kód `Main` metody spustí nové vlákno.  
  
 Maso v příkladu je v `static`metodě **BatchXPSPrinter. PrintXPS** . Po vytvoření tiskového serveru a fronty se metoda vyzve uživatele k zadání adresáře obsahujícího [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] soubory. Po ověření existence adresáře a přítomnosti \*souborů. XPS v něm metoda přidá každý takový soubor do tiskové fronty. V příkladu se předpokládá, že tiskárna není XPSDrv, takže předáváme `false` poslední <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> parametr metody. Z tohoto důvodu metoda ověří [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] označení v souboru předtím, než se pokusí o jeho převod na jazyk popisu stránky tiskárny. Pokud se ověření nepovede, vyvolá se výjimka. Ukázkový kód zachytí výjimku, upozorní uživatele na ni a pak přejde k procesu dalšího [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] souboru.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Pokud používáte XPSDrv tiskárnu, můžete nastavit konečný parametr na `true`. V takovém případě, [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] vzhledem k tomu, že se jedná o jazyk popisu stránky tiskárny, Metoda odešle soubor na tiskárnu bez ověření nebo převedení na jiný jazyk popisu stránky. Pokud si nejste jistí, jestli aplikace bude používat XPSDrv tiskárnu, můžete aplikaci upravit tak, aby si přečetla <xref:System.Printing.PrintQueue.IsXpsDevice%2A> vlastnost a větev podle toho, co najde.  
  
 Vzhledem k tomu, že bude zpočátku k dispozici málo XPSDrv tiskáren po [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] vydání a Microsoft .NET Framework, může být nutné promaskovat neXPSDrv tiskárnu jako tiskárnu XPSDrv. Provedete to tak, že přidáte Pipelineconfig. XML do seznamu souborů v následujícím klíči registru počítače, ve kterém je aplikace spuštěná:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<PseudoXPSPrinter>* \DependentFiles  
  
 *kde\<PseudoXPSPrinter >* je jakákoli tisková fronta. Počítač se pak musí restartovat.  
  
 Tento promaskování vám umožní předat `true` jako konečný <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> parametr, aniž by došlo k výjimce, ale vzhledem k tomu, že  *\<PseudoXPSPrinter >* není ve skutečnosti XPSDrv tiskárna, vytiskne se jenom uvolnění paměti.  
  
 **Poznámka:** Pro zjednodušení výše uvedený příklad používá přítomnost \*rozšíření. XPS jako test, který je [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]souborem. [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] Soubory ale nemusejí mít toto rozšíření. [IsXPS. exe (Nástroj pro dodržování isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) je jedním ze způsobů, jak otestovat soubor pro [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] účely platnosti.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.AddJob%2A>
- <xref:System.Threading.ApartmentState>
- <xref:System.STAThreadAttribute>
- [Dokumenty XPS](/windows/desktop/printdocs/documents)
- [Tisk dokumentu XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90))
- [Spravované a nespravované zřetězení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5s8ee185(v=vs.100))
- [isXPS. exe (Nástroj pro shodu isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100))
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
