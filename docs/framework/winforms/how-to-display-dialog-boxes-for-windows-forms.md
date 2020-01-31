---
title: 'Postupy: zobrazení dialogových oken'
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
ms.openlocfilehash: dd04a06eaa0dd7583ef2f72edb4cffa99aaaa60c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739459"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Postupy: Zobrazování dialogových oken pro Windows Forms
Dialogové okno se zobrazí stejným způsobem jako jakýkoli jiný formulář v aplikaci. Spouštěcí formulář se při spuštění aplikace automaticky načte. Chcete-li v aplikaci zobrazit druhý formulář nebo dialogové okno, zadejte kód pro načtení a zobrazení. Podobně pokud chcete, aby formulář nebo dialogové okno zmizely, napište kód pro uvolnění nebo skrytí.  
  
### <a name="to-display-a-dialog-box"></a>Zobrazení dialogového okna  
  
1. Přejděte k obslužné rutině události, pomocí které chcete otevřít dialogové okno. K tomu může dojít při výběru příkazu nabídky, při kliknutí na tlačítko nebo při výskytu jakékoli jiné události.  
  
2. V obslužné rutině události přidejte kód pro otevření dialogového okna. V tomto příkladu se k zobrazení dialogového okna používá událost kliknutí tlačítkem myši:  
  
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
