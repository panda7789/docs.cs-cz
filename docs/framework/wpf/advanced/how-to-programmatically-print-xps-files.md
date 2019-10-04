---
title: 'Postupy: Tisk souborů XPS z programu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing XPS files programmatically [WPF]
- XPS files [WPF], printing programmatically
ms.assetid: 0b1c0a3f-b19e-43d6-bcc9-eb3ec4e555ad
ms.openlocfilehash: d44f372fe5ef9633e91d8e46cca9e9a0967b9615
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834578"
---
# <a name="how-to-programmatically-print-xps-files"></a>Postupy: Tisk souborů XPS z programu

K tisku souborů XPS (XML Paper Specification) můžete použít jedno přetížení metody <xref:System.Printing.PrintQueue.AddJob%2A>, aniž byste museli otevírat <xref:System.Windows.Controls.PrintDialog> nebo v zásadě všechny [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].

Soubory XPS můžete také tisknout pomocí mnoha metod <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A?displayProperty=nameWithType> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A?displayProperty=nameWithType>. Další informace najdete v tématu [Tisk dokumentu XPS](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771525(v=vs.90)).

Dalším způsobem tisku XPS je použití metod @no__t 0 nebo <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A?displayProperty=nameWithType>. Viz [vyvolání dialogového okna pro tisk](how-to-invoke-a-print-dialog.md).

## <a name="example"></a>Příklad

Hlavní kroky pro použití @no__t metodou 0 se třemi parametry jsou následující. V následujícím příkladu jsou uvedeny podrobnosti.

1. Zjistěte, jestli je tiskárna XPSDrv tiskárnou. Další informace o XPSDrv najdete v tématu [Přehled tisku](printing-overview.md) .

2. Pokud tiskárna není XPSDrv tiskárna, nastavte objekt Apartment vlákna na jedno vlákno.

3. Vytvoření instance tiskového serveru a objektu tiskové fronty.

4. Zavolejte metodu, určete název úlohy, soubor, který se má vytisknout, a příznak <xref:System.Boolean> označující, jestli je tiskárna XPSDrv tiskárna.

Následující příklad ukazuje, jak Batch vytisknout všechny soubory XPS v adresáři. I když aplikace vyzve uživatele k zadání adresáře, metoda <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> pro tři parametry nevyžaduje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Dá se použít v jakékoli cestě kódu, kde máte název a cestu souboru XPS, které můžete předat.

@No__t-1 @no__t přetížení-1 musí běžet v jednom vlákně Apartment, pokud je parametr <xref:System.Boolean> `false`, který se musí nacházet v případě, že se používá jiná než XPSDrv tiskárna. Výchozí stav objektu apartment pro rozhraní .NET je však více vláken. Tato výchozí hodnota musí být obrácená, protože příklad předpokládá, že tiskárna není XPSDrv.

Existují dva způsoby, jak změnit výchozí nastavení. Jedním ze způsobů je jednoduše přidat <xref:System.STAThreadAttribute> (to znamená "`[System.STAThreadAttribute()]`") těsně nad první řádek metody `Main` aplikace (obvykle "`static void Main(string[] args)`"). Mnoho aplikací však vyžaduje, aby metoda `Main` měla vícevláknový stav typu apartment, takže existuje druhá metoda: volání <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> v samostatném vlákně, jehož stav objektu Apartment je nastaven na hodnotu <xref:System.Threading.ApartmentState.STA> s <xref:System.Threading.Thread.SetApartmentState%2A>. Následující příklad používá tuto druhou techniku.

Proto příklad začíná vytvořením instance objektu @no__t 0 a předáním metody **PrintXPS** jako parametru <xref:System.Threading.ThreadStart>. (Metoda **PrintXPS** je definována později v příkladu.) V dalším vlákně je vlákno nastaveno na jeden objekt Apartment. Jediný zbývající kód metody `Main` spustí nové vlákno.

Maso v příkladu je v metodě `static`**BatchXPSPrinter. PrintXPS** . Po vytvoření tiskového serveru a fronty se metoda vyzve uživatele k zadání adresáře, který obsahuje soubory XPS. Po ověření existence adresáře a přítomnosti souborů @no__t -0. XPS v ní metoda přidá každý takový soubor do tiskové fronty. V příkladu se předpokládá, že tiskárna není XPSDrv, takže předáváme `false` k poslednímu parametru metody <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>. Z tohoto důvodu metoda ověří kód XPS v souboru předtím, než se pokusí o jeho převod na jazyk popisu stránky tiskárny. Pokud se ověření nepovede, vyvolá se výjimka. Ukázkový kód zachytí výjimku, upozorní uživatele na ni a pak přejde k procesu dalšího souboru XPS.

[!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
[!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]

Pokud používáte XPSDrv tiskárnu, můžete nastavit konečný parametr tak, aby `true`. V takovém případě, vzhledem k tomu, že XPS je jazykový popis stránky tiskárny, metoda pošle soubor do tiskárny bez ověření nebo převedení na jiný jazyk popisu stránky. Pokud si nejste jistí v době návrhu, jestli aplikace bude používat XPSDrv tiskárnu, můžete aplikaci upravit tak, aby si přečetla vlastnost-0 @no__t a větev podle toho, co najde.

Vzhledem k tomu, že bude zpočátku k dispozici málo XPSDrv tiskáren po vydání [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] a Microsoft .NET Framework, bude pravděpodobně nutné vymezit XPSDrv tiskárnu jako tiskárnu XPSDrv. Provedete to tak, že přidáte Pipelineconfig. XML do seznamu souborů v následujícím klíči registru počítače, ve kterém je aplikace spuštěná:

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3 @ no__t-0 *\<PseudoXPSPrinter >* \DependentFiles

kde *\<PseudoXPSPrinter >* je jakákoli tisková fronta. Počítač se pak musí restartovat.

Tento promaskování vám umožní předat `true` jako konečný parametr <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29>, aniž by došlo k výjimce, ale vzhledem k tomu, že *> \<PseudoXPSPrinter* není ve skutečnosti XPSDrv tiskárna, vytiskne se jenom uvolnění paměti.

> [!NOTE]
> Pro zjednodušení výše uvedený příklad používá přítomnost rozšíření @no__t -0. XPS jako svůj test, že soubor je XPS. Soubory XPS ale nemusí mít toto rozšíření. [IsXPS. exe (Nástroj pro dodržování isXPS)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aa348104(v=vs.100)) je jedním ze způsobů, jak otestovat soubor pro dobu platnosti XPS.

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
