---
title: 'Postupy: Ověření a sloučení PrintTickets'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- merging PrintTickets [WPF]
- PrintTicket [WPF], merging
- validation of PrintTickets [WPF]
- PrintTicket [WPF], validation
ms.assetid: 4fe2d501-d0b0-4fef-86af-6ffe6c162532
ms.openlocfilehash: 11160d7ec59914afbe501ba731c0c04a85ffc4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-validate-and-merge-printtickets"></a>Postupy: Ověření a sloučení PrintTickets
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Tiskových schématu](http://go.microsoft.com/fwlink/?LinkId=186397) zahrnuje flexibilní a rozšiřitelný <xref:System.Printing.PrintCapabilities> a <xref:System.Printing.PrintTicket> elementy. První rozepisuje možností zařízení pro tisk a druhá možnost určuje, jak má zařízení použít tyto možnosti s ohledem na konkrétní pořadí dokumenty, jednotlivý dokument nebo jednotlivých stránek.  
  
 Typické pořadí úloh pro aplikace, která podporuje tisk vypadat takto.  
  
1.  Určení možnosti tiskárny.  
  
2.  Konfigurace <xref:System.Printing.PrintTicket> využívá tyto možnosti.  
  
3.  Ověření <xref:System.Printing.PrintTicket>.  
  
 Tento článek ukazuje, jak to udělat.  
  
## <a name="example"></a>Příklad  
 V jednoduchém příkladu níže jsme zajímá pouze v tom, jestli tiskárnu může podporovat duplexní – oboustranný tisk. Hlavní kroky jsou následující.  
  
1.  Získání <xref:System.Printing.PrintCapabilities> objektu s <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metoda.  
  
2.  Test na přítomnost schopností, které chcete. V následujícím příkladu jsme testovat <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> vlastnost <xref:System.Printing.PrintCapabilities> objektu přítomnost možnosti tisku na obou stranách papíru s "stránka měnící" delší strana stylů. Vzhledem k tomu <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> je kolekce, použijeme `Contains` metodu <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    >  Tento krok není nezbytně nutné. <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Metodu použitou níže zkontroluje každé žádosti <xref:System.Printing.PrintTicket> s možnostmi tiskárny. Pokud požadovaná funkce není podporovaná tiskárny, ovladač tiskárny budou nahrazeny alternativní požadavku v <xref:System.Printing.PrintTicket> vrácený metodou.  
  
3.  Pokud je podpora duplexní, ukázkový kód vytvoří <xref:System.Printing.PrintTicket> , požádá o duplexní. Ale aplikace neurčuje nastavení k dispozici v každé možné tiskárny <xref:System.Printing.PrintTicket> elementu. Který by plýtvání programátory a program čas. Místo toho nastaví pouze požadavek duplexní kód a pak sloučí to <xref:System.Printing.PrintTicket> s existujícími, plně nakonfigurované a ověřit, <xref:System.Printing.PrintTicket>, v takovém případě výchozí uživatele <xref:System.Printing.PrintTicket>.  
  
4.  Podle toho, ukázka volá <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metoda sloučit nové, minimální, <xref:System.Printing.PrintTicket> výchozí uživatele <xref:System.Printing.PrintTicket>. Tento příkaz vrátí <xref:System.Printing.ValidationResult> , který obsahuje nové <xref:System.Printing.PrintTicket> jako jednu ze svých vlastností.  
  
5.  Ukázka pak testů, který nové <xref:System.Printing.PrintTicket> požadavky duplexní. Pokud ano, pak ukázce je nový výchozí tiskové lístek pro uživatele. Pokud krok 2 výše byly ponechány a tiskárny nepodporuje duplexní delší strana, pak by vznikla test `false`. (Viz poznámka výše).  
  
6.  Posledním krokem významné je Potvrdit změnu <xref:System.Printing.PrintQueue.UserPrintTicket%2A> vlastnost <xref:System.Printing.PrintQueue> s <xref:System.Printing.PrintQueue.Commit%2A> metoda.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Tak, aby v tomto příkladu můžete rychle otestovat, zbývající části je uveden níže. Vytvoření projektu a obor názvů a vložte fragmenty kódu v tomto článku do bloku oboru názvů.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Printing.PrintCapabilities>  
 <xref:System.Printing.PrintTicket>  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Tisk – schéma](http://go.microsoft.com/fwlink/?LinkId=186397)
