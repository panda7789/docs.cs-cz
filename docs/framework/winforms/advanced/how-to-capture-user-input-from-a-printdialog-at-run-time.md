---
title: 'Postupy: Zachytávání uživatelského vstupu z komponenty PrintDialog při běhu'
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
ms.openlocfilehash: 2aaf988f362baf9cd80eb16e4a08f7f65a5077bb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311419"
---
# <a name="how-to-capture-user-input-from-a-printdialog-at-run-time"></a>Postupy: Zachytávání uživatelského vstupu z komponenty PrintDialog při běhu
Když nastavíte možnosti související s tiskem v době návrhu, někdy můžete změnit tyto možnosti v době běhu, pravděpodobně z důvodu volby provedené uživatelem. Můžete zaznamenat uživatelský vstup pro tisk dokumentu pomocí <xref:System.Windows.Forms.PrintDialog> a <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
### <a name="to-change-print-options-programmatically"></a>Chcete-li změnit možnosti tisku prostřednictvím kódu programu  
  
1. Přidat <xref:System.Windows.Forms.PrintDialog> a <xref:System.Drawing.Printing.PrintDocument> komponentu do formuláře.  
  
2. Nastavte <xref:System.Windows.Forms.PrintDialog.Document%2A> vlastnost <xref:System.Windows.Forms.PrintDialog> k <xref:System.Drawing.Printing.PrintDocument> přidán do formuláře.  
  
    ```vb  
    PrintDialog1.Document = PrintDocument1  
    ```  
  
    ```csharp  
    printDialog1.Document = PrintDocument1;  
    ```  
  
    ```cpp  
    printDialog1->Document = PrintDocument1;  
    ```  
  
3. Zobrazení <xref:System.Windows.Forms.PrintDialog> komponentu pomocí <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.  
  
    ```vb  
    PrintDialog1.ShowDialog()  
    ```  
  
    ```csharp  
    printDialog1.ShowDialog();  
    ```  
  
    ```cpp  
    printDialog1->ShowDialog();  
    ```  
  
4. Možnosti tisku uživatele z tohoto dialogového okna bude zkopírován do <xref:System.Drawing.Printing.PrinterSettings> vlastnost <xref:System.Drawing.Printing.PrintDocument> komponenty.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Tisk vícestránkového textového souboru v modelu Windows Forms](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [Podpora tisku ve Windows Forms](windows-forms-print-support.md)
