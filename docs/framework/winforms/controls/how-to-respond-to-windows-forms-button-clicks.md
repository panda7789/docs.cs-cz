---
title: Reakce na kliknutí na ovládací prvek Button
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], responding to Click events
- events [Windows Forms], Click events
- Click event [Windows Forms], Button control
- MouseDown event
- Button control [Windows Forms], click response
- double-clicks
- examples [Windows Forms], controls
- Click event [Windows Forms], responding to
ms.assetid: 7a4951bd-369c-4662-b246-28ad83eda484
ms.openlocfilehash: dd6cf75a316257c86a23b44a818422336c12aa67
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735714"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Postupy: Reakce na kliknutí na tlačítko Windows Forms
Nejzákladnější použití ovládacího prvku model Windows Forms <xref:System.Windows.Forms.Button> je spuštění kódu při kliknutí na tlačítko.  
  
 Kliknutím na <xref:System.Windows.Forms.Button> ovládací prvek vygenerujete také řadu dalších událostí, jako jsou události <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>a <xref:System.Windows.Forms.Control.MouseUp>. Pokud máte v úmyslu připojit obslužné rutiny událostí pro tyto související události, ujistěte se, že jejich akce nejsou v konfliktu. Pokud například kliknutím na tlačítko zrušíte informace, které uživatel zadal v textovém poli, pak se při pozastavení ukazatele myši na tlačítko nezobrazí popis tlačítka s aktuálně neexistujícími informacemi.  
  
 Pokud se uživatel pokusí dvakrát kliknout na ovládací prvek <xref:System.Windows.Forms.Button>, každé kliknutí se zpracuje samostatně; To znamená, že ovládací prvek nepodporuje událost dvojitého kliknutí.  
  
### <a name="to-respond-to-a-button-click"></a>Reakce na kliknutí na tlačítko  
  
- V `Click` tlačítka <xref:System.EventHandler> napište kód, který se má spustit. `Button1_Click` musí být svázány s ovládacím prvkem. Další informace naleznete v tématu [Postupy: vytváření obslužných rutin událostí v době běhu pro model Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       MessageBox.Show("Button1 was clicked")  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       MessageBox.Show("button1 was clicked");  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          MessageBox::Show("button1 was clicked");  
       }  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku Button](button-control-overview-windows-forms.md)
- [Metody výběru ovládacího prvku Windows Forms Button](ways-to-select-a-windows-forms-button-control.md)
- [Ovládací prvek Button](button-control-windows-forms.md)
