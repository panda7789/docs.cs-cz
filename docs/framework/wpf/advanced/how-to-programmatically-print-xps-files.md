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
ms.openlocfilehash: bb11ece91c1dc8ac27b67e4175c24e480da15812
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547582"
---
# <a name="how-to-programmatically-print-xps-files"></a>Postupy: Tisk souborů XPS z programu
Můžete použít jeden přetížení <xref:System.Printing.PrintQueue.AddJob%2A> metoda tisknout [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] soubory bez nutnosti otevírání <xref:System.Windows.Controls.PrintDialog> nebo, pokud v zásadě žádné [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] vůbec.  
  
 Můžete také vytisknout [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] soubory pomocí mnoho <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> a <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>. Další informace o tom [tisk dokumentu XPS](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90)).  
  
 Dalším způsobem, jak tisk [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] , je použít <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> nebo <xref:System.Windows.Controls.PrintDialog.PrintVisual%2A> metody <xref:System.Windows.Controls.PrintDialog> ovládacího prvku. V tématu [vyvolat dialogové okno tisku](how-to-invoke-a-print-dialog.md).  
  
## <a name="example"></a>Příklad  
 Pomocí parametru tři hlavní kroky <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metody jsou následující. Následující příklad uvádí podrobnosti.  
  
1.  Určí, pokud se XPSDrv tiskárnu. (Viz [přehled tisku](printing-overview.md) Další informace o XPSDrv.)  
  
2.  Pokud se nejedná XPSDrv tiskárnu, nastavte na jedno vlákno vláken typu apartment.  
  
3.  Vytvoří instanci objektu tiskové fronty a tiskový server.  
  
4.  Volání metody, zadání názvu úlohy, soubor pro tisk a <xref:System.Boolean> příznak označující, zda se XPSDrv tiskárnu.  
  
 Následující příklad ukazuje, jak dávky tiskových všechny [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] soubory v adresáři. I když aplikace vyzve uživatele k určení adresáře, parametr tři <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metoda nevyžaduje [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Může sloužit v jakékoli cestě kódu ve které máte [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] název a cesta, který můžete předat do ní.  
  
 Parametr tři <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> přetížení z <xref:System.Printing.PrintQueue.AddJob%2A> musí běžet v apartment s jedním vláknem vždy, když <xref:System.Boolean> parametr `false`, které musí být při použití jiných XPSDrv tiskárny. Nicméně výchozí stav objektu apartment pro [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] je více vláken. Toto výchozí nastavení musí vrátit zpět, protože příklad předpokládá bez XPSDrv tiskárny.  
  
 Existují dva způsoby, jak změnit výchozí nastavení. Jedním ze způsobů je jednoduše přidat <xref:System.STAThreadAttribute> (tedy "`[System.STAThreadAttribute()]`") nad první řádek aplikace `Main` – metoda (obvykle "`static void Main(string[] args)`"). Nicméně řada aplikací vyžaduje, `Main` metoda mají stav Vícevláknová apartment, takže není druhé metody: put volání <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> v samostatné vlákno, jejichž stav objektu apartment je nastavený na <xref:System.Threading.ApartmentState.STA> s <xref:System.Threading.Thread.SetApartmentState%2A>. Následující příklad používá tento druhý postup.  
  
 Podle toho v příkladu začne po vytvoření instance <xref:System.Threading.Thread> objekt a předání **PrintXPS** jako metodu <xref:System.Threading.ThreadStart> parametr. ( **PrintXPS** později v příkladu je definován metoda.) Další vlákno je nastavena na jedno vlákno apartment. Jenom zbývající kódu `Main` metoda spustí nové vlákno.  
  
 Maso v příkladu je v `static` **BatchXPSPrinter.PrintXPS** metoda. Po vytvoření tiskového serveru a fronty, metoda vyzve uživatele k adresáři obsahující [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] soubory. Po ověření existence adresáře a přítomnost \*XPS soubory v něm, metoda přidá každé takové soubor tiskové fronty. Příklad předpokládá, že tiskárny se jiný XPSDrv, takže jsme předávání `false` na poslední parametr <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> metoda. Z tohoto důvodu se metoda ověření [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] kód v souboru před pokusem o ho převést na jazyk popis stránky tiskárny. Pokud se ověření nezdaří, je vyvolána výjimka. Příklad kódu se zachycení výjimky, upozornit uživatele o tom a potom přejděte k další zpracování [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] souboru.  
  
 [!code-csharp[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BatchPrintXPSFiles/CSharp/Program.cs#batchprintxpsfiles)]
 [!code-vb[BatchPrintXPSFiles#BatchPrintXPSFiles](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BatchPrintXPSFiles/visualbasic/program.vb#batchprintxpsfiles)]  
  
 Pokud používáte XPSDrv tiskárny, pak můžete nastavit konečný parametr `true`. V takovém případě od [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] je jazyk popis stránky tiskárny, metoda odešle soubor do tiskárny bez její ověřování nebo jeho převodem na jiný jazyk popis stránky. Pokud si nejste jisti v době návrhu jestli aplikace bude používat XPSDrv tiskárny, můžete upravit aplikaci jej číst <xref:System.Printing.PrintQueue.IsXpsDevice%2A> vlastnost a větve podle co najde.  
  
 Vzhledem k tomu, že původně bude několik XPSDrv tiskárny k dispozici ihned po vydání [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)] a rozhraní Microsoft .NET Framework, musíte ke skrytí bez XPSDrv tiskárny jako XPSDrv tiskárny. Uděláte to tak, přidejte do seznamu souborů v následujícím klíči registru počítače se systémem aplikace Pipelineconfig.xml:  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3\\*\<PseudoXPSPrinter >* \DependentFiles  
  
 kde  *\<PseudoXPSPrinter >* je všechny tiskové fronty. Je pak nutné počítač restartovat.  
  
 Tato maskování vám umožní předat `true` jako konečný parametr z <xref:System.Printing.PrintQueue.AddJob%28System.String%2CSystem.String%2CSystem.Boolean%29> aniž by to způsobilo výjimku, ale protože  *\<PseudoXPSPrinter >* ve skutečnosti není tiskárny XPSDrv vytisknou pouze uvolňování paměti.  
  
 **Poznámka:** pro jednoduchost, v předchozím příkladu používá přítomnost \*rozšíření XPS jako jeho test, který je soubor [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)]. Ale [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] souborů nemusíte mít toto rozšíření. [IsXPS.exe (kontrolu shody nástroj)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100)) je jeden ze způsobů, jak soubor pro testování [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] platnosti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.AddJob%2A>  
 <xref:System.Threading.ApartmentState>  
 <xref:System.STAThreadAttribute>  
 [XPS](http://www.microsoft.com/xps)  
 [Tisk dokumentu XPS](https://msdn.microsoft.com/library/849555c8-0c4e-48c0-86bc-a5494c69b36c(v=vs.90))  
 [Spravovaná a nespravovaná vlákna](https://msdn.microsoft.com/library/db425c20-4b2f-4433-bf96-76071c7881e5(v=vs.100))  
 [isXPS.exe (kontrolu shody nástroj)](https://msdn.microsoft.com/library/bfbb433f-7ab6-417a-90f0-71443d76bcb3(v=vs.100))  
 [Dokumenty v platformě WPF](documents-in-wpf.md)  
 [Přehled tisku](printing-overview.md)
