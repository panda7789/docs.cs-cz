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
ms.openlocfilehash: 554c3c43f8ac4d41ddfc8651472d0b7fbed960bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522873"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Postupy: Zachycení uživatelského vstupu z komponenty PrintDialog při běhu
Když nastavíte možnosti týkající se tisku v době návrhu, někdy můžete tyto možnosti změnit za běhu, pravděpodobně z důvodu volby provedené uživatelem. Můžete zachycení uživatelského vstupu pro tisk dokumentu pomocí <xref:System.Windows.Forms.PrintDialog> a <xref:System.Drawing.Printing.PrintDocument> součásti.  
  
### <a name="to-change-print-options-programmatically"></a>Chcete-li změnit možnosti tisku prostřednictvím kódu programu  
  
1.  Přidat <xref:System.Windows.Forms.PrintDialog> a <xref:System.Drawing.Printing.PrintDocument> součásti do svého formuláře.  
  
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
  
3.  Zobrazení <xref:System.Windows.Forms.PrintDialog> součásti pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metoda.  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4.  Tisk volby uživatele z tohoto dialogového okna se zkopírují na <xref:System.Drawing.Printing.PrinterSettings> vlastnost <xref:System.Drawing.Printing.PrintDocument> součásti.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [Podpora tisku v modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
