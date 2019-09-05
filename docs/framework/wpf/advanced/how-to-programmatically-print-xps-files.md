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
ms.openlocfilehash: 5571544284326fa7ce26382711f696734a166df5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70254097"
---
# <a name="how-to-programmatically-print-xps-files"></a>Postupy: Tisk souborů XPS pomocí programu
Můžete použít jedno přetížení <xref:System.Printing.PrintQueue.AddJob%2A> metody pro tisk souborů XPS (XML Paper Specification) bez <xref:System.Windows.Controls.PrintDialog> otevírání nebo [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , v zásadě všechny najednou.  
  
 Soubory XPS můžete také tisknout pomocí mnoha <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A?displayProperty=nameWithType> metod a. <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A?displayProperty=nameWithType> Další informace najdete v tématu [Tisk dokumentu XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).  
  
 Dalším způsobem tisku XPS je použití <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A?displayProperty=nameWithType> metod nebo. <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A?displayProperty=nameWithType> Viz [vyvolání dialogového okna pro tisk](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Příklad  
 Hlavní kroky pro použití metody se třemi parametry <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> jsou následující. V následujícím příkladu jsou uvedeny podrobnosti.  
  
1. Zjistěte, jestli je tiskárna XPSDrv tiskárnou. (Další informace o XPSDrv najdete v tématu [Přehled tisku](printing-overview.md) .)  
  
2. Pokud tiskárna není XPSDrv tiskárna, nastavte objekt Apartment vlákna na jedno vlákno.  
  
3. Vytvoření instance tiskového serveru a objektu tiskové fronty.  
  
4. Zavolejte metodu, určete název úlohy, soubor k vytištění a <xref:System.Boolean> příznak označující, zda se jedná o tiskárnu XPSDrv.  
  
 Následující příklad ukazuje, jak Batch vytisknout všechny soubory XPS v adresáři. I když aplikace vyzve uživatele k zadání adresáře, metoda <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]tří parametrů nevyžaduje. Dá se použít v jakékoli cestě kódu, kde máte název a cestu souboru XPS, které můžete předat.  
  
 Pokud je <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> <xref:System.Boolean> parametr <xref:System.Printing.PrintQueue.AddJob%2A> ,kterýsemusínacházetvpřípadě,žesepoužívájinánežXPSDrvtiskárna,musísepřetěžovat`false`se třemi parametry. Výchozí stav objektu apartment pro rozhraní .NET je však více vláken. Tato výchozí hodnota musí být obrácená, protože příklad předpokládá, že tiskárna není XPSDrv.  
  
 Existují dva způsoby, jak změnit výchozí nastavení. Jedním ze <xref:System.STAThreadAttribute> způsobů je jednoduše přidat (tj. "`[System.STAThreadAttribute()]`") těsně nad první `Main` řádek metody aplikace (obvykle "`static void Main(string[] args)`"). Mnoho aplikací `Main` však vyžaduje, aby metoda měla stav s více vlákny, takže existuje druhá metoda: <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> volání do samostatného vlákna, jehož <xref:System.Threading.Thread.SetApartmentState%2A>stav Apartment je nastaven na <xref:System.Threading.ApartmentState.STA> . Následující příklad používá tuto druhou techniku.  
  
 Proto příklad začíná vytvořením instance <xref:System.Threading.Thread> objektu a předáním metody **PrintXPS** jako <xref:System.Threading.ThreadStart> parametru. (Metoda **PrintXPS** je definována později v příkladu.) V dalším vlákně je vlákno nastaveno na jeden objekt Apartment. Jediný zbývající kód `Main` metody spustí nové vlákno.  
  
 Maso v příkladu je v `static`metodě **BatchXPSPrinter. PrintXPS** . Po vytvoření tiskového serveru a fronty se metoda vyzve uživatele k zadání adresáře, který obsahuje soubory XPS. Po ověření existence adresáře a přítomnosti \*souborů. XPS v něm metoda přidá každý takový soubor do tiskové fronty. V příkladu se předpokládá, že tiskárna není XPSDrv, takže předáváme `false` poslední <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> parametr metody. Z tohoto důvodu metoda ověří kód XPS v souboru předtím, než se pokusí o jeho převod na jazyk popisu stránky tiskárny. Pokud se ověření nepovede, vyvolá se výjimka. Ukázkový kód zachytí výjimku, upozorní uživatele na ni a pak přejde k procesu dalšího souboru XPS.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Pokud používáte XPSDrv tiskárnu, můžete nastavit konečný parametr na `true`. V takovém případě, vzhledem k tomu, že XPS je jazykový popis stránky tiskárny, metoda pošle soubor do tiskárny bez ověření nebo převedení na jiný jazyk popisu stránky. Pokud si nejste jistí, jestli aplikace bude používat XPSDrv tiskárnu, můžete aplikaci upravit tak, aby si přečetla <xref:System.Printing.PrintQueue.IsXpsDevice%2A> vlastnost a větev podle toho, co najde.  
  
 Vzhledem k tomu, že bude zpočátku k dispozici málo XPSDrv tiskáren po [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] vydání a Microsoft .NET Framework, může být nutné promaskovat neXPSDrv tiskárnu jako tiskárnu XPSDrv. Provedete to tak, že přidáte Pipelineconfig. XML do seznamu souborů v následujícím klíči registru počítače, ve kterém je aplikace spuštěná:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\ *\<PseudoXPSPrinter>* \DependentFiles  
  
 *kde\<PseudoXPSPrinter >* je jakákoli tisková fronta. Počítač se pak musí restartovat.  
  
 Tento promaskování vám umožní předat `true` jako konečný <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> parametr, aniž by došlo k výjimce, ale vzhledem k tomu, že  *\<PseudoXPSPrinter >* není ve skutečnosti XPSDrv tiskárna, vytiskne se jenom uvolnění paměti.  
  
 **Poznámka:** V případě jednoduchosti výše uvedený příklad používá jako svůj test \*přítomnost rozšíření. XPS, že se jedná o soubor XPS. Soubory XPS ale nemusí mít toto rozšíření. [IsXPS. exe (Nástroj pro dodržování isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) je jedním ze způsobů, jak otestovat soubor pro dobu platnosti XPS.  
  
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
