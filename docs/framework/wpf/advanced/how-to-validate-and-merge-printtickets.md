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
ms.openlocfilehash: 9e5242c07179501e6b39840a36f8dd6364d65b84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918349"
---
# <a name="how-to-validate-and-merge-printtickets"></a>Postupy: Ověření a sloučení PrintTickets
Schéma tisku zahrnuje flexibilní a rozšiřitelnost <xref:System.Printing.PrintCapabilities> a <xref:System.Printing.PrintTicket> prvky. [](https://go.microsoft.com/fwlink/?LinkId=186397) [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] Předchozí rozepisuje možnosti tiskového zařízení a druhého nastavení určují, jak by mělo zařízení používat tyto možnosti s ohledem na konkrétní posloupnost dokumentů, jednotlivé dokumenty nebo jednotlivé stránky.  
  
 Typická posloupnost úloh pro aplikaci, která podporuje tisk, by byla následující.  
  
1. Určete schopnosti tiskárny.  
  
2. Nakonfigurujte, <xref:System.Printing.PrintTicket> aby se tyto možnosti používaly.  
  
3. <xref:System.Printing.PrintTicket>Ověřte.  
  
 Tento článek ukazuje, jak to provést.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu vás zajímá pouze to, jestli tiskárna podporuje oboustranný tisk – oboustranný tisk. Hlavní kroky jsou následující.  
  
1. <xref:System.Printing.PrintCapabilities> Získat objekt<xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> s metodou.  
  
2. Otestujte přítomnost požadované schopnosti. V následujícím příkladu testujeme <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> vlastnost <xref:System.Printing.PrintCapabilities> objektu pro přítomnost možnosti tisku na obou stranách listu papíru s "otáčením stránky" podél pravé strany listu. Vzhledem <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> k tomu, že `Contains` je kolekce, používáme <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>metodu.  
  
    > [!NOTE]
    > Tento krok není nezbytně nezbytný. <xref:System.Printing.PrintTicket> Níže uvedená <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metoda zkontroluje všechny požadavky v s funkcemi tiskárny. Pokud není požadovaná schopnost tiskárny podporována, ovladač tiskárny nahradí alternativní požadavek <xref:System.Printing.PrintTicket> vrácený metodou.  
  
3. Pokud tiskárna podporuje duplexní režim, vzorový kód vytvoří a <xref:System.Printing.PrintTicket> požádá o oboustranný přenos. Aplikace ale neurčuje všechna možná nastavení tiskárny, která jsou k dispozici v <xref:System.Printing.PrintTicket> elementu. To by bylo wasteful programátora i času programu. Místo toho kód nastaví pouze duplexní požadavek a pak ho sloučí <xref:System.Printing.PrintTicket> s existujícím, plně nakonfigurovaným a <xref:System.Printing.PrintTicket>ověřeným, v tomto případě jako výchozí nastavení <xref:System.Printing.PrintTicket>uživatele.  
  
4. Proto ukázka volá <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> metodu pro sloučení nového, <xref:System.Printing.PrintTicket> minimálního s výchozím nastavením <xref:System.Printing.PrintTicket>uživatele. Vrátí <xref:System.Printing.ValidationResult> , který obsahuje nový <xref:System.Printing.PrintTicket> jako jednu z jeho vlastností.  
  
5. Ukázka potom testuje, zda nové <xref:System.Printing.PrintTicket> požadavky přibyly duplexní. V takovém případě ukázka vytvoří nový výchozí tiskový lístek pro uživatele. Pokud byl krok 2 výše popsaný a tiskárna nepodporovala oboustranně, pak test by byl výsledkem `false`. (Viz poznámka výše.)  
  
6. Posledním významným krokem je potvrzení změny <xref:System.Printing.PrintQueue.UserPrintTicket%2A> vlastnosti <xref:System.Printing.PrintQueue> <xref:System.Printing.PrintQueue.Commit%2A> metody s metodou.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Aby bylo možné rychle otestovat tento příklad, zbývající část je uvedena níže. Vytvořte projekt a obor názvů a vložte oba fragmenty kódu v tomto článku do bloku oboru názvů.  
  
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
