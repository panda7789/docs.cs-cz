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
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708129"
---
# <a name="windows-forms-print-support"></a>Podpora tisku ve Windows Forms
Tisk ve Windows Forms se primárně skládá z použití [PrintDocument – komponenta](../controls/printdocument-component-windows-forms.md) komponenty, aby uživatelům tisknout a [printpreviewdialog – ovládací prvek](../controls/printpreviewdialog-control-windows-forms.md) ovládacího prvku, [PrintDialog Komponenta](../controls/printdialog-component-windows-forms.md) a [PageSetupDialog – komponenta](../controls/pagesetupdialog-component-windows-forms.md) součásti známému grafické rozhraní poskytovat Uživatelé zvyklí operačního systému Windows.  
  
 Obvykle vytvoříte novou instanci třídy <xref:System.Drawing.Printing.PrintDocument> komponenty, nastavte vlastnosti, které popisují, jak vytisknout pomocí <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings> třídy a volání <xref:System.Drawing.Printing.PrintDocument.Print%2A> metoda ve skutečnosti vytisknout dokument.  
  
 V průběhu tisk z aplikace založené na Windows <xref:System.Drawing.Printing.PrintDocument> komponenty zobrazí přerušení tisku dialogové okno s které uživatele upozorní na to, že dochází k tisku a umožňují tiskové úlohy budou zrušeny.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytvoření tiskových úloh standardní Windows Forms](how-to-create-standard-windows-forms-print-jobs.md)  
 Vysvětluje způsob používání <xref:System.Drawing.Printing.PrintDocument> komponenty tisknout z formuláře Windows.  
  
 [Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Vysvětluje, jak upravit vybrané možnosti tisku prostřednictvím kódu programu pomocí <xref:System.Windows.Forms.PrintDialog> komponenty.  
  
 [Postupy: Volba tiskáren připojených k počítači uživatele v modelu Windows Forms](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Popisuje změny tiskárny pro tisk na použití <xref:System.Windows.Forms.PrintDialog> komponentu v době běhu.  
  
 [Postupy: Tisk grafiky ve Windows Forms](how-to-print-graphics-in-windows-forms.md)  
 Popisuje odesílání grafiky k tiskárně.  
  
 [Postupy: Tisk vícestránkového textového souboru ve Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Popisuje odesílání text, který tiskárnu.  
  
 [Postupy: Kompletní Windows Forms tiskové úlohy](how-to-complete-windows-forms-print-jobs.md)  
 Vysvětluje, jak upozornit uživatele na dokončení tiskové úlohy.  
  
 [Postupy: Tisk formuláře Windows](how-to-print-a-windows-form.md)  
 Ukazuje, jak vytisknout kopii aktuálního formuláře.  
  
 [Postupy: Tisk ve Windows Forms pomocí náhledu tisku](how-to-print-in-windows-forms-using-print-preview.md)  
 Ukazuje, jak používat <xref:System.Windows.Forms.PrintPreviewDialog> pro tisk dokumentu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Komponenta PrintDocument](../controls/printdocument-component-windows-forms.md)  
 Vysvětluje použití <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
 [Komponenta PrintDialog](../controls/printdialog-component-windows-forms.md)  
 Vysvětluje použití <xref:System.Windows.Forms.PrintDialog> komponenty.  
  
 [Ovládací prvek PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md)  
 Vysvětluje použití <xref:System.Windows.Forms.PrintPreviewDialog> ovládacího prvku.  
  
 [Komponenta PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md)  
 Vysvětluje použití <xref:System.Windows.Forms.PageSetupDialog> komponenty.  
  
 <xref:System.Drawing.Printing>  
 Popisuje třídy v <xref:System.Drawing.Printing> oboru názvů.
