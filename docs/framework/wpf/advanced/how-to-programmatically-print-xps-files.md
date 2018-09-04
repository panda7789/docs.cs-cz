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
ms.openlocfilehash: 25c0b34bd33bee626df14c8dbedce0b82e895b58
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43532813"
---
# <a name="how-to-programmatically-print-xps-files"></a>Postupy: Tisk souborů XPS z programu
Můžete použít jednu přetížení <xref:System.Printing.PrintQueue.AddJob%2A> metoda tisknout [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] soubory bez zahájení <xref:System.Windows.Controls.PrintDialog> nebo v zásadě, všechny [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] vůbec.  
  
 Můžete také vytisknout [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] soubory použijte všechny různé <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>. Další informace o tom [tisk dokumentu XPS](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90)).  
  
 Dalším způsobem, jak tisk [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] , je použít <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> nebo <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> metody <xref:System.Windows.Controls.PrintDialog> ovládacího prvku. Zobrazit [vyvolání dialogového okna Tisk](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Příklad  
 Pomocí parametru tři hlavní kroky <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metody jsou následující. Následující příklad uvádí podrobnosti.  
  
1.  Určete, pokud se XPSDrv tiskárnu. (Viz [přehled tisku s](printing-overview.md) Další informace o tom XPSDrv.)  
  
2.  Pokud se nejedná XPSDrv tiskárnu, nastavte vlákně na jedno vlákno.  
  
3.  Vytvoření instance tiskového serveru a objekt tiskové fronty.  
  
4.  Volat metodu s názvem projektu, souborů, které se mají vytisknout a <xref:System.Boolean> příznak označující, zda se XPSDrv tiskárnu.  
  
 Následující příklad ukazuje, jak batch tisk všechny [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] soubory v adresáři. I když aplikace vyzve uživatele k zadejte adresář, parametr tři <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metoda nevyžaduje, aby [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Může sloužit všechny cesty kódu ve které máte [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] název a cesta, kterou můžete předat do ní.  
  
 Parametr tři <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> přetížení <xref:System.Printing.PrintQueue.AddJob%2A> musí být spuštěný v jedné vlákně pokaždé, když <xref:System.Boolean> parametr je `false`, který musí být při použití jiných XPSDrv tiskárny. Nicméně výchozí stav objektu apartment pro [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] je více vláken. Toto výchozí nastavení musí vrátit zpět, protože příklad předpokládá bez XPSDrv tiskárny.  
  
 Existují dva způsoby, jak změnit výchozí nastavení. Jedním ze způsobů je jednoduše přidat <xref:System.STAThreadAttribute> (tedy "`[System.STAThreadAttribute()]`") přímo nad první řádek aplikace `Main` – metoda (obvykle "`static void Main(string[] args)`"). Ale mnohé aplikace vyžadují, aby `Main` metody mají stav vícevláknového objektu apartment, tedy druhá metoda: umístit volání <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> v samostatném vlákně, jehož stav objektu apartment je nastavený na <xref:System.Threading.ApartmentState.STA> s <xref:System.Threading.Thread.SetApartmentState%2A>. Následující příklad používá tento druhý postup.  
  
 Odpovídajícím způsobem, v příkladu spustí po vytvoření instance <xref:System.Threading.Thread> objektu a předají se jí **PrintXPS** metody, jako <xref:System.Threading.ThreadStart> parametr. ( **PrintXPS** dále v tomto příkladu je definována metoda.) Další vlákno je nastavena na objektu apartment jedno vlákno. Jediný zbývající kód `Main` metoda začíná nové vlákno.  
  
 Masa v příkladu se `static` **BatchXPSPrinter.PrintXPS** metody. Po vytvoření tiskového serveru a fronty, metoda výzvu k zadání adresáře, který obsahuje [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] soubory. Po ověření existence adresáře a přítomnost \*XPS soubory v něm, metoda přidá každý takový soubor tiskové fronty. Příklad předpokládá, že je tiskárna bez XPSDrv, tak jsme prochází `false` pro poslední parametr <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metody. Z tohoto důvodu se ověří metodu [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] kód v souboru dříve než se pokusí převést na jazyk popisu stránky tiskárny. Pokud se ověření nezdaří, je vyvolána výjimka. Příklad kódu se zachytit výjimku, informovat uživatele o tom a poté přejděte k další zpracování [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] souboru.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Pokud používáte XPSDrv tiskárny a potom poslední parametr lze nastavit na `true`. V takovém případě od [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] je jazyk stránky popis tiskárny, metoda odešle soubor do tiskárny bez ověřování nebo jeho převodu do jiného jazyka popis stránky. Pokud si nejste jisti v době návrhu, jestli aplikace budou používat XPSDrv tiskárny, můžete upravit aplikaci jeho čtení <xref:System.Printing.PrintQueue.IsXpsDevice%2A> vlastnost a větev, podle zjištěných informacích.  
  
 Protože zpočátku bude několik XPSDrv tiskárny k dispozici ihned po vydání [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] a Microsoft .NET Framework, může být vhodné skrýt bez XPSDrv tiskárny jako XPSDrv tiskárny. Uděláte to tak, přidejte do seznamu souborů v následujícím klíči registru počítače se systémem aplikace Pipelineconfig.xml:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter >* \DependentFiles  
  
 kde  *\<PseudoXPSPrinter >* je jakékoli tiskové fronty. Je pak nutné počítač restartovat.  
  
 Tato maskování vám umožní předat `true` jako konečný parametr <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> aniž by to způsobilo výjimku, ale od té doby  *\<PseudoXPSPrinter >* není ve skutečnosti XPSDrv tiskárna vytiskne pouze uvolňování paměti.  
  
 **Poznámka:** pro zjednodušení výše uvedený příklad používá přítomnost \*XPS rozšíření jako jeho test, který je soubor [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Ale [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] soubory nemusí mít toto rozšíření. [IsXPS.exe (isxps pro kontrolu shody nástroj)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100)) je jeden ze způsobů, jak soubor pro testování [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] platnosti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](https://www.microsoft.com/xps)  
 [Tisk dokumentu XPS](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90))  
 [Spravovaná a nespravovaná vlákna](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))  
 [isXPS.exe (isxps pro kontrolu shody nástroj)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100))  
 [Dokumenty v platformě WPF](documents-in-wpf.md)  
 [Přehled tisku](printing-overview.md)
