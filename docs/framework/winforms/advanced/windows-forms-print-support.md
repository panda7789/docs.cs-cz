---
title: Podpora tisku
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732489"
---
# <a name="windows-forms-print-support"></a>Podpora tisku ve Windows Forms
Tisk v model Windows Forms se skládá hlavně z použití komponenty [komponenty PrintDocument](../controls/printdocument-component-windows-forms.md) , aby mohl uživatel tisknout, a ovládací prvek [řízení PrintPreviewDialog –](../controls/printpreviewdialog-control-windows-forms.md) , komponenty [PrintDialog komponenty](../controls/printdialog-component-windows-forms.md) a komponenty [PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md) poskytují známé grafické rozhraní pro uživatele, kteří jsou zvyklí na operační systém Windows.  
  
 Obvykle vytvoříte novou instanci součásti <xref:System.Drawing.Printing.PrintDocument>, nastavíte vlastnosti, které popisují, co tisknout pomocí tříd <xref:System.Drawing.Printing.PrinterSettings> a <xref:System.Drawing.Printing.PageSettings>, a zavolejte metodu <xref:System.Drawing.Printing.PrintDocument.Print%2A> pro skutečný tisk dokumentu.  
  
 V průběhu tisku z aplikace pro systém Windows bude <xref:System.Drawing.Printing.PrintDocument> komponenta zobrazovat dialogové okno přerušit tisk, aby byli uživatelé upozorněni na skutečnost, že k tisku dochází a zda se má tisková úloha zrušit.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytváření standardních tiskových úloh modelu Windows Forms](how-to-create-standard-windows-forms-print-jobs.md)  
 Vysvětluje, jak používat komponentu <xref:System.Drawing.Printing.PrintDocument> k tisku z formuláře Windows Form.  
  
 [Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Vysvětluje, jak upravit vybrané možnosti tisku programově pomocí <xref:System.Windows.Forms.PrintDialog> komponenty.  
  
 [Postupy: Volba tiskáren připojených k počítači uživatele v modelu Windows Forms](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 V této části najdete popis změny tiskárny pro tisk pomocí <xref:System.Windows.Forms.PrintDialog> komponenty v době běhu.  
  
 [Postupy: Tisk grafiky v modelu Windows Forms](how-to-print-graphics-in-windows-forms.md)  
 Popisuje odeslání grafiky na tiskárnu.  
  
 [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Popisuje odeslání textu do tiskárny.  
  
 [Postupy: Dokončení tiskových úloh modelu Windows Forms](how-to-complete-windows-forms-print-jobs.md)  
 Vysvětluje, jak upozornit uživatele na dokončení tiskové úlohy.  
  
 [Postupy: Tisk formuláře Windows](how-to-print-a-windows-form.md)  
 Ukazuje, jak vytisknout kopii aktuálního formuláře.  
  
 [Postupy: Tisk v modelu Windows Forms pomocí náhledu tisku](how-to-print-in-windows-forms-using-print-preview.md)  
 Ukazuje, jak použít <xref:System.Windows.Forms.PrintPreviewDialog> pro tisk dokumentu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Komponenta PrintDocument](../controls/printdocument-component-windows-forms.md)  
 Vysvětluje použití součásti <xref:System.Drawing.Printing.PrintDocument>.  
  
 [Komponenta PrintDialog](../controls/printdialog-component-windows-forms.md)  
 Vysvětluje použití součásti <xref:System.Windows.Forms.PrintDialog>.  
  
 [Ovládací prvek PrintPreviewDialog](../controls/printpreviewdialog-control-windows-forms.md)  
 Vysvětluje použití ovládacího prvku <xref:System.Windows.Forms.PrintPreviewDialog>.  
  
 [Komponenta PageSetupDialog](../controls/pagesetupdialog-component-windows-forms.md)  
 Vysvětluje použití součásti <xref:System.Windows.Forms.PageSetupDialog>.  
  
 <xref:System.Drawing.Printing>  
 Popisuje třídy v oboru názvů <xref:System.Drawing.Printing>.
