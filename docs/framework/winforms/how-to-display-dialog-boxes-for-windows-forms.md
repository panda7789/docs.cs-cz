---
title: 'Postupy: Zobrazování dialogových oken pro Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, displaying
- Windows Forms dialog boxes [Windows Forms], displaying
- Windows Forms, calling one form from another
- dialog boxes [Windows Forms], displaying for Windows Forms
ms.assetid: aaac1b38-c651-495a-8d3d-5a9bfb32fee3
ms.openlocfilehash: a25fe86c4dde1fed69e192956d77615bf2a70402
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537421"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Postupy: Zobrazování dialogových oken pro Windows Forms
Zobrazit dialogové okno stejným způsobem zobrazí všechny formuláře v aplikaci. Formulář spuštění načte automaticky, když je aplikace spuštěna. Chcete-li druhý formulář nebo dialogové okno se zobrazí v aplikaci, napište kód pro načtení a zobrazit ji. Stejně tak aby formulář nebo dialogové okno pole zmizí, zápis kódu pro uvolnění nebo skrytí podokna.  
  
### <a name="to-display-a-dialog-box"></a>Chcete-li zobrazit dialogové okno  
  
1.  Přejděte k obslužné rutině událostí, pro který chcete otevřít dialogové okno. Tato situace může nastat, pokud je vybraný příkaz nabídky, při kliknutí na tlačítko nebo při výskytu další události.  
  
2.  V obslužné rutině události přidejte kód k otevření dialogového okna. V tomto příkladu se používá události kliknutí na tlačítko zobrazit dialogové okno:  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim dlg1 as new Form()  
       dlg1.ShowDialog()  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
       Form dlg1 = new Form();  
       dlg1.ShowDialog();  
    }  
    ```  
  
    ```cpp  
    private:   
      void button1_Click(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        Form ^ dlg1 = gcnew Form();  
        dlg1->ShowDialog();  
      }  
    ```
