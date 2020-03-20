---
title: 'Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
ms.openlocfilehash: 99db077b41a59fe9263f7283b58b8c31959c7c79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182081"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů
> [!NOTE]
> Ovládací <xref:System.Windows.Forms.ToolStrip> prvek nahradí a přidá <xref:System.Windows.Forms.ToolBar> funkce ovládacího prvku; <xref:System.Windows.Forms.ToolBar> ovládací prvek je však zachován a to jak pro zpětnou kompatibilitu, tak pro budoucí použití, pokud se rozhodnete.  
  
 Pokud formulář systému <xref:System.Windows.Forms.ToolBar> Windows obsahuje ovládací prvek s tlačítky panelu nástrojů, budete chtít vědět, na které tlačítko uživatel klepne.  
  
 V <xref:System.Windows.Forms.ToolBar.ButtonClick> případě ovládacího <xref:System.Windows.Forms.ToolBar> prvku můžete <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> vyhodnotit <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> vlastnost třídy. V níže uvedeném příkladu se zobrazí okno se zprávou označující, na které tlačítko bylo kliknuto. Podrobnosti najdete v tématu <xref:System.Windows.Forms.MessageBox>.  
  
 Následující příklad předpokládá, <xref:System.Windows.Forms.ToolBar> že ovládací prvek byl přidán do formuláře systému Windows.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Zpracování události Click na panelu nástrojů  
  
1. V postupu přidejte tlačítka panelu nástrojů do ovládacího <xref:System.Windows.Forms.ToolBar> prvku.  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
    ```  
  
    ```csharp  
    public void ToolBarConfig()
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2. Přidejte obslužnou <xref:System.Windows.Forms.ToolBar> <xref:System.Windows.Forms.ToolBar.ButtonClick> rutinu události pro událost ovládacího prvku. Pomocí příkazu přepínání případů <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> a třídy určete tlačítko panelu nástrojů, na které bylo kliknuto. Na základě tohoto, zobrazit příslušné okno se zprávou.  
  
    > [!NOTE]
    > Okno se zprávou se používá výhradně jako zástupný symbol v tomto příkladu. Neváhejte a přidejte další kód ke spuštění při klepnutí na tlačítka panelu nástrojů.  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolBar>
- [Postupy: Přidání tlačítek do ovládacího prvku ToolBar](how-to-add-buttons-to-a-toolbar-control.md)
- [Postupy: Definování ikony pro tlačítko ToolBar](how-to-define-an-icon-for-a-toolbar-button.md)
- [ToolBar – ovládací prvek](toolbar-control-windows-forms.md)
