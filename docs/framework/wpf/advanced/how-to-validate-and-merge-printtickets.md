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
ms.openlocfilehash: bd7f399555b343a52ec6f36aa3b8c706747d8b06
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094524"
---
# <a name="how-to-validate-and-merge-printtickets"></a>Postupy: Ověření a sloučení PrintTickets
[Schéma tisku](/windows/win32/printdocs/printschema) v systému Microsoft Windows zahrnuje flexibilní a rozšiřitelné prvky <xref:System.Printing.PrintCapabilities> a <xref:System.Printing.PrintTicket>. Předchozí rozepisuje možnosti tiskového zařízení a druhého nastavení určují, jak by mělo zařízení používat tyto možnosti s ohledem na konkrétní posloupnost dokumentů, jednotlivé dokumenty nebo jednotlivé stránky.  
  
 Typická posloupnost úloh pro aplikaci, která podporuje tisk, by byla následující.  
  
1. Určete schopnosti tiskárny.  
  
2. Nakonfigurujte <xref:System.Printing.PrintTicket>, aby tyto možnosti používaly.  
  
3. Ověřte <xref:System.Printing.PrintTicket>.  
  
 Tento článek ukazuje, jak to provést.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu vás zajímá pouze to, jestli tiskárna podporuje oboustranný tisk – oboustranný tisk. Hlavní kroky jsou následující.  
  
1. Získá objekt <xref:System.Printing.PrintCapabilities> s metodou <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>.  
  
2. Otestujte přítomnost požadované schopnosti. V následujícím příkladu otestujeme vlastnost <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> objektu <xref:System.Printing.PrintCapabilities>, aby byla přítomna možnost tisku na obou stranách listu papíru se stránkou otáčení stránky podél pravé strany listu. Vzhledem k tomu, že <xref:System.Printing.PrintCapabilities.DuplexingCapability%2A> je kolekce, používáme metodu `Contains` <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
    > [!NOTE]
    > Tento krok není nezbytně nezbytný. Níže uvedená metoda <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> bude kontrolovat všechny žádosti v <xref:System.Printing.PrintTicket> na možnosti tiskárny. Pokud tiskárna nepodporuje požadovanou funkci, ovladač tiskárny nahradí alternativní požadavek v <xref:System.Printing.PrintTicket> vráceném metodou.  
  
3. Pokud tiskárna podporuje duplexní režim, vzorový kód vytvoří <xref:System.Printing.PrintTicket>, která žádá o oboustranný přenos. Aplikace ale neurčuje všechna možná nastavení tiskárny, která jsou k dispozici v prvku <xref:System.Printing.PrintTicket>. To by bylo wasteful programátora i času programu. Místo toho kód nastaví pouze duplexní požadavek a potom tento <xref:System.Printing.PrintTicket> sloučí s existujícím, plně nakonfigurovaným a ověřeným <xref:System.Printing.PrintTicket>, v tomto případě výchozí <xref:System.Printing.PrintTicket>uživatele.  
  
4. Proto ukázka zavolá metodu <xref:System.Printing.PrintQueue.MergeAndValidatePrintTicket%2A> pro sloučení nového, minimálního <xref:System.Printing.PrintTicket> s výchozím <xref:System.Printing.PrintTicket>uživatele. Vrátí <xref:System.Printing.ValidationResult>, který obsahuje nový <xref:System.Printing.PrintTicket> jako jednu z jeho vlastností.  
  
5. Ukázka potom testuje, zda nový <xref:System.Printing.PrintTicket> žádá o oboustranný přenos. V takovém případě ukázka vytvoří nový výchozí tiskový lístek pro uživatele. Pokud byl krok 2 výše popsaný a tiskárna nepodporovala oboustranný přenos, pak test by byl výsledkem `false`. (Viz poznámka výše.)  
  
6. Posledním významným krokem je potvrzení změny vlastnosti <xref:System.Printing.PrintQueue.UserPrintTicket%2A> <xref:System.Printing.PrintQueue> pomocí metody <xref:System.Printing.PrintQueue.Commit%2A>.  
  
 [!code-csharp[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#usingmergeandvalidate)]
 [!code-vb[PrintTicketManagment#UsingMergeAndValidate](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#usingmergeandvalidate)]  
  
 Aby bylo možné rychle otestovat tento příklad, zbývající část je uvedena níže. Vytvořte projekt a obor názvů a vložte oba fragmenty kódu v tomto článku do bloku oboru názvů.  
  
 [!code-csharp[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintTicketManagment/CSharp/printticket.cs#uiformergeandvalidateptutility)]
 [!code-vb[PrintTicketManagment#UIForMergeAndValidatePTUtility](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintTicketManagment/visualbasic/printticket.vb#uiformergeandvalidateptutility)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
- [Tisk schématu](/windows/win32/printdocs/printschema)
