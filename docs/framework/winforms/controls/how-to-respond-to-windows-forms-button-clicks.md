---
title: "Postupy: Reakce na kliknutí na tlačítko Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28b0467c8b589882fe5afd7e884d0de55d8ca564
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Postupy: Reakce na kliknutí na tlačítko Windows Forms
Nejzákladnější použití Windows Forms <xref:System.Windows.Forms.Button> ovládacího prvku je při kliknutí na tlačítko spouštět nějaký kód.  
  
 Kliknutím na tlačítko <xref:System.Windows.Forms.Button> řízení vytvoří také několik dalších událostí, jako <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, a <xref:System.Windows.Forms.Control.MouseUp> události. Pokud máte v úmyslu připojení obslužné rutiny události pro tyto související události, ujistěte se, že jejich akce nejsou v konfliktu. Například pokud kliknete na tlačítko vymaže informace, které uživatel zadal v textovém poli, pozastavení ukazatel myši nad tlačítko nesmí zobrazí se s touto nyní neexistující informací.  
  
 Pokud se uživatel pokusí dvakrát klikněte <xref:System.Windows.Forms.Button> ovládací prvek, každý klikněte na tlačítko se zpracovávají odděleně; to znamená, ovládacího prvku nepodporuje událost poklikejte na soubor.  
  
### <a name="to-respond-to-a-button-click"></a>Reakce na kliknutí na tlačítko  
  
-   U tlačítka `Click` <xref:System.EventHandler> psát kód pro spuštění. `Button1_Click`musí být vázána k ovládacímu prvku. Další informace najdete v tématu [postupy: vytváření obslužných rutin událostí spustit čas pro Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Metody výběru ovládacího prvku Windows Forms Button](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Ovládací prvek Button](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
