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
ms.openlocfilehash: 7cdd0ebeb03d078a952dd9ffe4d2ed7590417054
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359481"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Postupy: Vyčíslení dílčí sady tiskové fronty
Je běžné situace spojenou s rozšiřováním Odborníci v oblasti technologií (IT) informace o správě pořádaného microsoftem sadu tiskárny pro vygenerování seznamu tiskáren, které mají určité charakteristické vlastnosti. Tato funkce je poskytována <xref:System.Printing.PrintServer.GetPrintQueues%2A> metodu <xref:System.Printing.PrintServer> objektu a <xref:System.Printing.EnumeratedPrintQueueTypes> výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kódu začíná tím, že vytvoříte pole příznaky určující vlastnosti tiskové fronty, které chceme seznamu. V tomto příkladu hledáme tiskové fronty, které jsou nainstalovány místně na tiskovém serveru a sdílejí. <xref:System.Printing.EnumeratedPrintQueueTypes> Výčet poskytuje mnoho dalších možností.  
  
 Kód poté vytvoří <xref:System.Printing.LocalPrintServer> objektu, třída odvozená z <xref:System.Printing.PrintServer>. Místní tiskový server je počítač, na kterém je aplikace spuštěna.  
  
 Poslední významný krok je pole, které chcete předat <xref:System.Printing.PrintServer.GetPrintQueues%2A> metody.  
  
 A konečně výsledky se zobrazí uživateli.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 V tomto příkladu může rozšířit tak, že `foreach` smyčku, která vás provede každou tiskovou frontu, proveďte další blokování. Například jste mohli vyfiltroval tiskárny, které nepodporují oboustranný tisk tím, že volání smyčky každou tiskovou frontu <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metoda a testování vrácené hodnoty přítomnost duplexní.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
- [Zapisovací modul dokumentů Microsoft XPS](https://go.microsoft.com/fwlink/?LinkId=147319)
