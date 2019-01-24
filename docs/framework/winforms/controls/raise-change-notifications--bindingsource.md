---
title: 'Postupy: Vytváření oznámení o změnách pomocí BindingSource a INotifyPropertyChanged – rozhraní'
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
ms.openlocfilehash: cf6f39154b7b896a835bda7f946134fbff8dbe17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543955"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Postupy: Vytváření oznámení o změnách pomocí BindingSource a INotifyPropertyChanged – rozhraní
<xref:System.Windows.Forms.BindingSource> Komponenty automaticky zjistí změny ve zdroji dat. Pokud je typ obsažený v implementuje zdroj dat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a vyvolá <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události při změně hodnoty vlastnosti. To je užitečné, protože ovládací prvky vázané <xref:System.Windows.Forms.BindingSource> pak automaticky aktualizuje jako změn dat zdrojové hodnoty.  
  
> [!NOTE]
>  Pokud zdroj dat implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a provádění asynchronní operace, by neměla provést změny pro zdroj dat na vlákně na pozadí. By měl místo toho načtěte data ve vlákně na pozadí a slučování dat do seznamu na vlákně UI.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jednoduchý provádění <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Také ukazuje, jak <xref:System.Windows.Forms.BindingSource> automaticky předá Změna zdroje dat pro vazbu ovládacího prvku, když <xref:System.Windows.Forms.BindingSource> je vázán na seznam <xref:System.ComponentModel.INotifyPropertyChanged> typu.  
  
 Pokud používáte `CallerMemberName` atribut, volání `NotifyPropertyChanged` metoda není nutné zadat název vlastnosti jako argument řetězec. Další informace najdete v tématu [informace o subjektu volajícím](https://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu. Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb129228(v=vs.100)).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ComponentModel.INotifyPropertyChanged>
- [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [Postupy: Vytváření oznámení o změnách pomocí metody BindingSource Resetitem](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
