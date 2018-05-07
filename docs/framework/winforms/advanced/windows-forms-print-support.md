---
title: Podpora tisku ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 4ea04d0b6bb8ffa7182d5166ebd66b809adeed34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="windows-forms-print-support"></a>Podpora tisku ve Windows Forms
Tisk ve Windows Forms se primárně skládá z pomocí [PrintDocument – komponenta](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) komponenty, aby uživatelům tisknout a [printpreviewdialog – ovládací prvek](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) řízení, [PrintDialog Součást](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) a [PageSetupDialog – komponenta](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) součásti, které poskytují obeznámeni grafické rozhraní uživatelům zvykli na operačním systému Windows.  
  
 Obvykle vytvoříte novou instanci třídy <xref:System.Drawing.Printing.PrintDocument> součást, nastavte vlastnosti, které popisují, co tisknout, pomocí <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings> třídy a volání <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda ve skutečnosti tisk dokumentu.  
  
 Během tisku z aplikace systému Windows <xref:System.Drawing.Printing.PrintDocument> součást zobrazí přerušení tiskové dialogové které uživatele upozorní na to, že dochází k tisku a umožnit tiskové úlohy ke zrušení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytváření standardních tiskových úloh modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 Vysvětluje, jak používat <xref:System.Drawing.Printing.PrintDocument> součást tisknout z formuláře Windows.  
  
 [Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Vysvětluje, jak upravit vybranou možností tisku programově pomocí <xref:System.Windows.Forms.PrintDialog> součásti.  
  
 [Postupy: Volba tiskáren připojených k počítači uživatele v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Popisuje změnu tiskárny pro tisk pomocí <xref:System.Windows.Forms.PrintDialog> součásti v době běhu.  
  
 [Postupy: Tisk grafiky v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 Popisuje odesílání grafiky na tiskárnu.  
  
 [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Popisuje odesílání textu na tiskárnu.  
  
 [Postupy: Dokončení tiskových úloh modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 Vysvětluje, jak upozornit uživatele na dokončení tiskových úloh.  
  
 [Postupy: Tisk formuláře Windows](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 Ukazuje, jak chcete vytisknout kopii aktuálního formuláře.  
  
 [Postupy: Tisk v modelu Windows Forms pomocí náhledu tisku](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 Ukazuje, jak používat <xref:System.Windows.Forms.PrintPreviewDialog> pro tisk dokumentu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Komponenta PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 Popisuje použití <xref:System.Drawing.Printing.PrintDocument> součásti.  
  
 [Komponenta PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 Popisuje použití <xref:System.Windows.Forms.PrintDialog> součásti.  
  
 [Ovládací prvek PrintPreviewDialog](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 Popisuje použití <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.  
  
 [Komponenta PageSetupDialog](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 Popisuje použití <xref:System.Windows.Forms.PageSetupDialog> součásti.  
  
 <xref:System.Drawing.Printing>  
 Popisuje třídy v <xref:System.Drawing.Printing> oboru názvů.
