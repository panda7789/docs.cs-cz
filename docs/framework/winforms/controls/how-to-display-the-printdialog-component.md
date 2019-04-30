---
title: Postup zobrazení součásti PrintDialog
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 198ae75d407bd1837033a1cc186d84ff972fdc2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941567"
---
# <a name="how-to-display-the-printdialog-component"></a>Postup zobrazení součásti PrintDialog

<xref:System.Windows.Forms.PrintDialog> Součástí je standardní Windows dialogového okna Tisk pole, která bude zkušenosti s mnoha uživatelů. Vzhledem k tomu, že uživatelé budou okamžitě vyhovuje, bylo by vhodné pro použití <xref:System.Windows.Forms.PrintDialog> komponenty.

## <a name="to-display-the-printdialog-component"></a>K zobrazení součásti PrintDialog

- Volání <xref:System.Windows.Forms.Form.ShowDialog%2A> metodu z kódu vaší aplikace.

     Jakmile součást se zobrazí, uživatelé se s ní pracovat, nastavení vlastnosti tiskové úlohy. Tyto jsou uložené v <xref:System.Drawing.Printing.PrinterSettings> třídu (a <xref:System.Drawing.Printing.PageSettings> třídy, když chce uživatel [PageSetupDialog – komponenta](pagesetupdialog-component-windows-forms.md) prostřednictvím <xref:System.Windows.Forms.PrintDialog> součásti) spojené s danou tiskovou úlohu. Potom může provést volání vlastností sady k určení, jaké jsou specifikace tiskové úlohy.

## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření tiskových úloh standardní Windows Forms](../advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu](../advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [Ovládací prvek PrintPreviewDialog](printpreviewdialog-control-windows-forms.md)
- [Komponenta PrintDialog](printdialog-component-windows-forms.md)
- [Podpora tisku v modelu Windows Forms](../advanced/windows-forms-print-support.md)
- [Windows Forms – ovládací prvky](index.md)