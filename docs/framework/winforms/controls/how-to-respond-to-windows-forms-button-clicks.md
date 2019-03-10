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
ms.openlocfilehash: e6e6d041422a79171ec4b6159f0789b8aa6a50d5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724983"
---
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="b21cb-102">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b21cb-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="b21cb-103">Základní použití prvku Windows Forms <xref:System.Windows.Forms.Button> ovládací prvek je ke spuštění kódu po kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="b21cb-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="b21cb-104">Kliknutím <xref:System.Windows.Forms.Button> ovládací prvek také vygeneruje celou řadou dalších událostí, jako <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, a <xref:System.Windows.Forms.Control.MouseUp> události.</span><span class="sxs-lookup"><span data-stu-id="b21cb-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="b21cb-105">Pokud máte v úmyslu připojte obslužné rutiny událostí pro tyto související události, ujistěte se, že jejich akce není v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="b21cb-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="b21cb-106">Například pokud kliknutím na tlačítko vymaže informace, které uživatel zadal do textového pole, pak umístěním ukazatele myši nad tlačítkem by neměl zobrazení popisu tlačítka s touto nyní neexistující informací.</span><span class="sxs-lookup"><span data-stu-id="b21cb-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="b21cb-107">Pokud se uživatel pokusí dvakrát klikněte <xref:System.Windows.Forms.Button> ovládacího prvku, každé klikněte na tlačítko se zpracovávají odděleně; to znamená, ovládací prvek nepodporuje dvakrát klikněte na událost.</span><span class="sxs-lookup"><span data-stu-id="b21cb-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="b21cb-108">Reakce na kliknutí na tlačítko</span><span class="sxs-lookup"><span data-stu-id="b21cb-108">To respond to a button click</span></span>  
  
-   <span data-ttu-id="b21cb-109">Na tlačítku `Click` <xref:System.EventHandler> napsat kód ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="b21cb-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="b21cb-110">`Button1_Click` musí být vázán na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="b21cb-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="b21cb-111">Další informace najdete v tématu [jak: Vytváření obslužných rutin událostí pro Windows Forms v době běhu](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="b21cb-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b21cb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b21cb-112">See also</span></span>
- [<span data-ttu-id="b21cb-113">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="b21cb-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="b21cb-114">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="b21cb-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="b21cb-115">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="b21cb-115">Button Control</span></span>](button-control-windows-forms.md)
