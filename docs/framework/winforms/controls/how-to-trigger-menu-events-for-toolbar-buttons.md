---
title: 'Postupy: Aktivační události nabídky pro tlačítka panelu nástrojů'
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
ms.openlocfilehash: 6459c61e49a49001d490d5213f23ff652d4a1939
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609587"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a><span data-ttu-id="30b6f-102">Postupy: Aktivační události nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="30b6f-102">How to: Trigger Menu Events for Toolbar Buttons</span></span>
> [!NOTE]
>  <span data-ttu-id="30b6f-103"><xref:System.Windows.Forms.ToolStrip> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="30b6f-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="30b6f-104">Pokud vaše funkce formuláře Windows <xref:System.Windows.Forms.ToolBar> ovládacího prvku pomocí tlačítka panelu nástrojů, budou chtít vědět, která tlačítko uživatel klikne.</span><span class="sxs-lookup"><span data-stu-id="30b6f-104">If your Windows Form features a <xref:System.Windows.Forms.ToolBar> control with toolbar buttons, you will want to know which button the user clicks.</span></span>  
  
 <span data-ttu-id="30b6f-105">Na <xref:System.Windows.Forms.ToolBar.ButtonClick> událost <xref:System.Windows.Forms.ToolBar> ovládacího prvku, lze vyhodnotit <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> vlastnost <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> třídy.</span><span class="sxs-lookup"><span data-stu-id="30b6f-105">On the <xref:System.Windows.Forms.ToolBar.ButtonClick> event of the <xref:System.Windows.Forms.ToolBar> control, you can evaluate the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> property of the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class.</span></span> <span data-ttu-id="30b6f-106">V následujícím příkladu se zobrazí okno se zprávou, určující, které tlačítko došlo ke kliknutí na.</span><span class="sxs-lookup"><span data-stu-id="30b6f-106">In the example below, a message box is shown, indicating which button was clicked.</span></span> <span data-ttu-id="30b6f-107">Podrobnosti najdete v tématu <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="30b6f-107">For details, see <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
 <span data-ttu-id="30b6f-108">Následující příklad předpokládá <xref:System.Windows.Forms.ToolBar> ovládací prvek byl přidán do formuláře Windows.</span><span class="sxs-lookup"><span data-stu-id="30b6f-108">The example below assumes a <xref:System.Windows.Forms.ToolBar> control has been added to a Windows Form.</span></span>  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a><span data-ttu-id="30b6f-109">Zpracování události kliknutí na panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="30b6f-109">To handle the Click event on a toolbar</span></span>  
  
1.  <span data-ttu-id="30b6f-110">V postupu, přidání tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="30b6f-110">In a procedure, add toolbar buttons to the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
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
  
2.  <span data-ttu-id="30b6f-111">Přidat obslužnou rutinu události pro <xref:System.Windows.Forms.ToolBar> ovládacího prvku <xref:System.Windows.Forms.ToolBar.ButtonClick> událostí.</span><span class="sxs-lookup"><span data-stu-id="30b6f-111">Add an event handler for the <xref:System.Windows.Forms.ToolBar> control's <xref:System.Windows.Forms.ToolBar.ButtonClick> event.</span></span> <span data-ttu-id="30b6f-112">Přepnutí příkaz případu a <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> třídu k určení, ke které došlo ke kliknutí na tlačítko na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="30b6f-112">Use a case switching statement and the <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> class to determine the toolbar button that was clicked.</span></span> <span data-ttu-id="30b6f-113">Na základě toho zobrazit příslušné pole se zprávou.</span><span class="sxs-lookup"><span data-stu-id="30b6f-113">Based on this, show an appropriate message box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30b6f-114">Okno se zprávou slouží pouze jako zástupný symbol v tomto příkladu.</span><span class="sxs-lookup"><span data-stu-id="30b6f-114">A message box is being used solely as a placeholder in this example.</span></span> <span data-ttu-id="30b6f-115">Teď můžete přidat další kód ke spuštění po klepnutí na tlačítka na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="30b6f-115">Feel free to add other code to execute when the toolbar buttons are clicked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30b6f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30b6f-116">See also</span></span>
- <xref:System.Windows.Forms.ToolBar>
- [<span data-ttu-id="30b6f-117">Postupy: Přidání tlačítek do ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="30b6f-117">How to: Add Buttons to a ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md)
- [<span data-ttu-id="30b6f-118">Postupy: Definování ikony pro tlačítko ToolBar</span><span class="sxs-lookup"><span data-stu-id="30b6f-118">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)
- [<span data-ttu-id="30b6f-119">Ovládací prvek ToolBar</span><span class="sxs-lookup"><span data-stu-id="30b6f-119">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
