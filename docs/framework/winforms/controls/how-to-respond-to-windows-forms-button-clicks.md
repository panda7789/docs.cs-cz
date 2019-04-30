---
title: 'Postupy: Reakce na kliknutí na tlačítko Windows Forms'
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
ms.openlocfilehash: a10eaa3ea62df9301a53f5609b503bfabcb50a46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913078"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a>Postupy: Reakce na kliknutí na tlačítko Windows Forms
Základní použití prvku Windows Forms <xref:System.Windows.Forms.Button> ovládací prvek je ke spuštění kódu po kliknutí na tlačítko.  
  
 Kliknutím <xref:System.Windows.Forms.Button> ovládací prvek také vygeneruje celou řadou dalších událostí, jako <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, a <xref:System.Windows.Forms.Control.MouseUp> události. Pokud máte v úmyslu připojte obslužné rutiny událostí pro tyto související události, ujistěte se, že jejich akce není v konfliktu. Například pokud kliknutím na tlačítko vymaže informace, které uživatel zadal do textového pole, pak umístěním ukazatele myši nad tlačítkem by neměl zobrazení popisu tlačítka s touto nyní neexistující informací.  
  
 Pokud se uživatel pokusí dvakrát klikněte <xref:System.Windows.Forms.Button> ovládacího prvku, každé klikněte na tlačítko se zpracovávají odděleně; to znamená, ovládací prvek nepodporuje dvakrát klikněte na událost.  
  
### <a name="to-respond-to-a-button-click"></a>Reakce na kliknutí na tlačítko  
  
- Na tlačítku `Click` <xref:System.EventHandler> napsat kód ke spuštění. `Button1_Click` musí být vázán na ovládacím prvku. Další informace najdete v tématu [jak: Vytváření obslužných rutin událostí pro Windows Forms v době běhu](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
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
