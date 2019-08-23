---
title: 'Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 7dc640f272226da650a63b1a3434822d21053b48
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968281"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged
Komponenta automaticky detekuje změny ve zdroji dat, když typ obsažený ve zdroji dat <xref:System.ComponentModel.INotifyPropertyChanged> implementuje rozhraní a vyvolá <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události při změně hodnoty vlastnosti. <xref:System.Windows.Forms.BindingSource> To je užitečné, protože ovládací prvky vázané <xref:System.Windows.Forms.BindingSource> na se budou automaticky aktualizovat podle změny hodnot zdrojů dat.  
  
> [!NOTE]
> Pokud váš zdroj dat implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a provádíte asynchronní operace, neměli byste provádět změny zdroje dat ve vlákně na pozadí. Místo toho byste měli číst data ve vlákně na pozadí a slučovat data do seznamu ve vlákně uživatelského rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jednoduchou implementaci <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Také ukazuje, jak <xref:System.Windows.Forms.BindingSource> automaticky předává zdroj dat do vázaného ovládacího prvku, <xref:System.Windows.Forms.BindingSource> když je svázán se seznamem <xref:System.ComponentModel.INotifyPropertyChanged> typu.  
  
 Použijete `CallerMemberName` -li atribut, volání `NotifyPropertyChanged` metody nemusejí zadávat název vlastnosti jako argument řetězce. Další informace naleznete v tématu [informace o volajícím (C#)](../../../csharp/programming-guide/concepts/caller-information.md) nebo [informace o volajícím (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Vyvolat oznámení o změnách pomocí metody BindingSource ResetItem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
