---
title: 'Postup: Zobrazení dialogových oken'
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
ms.openlocfilehash: 3625080c7c322e297a9de92e4f95a40c0caf3e72
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181977"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Postupy: Zobrazování dialogových oken pro Windows Forms
Dialogové okno se zobrazí stejným způsobem jako jakýkoli jiný formulář v aplikaci. Spouštěcí formulář se načte automaticky při spuštění aplikace. Chcete-li, aby se v aplikaci objevil druhý formulář nebo dialogové okno, napište kód, který se načte a zobrazí. Podobně chcete-li, aby formulář nebo dialogové okno zmizelo, napište kód pro jeho uvolnění nebo skrytí.  
  
### <a name="to-display-a-dialog-box"></a>Zobrazení dialogového okna  
  
1. Přejděte na obslužnou rutinu události, se kterou chcete dialogové okno otevřít. K tomu může dojít, když je vybrán příkaz nabídky, klepnutí na tlačítko nebo při výskytu jakékoli jiné události.  
  
2. V obslužné rutině události přidejte kód a otevřete dialogové okno. V tomto příkladu se k zobrazení dialogového okna používá událost kliknutí na tlačítko:  
  
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
