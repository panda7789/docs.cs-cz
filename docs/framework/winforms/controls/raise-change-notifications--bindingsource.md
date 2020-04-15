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
ms.openlocfilehash: 07248ec0b8ac4f2356d9c9915b6a904dfad30cb2
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388971"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged
Komponenta <xref:System.Windows.Forms.BindingSource> automaticky rozpozná změny ve zdroji dat, když typ obsažený <xref:System.ComponentModel.INotifyPropertyChanged> ve zdroji <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> dat implementuje rozhraní a vyvolá události při změně hodnoty vlastnosti. To je užitečné, protože <xref:System.Windows.Forms.BindingSource> ovládací prvky vázané na bude automaticky aktualizovat jako hodnoty zdroje dat změnit.  
  
> [!NOTE]
> Pokud váš zdroj <xref:System.ComponentModel.INotifyPropertyChanged> dat implementuje a provádíte asynchronní operace, neměli byste provádět změny zdroje dat ve vlákně na pozadí. Místo toho byste měli číst data ve vlákně na pozadí a sloučit data do seznamu ve vlákně uživatelského rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jednoduchou <xref:System.ComponentModel.INotifyPropertyChanged> implementaci rozhraní. Také ukazuje, <xref:System.Windows.Forms.BindingSource> jak automaticky předá změnu zdroje <xref:System.Windows.Forms.BindingSource> dat vázanému ovládacímu <xref:System.ComponentModel.INotifyPropertyChanged> prvku, když je vázán na seznam typu.  
  
 Pokud použijete `CallerMemberName` atribut, volání `NotifyPropertyChanged` metody není nutné zadat název vlastnosti jako argument řetězce. Další informace naleznete v [tématu Informace o volajícím (C#)](../../../csharp/language-reference/attributes/caller-information.md) nebo [Informace o volajícím (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System.Data, System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
