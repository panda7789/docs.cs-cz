---
title: 'Postupy: Zobrazení komponenty PrintDialog'
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 5315dc8b47c8ca846376ac6d1da5a0bf46fd6241
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543994"
---
# <a name="how-to-display-the-printdialog-component"></a>Postupy: Zobrazení komponenty PrintDialog
<xref:System.Windows.Forms.PrintDialog> Součástí je standardní Windows dialogového okna Tisk pole, která bude zkušenosti s mnoha uživatelů. Vzhledem k tomu, že uživatelé budou okamžitě vyhovuje, bylo by vhodné pro použití <xref:System.Windows.Forms.PrintDialog> komponenty.  
  
### <a name="to-display-the-printdialog-component"></a>K zobrazení součásti PrintDialog  
  
-   Volání <xref:System.Windows.Forms.Form.ShowDialog%2A> metodu z kódu vaší aplikace.  
  
     Jakmile součást se zobrazí, uživatelé se s ní pracovat, nastavení vlastnosti tiskové úlohy. Tyto jsou uložené v <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` třídu (a <xref:System.Drawing.Printing.PageSettings> třídy, když chce uživatel [PageSetupDialog – komponenta](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) prostřednictvím <xref:System.Windows.Forms.PrintDialog> součásti) spojené s danou tiskovou úlohu. Potom může provést volání vlastností sady k určení, jaké jsou specifikace tiskové úlohy.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Vytvoření tiskových úloh standardní Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [Ovládací prvek PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)
- [Komponenta PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
- [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
- [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)
