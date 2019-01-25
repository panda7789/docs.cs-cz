---
title: 'Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print options [Windows Forms], changing at run time
- printing [Windows Forms], options
- print options
- run time [Windows Forms], changing print options
ms.assetid: 438501d8-9a70-4fb3-aae6-e46579aba0c6
ms.openlocfilehash: a15563560615f5b857220c0b548fc57f31ee4e09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527663"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu
Když nastavíte možnosti související s tiskem v době návrhu, někdy můžete změnit tyto možnosti v době běhu, pravděpodobně z důvodu volby provedené uživatelem. Můžete zaznamenat uživatelský vstup pro tisk dokumentu pomocí <xref:System.Windows.Forms.PrintDialog> a <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
### <a name="to-change-print-options-programmatically"></a>Chcete-li změnit možnosti tisku prostřednictvím kódu programu  
  
1.  Přidat <xref:System.Windows.Forms.PrintDialog> a <xref:System.Drawing.Printing.PrintDocument> komponentu do formuláře.  
  
2.  Nastavte <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintDialog> k <xref:System.Drawing.Printing.PrintDocument> přidán do formuláře.  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3.  Zobrazení <xref:System.Windows.Forms.PrintDialog> komponentu pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  Možnosti tisku uživatele z tohoto dialogového okna bude zkopírován do <xref:System.Drawing.Printing.PrinterSettings> vlastnost <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Tisk vícestránkového textového souboru ve Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
