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
ms.openlocfilehash: be8b299c99515394bc676cfd7a715cb82ac4d58c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051104"
---
# <a name="how-to-validate-and-merge-printtickets"></a>Postupy: Ověření a sloučení PrintTickets
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [Tisk schématu](https://go.microsoft.com/fwlink/?LinkId=186397) zahrnuje flexibilní a rozšiřitelné <xref:System.Printing.PrintCapabilities> a <xref:System.Printing.PrintTicket> elementy. Předchozí najdete výčet možností zařízení pro tisk a druhá možnost určuje, jak zařízení používali tyto možnosti s ohledem na konkrétní pořadí dokumentů, jednotlivý dokument nebo jednotlivých stránek.  
  
 Typická posloupnost úloh pro aplikace, která podporuje tisk by měl vypadat takto.  
  
1. Určení možnosti tiskárny.  
  
2. Konfigurace <xref:System.Printing.PrintTicket> používání těchto možností.  
  
3. Ověření <xref:System.Printing.PrintTicket>.  
  
 Tento článek ukazuje, jak to provést.  
  
## <a name="example"></a>Příklad  
 V následujícím jednoduchém příkladu nás zajímají pouze určuje, zda tiskárnu může podporovat duplexní – oboustranný tisk. Hlavní kroky jsou následující.  
  
1. Získat <xref:System.Printing.PrintCapabilities> objektu <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metody.  
  
2. Testovat přítomnost schopností, který chcete. V následujícím příkladu testujeme <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> vlastnost <xref:System.Printing.PrintCapabilities> objektu přítomnost možnosti tisku na obou stranách list papíru s měnící"stránky" po dlouhé straně stylů. Protože <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> je kolekce, můžeme použít `Contains` metoda <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    >  Tento krok není nezbytně nutné. <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> Metoda používá pod kontrola za každý požadavek <xref:System.Printing.PrintTicket> s možnostmi tiskárny. Pokud požadované funkce nepodporuje tiskárny, ovladač tiskárny nahradí alternativní žádosti v <xref:System.Printing.PrintTicket> vrácený metodou.  
  
3. Pokud je podpora duplexní, ukázkový kód vytvoří <xref:System.Printing.PrintTicket> , která požádá o duplexní. Aplikace, nemůžou ale zadat nastavení k dispozici v každé možné tiskárny <xref:System.Printing.PrintTicket> elementu. Bylo by plýtváním programátorů i čas programu. Místo toho kód nastaví pouze duplexní požadavek a pak sloučí to <xref:System.Printing.PrintTicket> s existujícím, plně nakonfigurované a ověřit, <xref:System.Printing.PrintTicket>, v tomto případě výchozí uživatele <xref:System.Printing.PrintTicket>.  
  
4. Odpovídajícím způsobem, ukázka zavolá <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metoda sloučit nové, minimal, <xref:System.Printing.PrintTicket> s výchozí uživatele <xref:System.Printing.PrintTicket>. Tím se vrátí <xref:System.Printing.ValidationResult> , který obsahuje novou <xref:System.Printing.PrintTicket> jako jedna z jeho vlastností.  
  
5. Ukázka pak testy, které nový <xref:System.Printing.PrintTicket> požadavků duplexní. Pokud ano, pak vzorku umožňuje nový lístek výchozí tisku pro daného uživatele. Bylo vynecháno kroku 2 výše a tiskárny nepodporuje duplexní po dlouhé straně a pak test by vznikla `false`. (Viz poznámka výše.)  
  
6. Je poslední významný krok k potvrzení změn do <xref:System.Printing.PrintQueue.UserPrintTicket%2A> vlastnost <xref:System.Printing.PrintQueue> s <xref:System.Printing.PrintQueue.Commit%2A> metody.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Takže můžete rychle otestovat v tomto příkladu, zbytek je uveden níže. Vytvoření projektu a obor názvů a pak vložte fragmenty kódu v tomto článku do bloku oboru názvů.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
- [Tisk schématu](https://go.microsoft.com/fwlink/?LinkId=186397)
