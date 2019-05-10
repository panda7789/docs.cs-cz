---
title: 'Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: f1c1a0abaeddadb44b40d56eb2f8a28e4b58f4f5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651774"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a>Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker
Pokud chcete, aby vaše aplikace umožňuje uživatelům vybrat datum a čas a k zobrazení tohoto data a času v zadaném formátu, použijte <xref:System.Windows.Forms.DateTimePicker> ovládacího prvku. Následující postup ukazuje, jak používat <xref:System.Windows.Forms.DateTimePicker> ovládací prvek pro zobrazení času.  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a>K zobrazení času pomocí ovládacího prvku DateTimePicker  
  
1. Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost <xref:System.Windows.Forms.DateTimePickerFormat.Time>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. Nastavte <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> vlastnost <xref:System.Windows.Forms.DateTimePicker> k `true`.  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Windows.Forms.DateTimePicker> , která umožňuje uživatelům zvolit pouze čas.  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvek DateTimePicker](datetimepicker-control-windows-forms.md)
