---
title: 'Postupy: Vyčíslení dílčí sady tiskové fronty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- enumerating [WPF], subset of print queues
- print queues [WPF], enumerating subset of
ms.assetid: cc4a1b5b-d46f-4c5e-bc26-22c226e4bee0
ms.openlocfilehash: 3e616b3b61b4b1b561d5bdb7e51525f391901a22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Postupy: Vyčíslení dílčí sady tiskové fronty
Běžné situace Odborníci v oblasti technologií (IT) informace o správě společnosti sadu tiskárny, jimž je vygenerovat seznam tiskárny, které mají určité charakteristické vlastnosti. Tato funkce poskytuje <xref:System.Printing.PrintServer.GetPrintQueues%2A> metodu <xref:System.Printing.PrintServer> objektu a <xref:System.Printing.EnumeratedPrintQueueTypes> výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu začíná vytvořením pole příznaky, které určují vlastnosti tiskové fronty, které chcete zobrazit seznam. V tomto příkladu jsme hledáte tiskové fronty, které jsou nainstalovány místně na tiskovém serveru a sdílejí. <xref:System.Printing.EnumeratedPrintQueueTypes> Výčet obsahuje mnoho dalších možností.  
  
 Kód vytvoří <xref:System.Printing.LocalPrintServer> objektu třída odvozená z <xref:System.Printing.PrintServer>. Místní tiskový server je počítač, na kterém je aplikace spuštěna.  
  
 Posledním krokem významné je předat pole do <xref:System.Printing.PrintServer.GetPrintQueues%2A> metoda.  
  
 Nakonec výsledky se zobrazí uživateli.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Tento příklad šlo rozšířit tak, že `foreach` smyčky, že kroky prostřednictvím každou tiskovou frontu provádět další blokování. Například je může vyloučit tiskárny, které nepodporují oboustranný tisk tak, že volání smyčky každou tiskovou frontu <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metoda a testování vrácená hodnota přítomnost duplexní.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Printing.PrintServer.GetPrintQueues%2A>  
 <xref:System.Printing.PrintServer>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.EnumeratedPrintQueueTypes>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>  
 [Dokumenty v platformě WPF](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [Přehled tisku](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [Zapisovací modul dokumentů Microsoft XPS](http://go.microsoft.com/fwlink/?LinkId=147319)
