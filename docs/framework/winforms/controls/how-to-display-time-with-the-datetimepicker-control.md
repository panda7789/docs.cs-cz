---
title: 'Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker'
description: Naučte se používat ovládací prvek model Windows Forms DateTimePicker k tomu, aby uživatelé mohli vybrat datum a čas a zobrazit toto datum a čas v zadaném formátu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time [Windows Forms], displaying in DateTimePicker control
- examples [Windows Forms], DateTimePicker control
- DateTimePicker control [Windows Forms], displaying time
ms.assetid: 0c1c8b40-1b50-4301-a90c-39516775ccb1
ms.openlocfilehash: ab584367a189d05e567bb57d386c6bf629201102
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325578"
---
# <a name="how-to-display-time-with-the-datetimepicker-control"></a>Postupy: Zobrazení času pomocí ovládacího prvku DateTimePicker
Pokud chcete, aby vaše aplikace uživatelům umožnila vybrat datum a čas a zobrazit toto datum a čas v zadaném formátu, použijte <xref:System.Windows.Forms.DateTimePicker> ovládací prvek. Následující postup ukazuje, jak použít <xref:System.Windows.Forms.DateTimePicker> ovládací prvek k zobrazení času.  
  
### <a name="to-display-the-time-with-the-datetimepicker-control"></a>Zobrazení času s ovládacím prvkem DateTimePicker  
  
1. Nastavte <xref:System.Windows.Forms.DateTimePicker.Format%2A> vlastnost na<xref:System.Windows.Forms.DateTimePickerFormat.Time>  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#2)]  
  
2. Nastavte <xref:System.Windows.Forms.DateTimePicker.ShowUpDown%2A> vlastnost pro na <xref:System.Windows.Forms.DateTimePicker> `true` .  
  
     [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#3)]  
  
## <a name="example"></a>Příklad  
 Následující ukázka kódu ukazuje, jak vytvořit <xref:System.Windows.Forms.DateTimePicker> , který umožňuje uživatelům zvolit jenom čas.  
  
 [!code-csharp[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.DateTimePickerTimeOnly#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DateTimePickerTimeOnly/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také

- [DateTimePicker – ovládací prvek](datetimepicker-control-windows-forms.md)
