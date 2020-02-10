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
ms.openlocfilehash: aae41931f012f6d34fc057fdd6ee9fc9baab6e7b
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094537"
---
# <a name="how-to-enumerate-a-subset-of-print-queues"></a>Postupy: Vyčíslení dílčí sady tiskové fronty
Běžnou situací, kterou čelí odborníci na informační technologie (IT), která spravuje sadu tiskáren v rámci podnikové sítě, je vygenerovat seznam tiskáren, které mají určité charakteristiky. Tato funkce je k dispozici pomocí metody <xref:System.Printing.PrintServer.GetPrintQueues%2A> objektu <xref:System.Printing.PrintServer> a výčtu <xref:System.Printing.EnumeratedPrintQueueTypes>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu kód začíná vytvořením pole příznaků, které určují charakteristiky tiskových front, které chceme zobrazit. V tomto příkladu hledáme tiskové fronty, které jsou nainstalované místně na tiskovém serveru a jsou sdílené. Výčet <xref:System.Printing.EnumeratedPrintQueueTypes> poskytuje mnoho dalších možností.  
  
 Kód poté vytvoří objekt <xref:System.Printing.LocalPrintServer>, třídu odvozenou z <xref:System.Printing.PrintServer>. Místní tiskový server je počítač, na kterém je aplikace spuštěná.  
  
 Posledním krokem je předat pole do metody <xref:System.Printing.PrintServer.GetPrintQueues%2A>.  
  
 Nakonec se výsledky zobrazí uživateli.  
  
 [!code-cpp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/cpp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CPP/Program.cpp#listsubsetofprintqueues)]
 [!code-csharp[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/csharp/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/CSharp/Program.cs#listsubsetofprintqueues)]
 [!code-vb[EnumerateSubsetOfPrintQueues#ListSubsetOfPrintQueues](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EnumerateSubsetOfPrintQueues/visualbasic/program.vb#listsubsetofprintqueues)]  
  
 Tento příklad můžete rozšířit tím, že zadáte `foreach` smyčkou, kterou jednotlivé tiskové fronty provedou k dalšímu prověřování. Můžete například umístit tiskárny, které nepodporují oboustranný tisk, voláním každé <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A> metody tiskové fronty a otestovat vrácenou hodnotu pro přítomnost duplexního přenosu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Printing.PrintServer.GetPrintQueues%2A>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.EnumeratedPrintQueueTypes>
- <xref:System.Printing.PrintQueue>
- <xref:System.Printing.PrintQueue.GetPrintCapabilities%2A>
- [Dokumenty v platformě WPF](documents-in-wpf.md)
- [Přehled tisku](printing-overview.md)
- [Zapisovač dokumentů Microsoft XPS](/windows/win32/printdocs/microsoft-xps-document-writer)
