---
title: "Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů"
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
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 80d28bdb85a91ddd3129e7e0fab443f81ba9ecef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStrip> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.  
  
 Pokud vaše formuláře Windows funkce <xref:System.Windows.Forms.ToolBar> ovládacího prvku pomocí tlačítka panelu nástrojů, budete chtít vědět, který uživatel klikne na tlačítko.  
  
 Na <xref:System.Windows.Forms.ToolBar.ButtonClick> události <xref:System.Windows.Forms.ToolBar> ovládací prvek, je možné vyhodnotit <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> vlastnost <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> třídy. V následujícím příkladu se zobrazí okno se zprávou, která určuje, které tlačítko bylo kliknuto. Podrobnosti najdete v tématu <xref:System.Windows.Forms.MessageBox>.  
  
 Následující příklad předpokládá <xref:System.Windows.Forms.ToolBar> ovládací prvek byl přidán do formuláře systému Windows.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Zpracování události klikněte na panelu nástrojů  
  
1.  V postupu, přidání tlačítek panelu nástrojů <xref:System.Windows.Forms.ToolBar> ovládacího prvku.  
  
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
  
2.  Přidání obslužné rutiny události pro <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.ButtonClick> událostí. Použít případu přepínání příkazu a <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> třídu k určení bylo stisknuto tlačítko panelu nástrojů. Na základě zobrazit odpovídající pole se zprávou.  
  
    > [!NOTE]
    >  Okno se zprávou se používá výhradně jako zástupný znak v tomto příkladu. Nebojte se, že jste přidat další kód provést po klepnutí na tlačítka panelu nástrojů.  
  
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
 <xref:System.Windows.Forms.ToolBar>  
 [Postupy: přidávání tlačítek do ovládacího prvku panel nástrojů](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)  
 [Postupy: definování ikony pro tlačítko panelu nástrojů](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [ToolBar – ovládací prvek](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
