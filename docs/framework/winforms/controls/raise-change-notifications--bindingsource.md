---
title: 'Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de75d4d3d8de34bc85ee47b6761724da93fc0ecc
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Postupy: Vytváření oznámení o změnách pomocí rozhraní BindingSource a INotifyPropertyChanged
<xref:System.Windows.Forms.BindingSource> Součást automaticky zjistí změny ve zdroji dat při typu obsažené v implementuje zdroje dat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a vyvolá <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události při změně hodnoty vlastnosti. To je užitečné, protože ovládací prvky vázané <xref:System.Windows.Forms.BindingSource> se pak automaticky aktualizuje jako změny dat zdrojové hodnoty.  
  
> [!NOTE]
>  Pokud vaše data zdroje implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a provádění asynchronní operace, neprovádějte změny pro zdroj dat na vlákna na pozadí. Místo toho doporučujeme číst data v vlákna na pozadí a slučování dat do seznamu ve vlákně UI.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jednoduchou implementaci <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Také ukazuje, jak <xref:System.Windows.Forms.BindingSource> automaticky předá Změna zdroje dat do hranice řídí, kdy se <xref:System.Windows.Forms.BindingSource> je vázána na seznam <xref:System.ComponentModel.INotifyPropertyChanged> typu.  
  
 Pokud použijete `CallerMemberName` atribut, volání `NotifyPropertyChanged` metoda není nutné zadat název vlastnosti jako argument řetězec. Další informace najdete v tématu [informace o subjektu volajícím](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [Komponenta BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
