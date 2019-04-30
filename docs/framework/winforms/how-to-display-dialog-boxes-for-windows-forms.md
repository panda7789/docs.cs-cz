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
ms.openlocfilehash: b99f2273dae88faf86448da6e1d2986a83803abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802580"
---
# <a name="how-to-display-dialog-boxes-for-windows-forms"></a>Postupy: Zobrazování dialogových oken pro Windows Forms
Zobrazit dialogové okno stejným způsobem, zobrazit jiné formuláře v aplikaci. Změna formuláře úvodního formuláře načte automaticky při spuštění aplikace. Chcete-li druhý formulář nebo dialogové okno se zobrazí v aplikaci, napište kód pro načtení a zobrazení. Podobně aby formulář nebo dialogové okno pole zmizí, napište kód, který uvolnit nebo skryli.  
  
### <a name="to-display-a-dialog-box"></a>Chcete-li zobrazit dialogové okno  
  
1. Přejděte do obslužné rutiny události, které chcete otevřít dialogové okno. Tomu může dojít, pokud příkaz nabídky je vybraná, po kliknutí na tlačítko, nebo když dojde k jakékoli události.  
  
2. V obslužné rutině události přidejte kód pro otevření dialogového okna. V tomto příkladu je události kliknutí na tlačítko použít zobrazíte dialogové okno:  
  
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
