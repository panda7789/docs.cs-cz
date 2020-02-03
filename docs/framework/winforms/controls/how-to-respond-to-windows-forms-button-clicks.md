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
# <a name="how-to-respond-to-windows-forms-button-clicks"></a><span data-ttu-id="8216b-102">Postupy: Reakce na kliknutí na tlačítko Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8216b-102">How to: Respond to Windows Forms Button Clicks</span></span>
<span data-ttu-id="8216b-103">Nejzákladnější použití ovládacího prvku model Windows Forms <xref:System.Windows.Forms.Button> je spuštění kódu při kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="8216b-103">The most basic use of a Windows Forms <xref:System.Windows.Forms.Button> control is to run some code when the button is clicked.</span></span>  
  
 <span data-ttu-id="8216b-104">Kliknutím na <xref:System.Windows.Forms.Button> ovládací prvek vygenerujete také řadu dalších událostí, jako jsou události <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>a <xref:System.Windows.Forms.Control.MouseUp>.</span><span class="sxs-lookup"><span data-stu-id="8216b-104">Clicking a <xref:System.Windows.Forms.Button> control also generates a number of other events, such as the <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseDown>, and <xref:System.Windows.Forms.Control.MouseUp> events.</span></span> <span data-ttu-id="8216b-105">Pokud máte v úmyslu připojit obslužné rutiny událostí pro tyto související události, ujistěte se, že jejich akce nejsou v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="8216b-105">If you intend to attach event handlers for these related events, be sure that their actions do not conflict.</span></span> <span data-ttu-id="8216b-106">Pokud například kliknutím na tlačítko zrušíte informace, které uživatel zadal v textovém poli, pak se při pozastavení ukazatele myši na tlačítko nezobrazí popis tlačítka s aktuálně neexistujícími informacemi.</span><span class="sxs-lookup"><span data-stu-id="8216b-106">For example, if clicking the button clears information that the user has typed in a text box, pausing the mouse pointer over the button should not display a tool tip with that now-nonexistent information.</span></span>  
  
 <span data-ttu-id="8216b-107">Pokud se uživatel pokusí dvakrát kliknout na ovládací prvek <xref:System.Windows.Forms.Button>, každé kliknutí se zpracuje samostatně; To znamená, že ovládací prvek nepodporuje událost dvojitého kliknutí.</span><span class="sxs-lookup"><span data-stu-id="8216b-107">If the user attempts to double-click the <xref:System.Windows.Forms.Button> control, each click will be processed separately; that is, the control does not support the double-click event.</span></span>  
  
### <a name="to-respond-to-a-button-click"></a><span data-ttu-id="8216b-108">Reakce na kliknutí na tlačítko</span><span class="sxs-lookup"><span data-stu-id="8216b-108">To respond to a button click</span></span>  
  
- <span data-ttu-id="8216b-109">V `Click` tlačítka <xref:System.EventHandler> napište kód, který se má spustit.</span><span class="sxs-lookup"><span data-stu-id="8216b-109">In the button's `Click` <xref:System.EventHandler> write the code to run.</span></span> <span data-ttu-id="8216b-110">`Button1_Click` musí být svázány s ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="8216b-110">`Button1_Click` must be bound to the control.</span></span> <span data-ttu-id="8216b-111">Další informace naleznete v tématu [Postupy: vytváření obslužných rutin událostí v době běhu pro model Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8216b-111">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8216b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="8216b-112">See also</span></span>

- [<span data-ttu-id="8216b-113">Přehled ovládacího prvku Button</span><span class="sxs-lookup"><span data-stu-id="8216b-113">Button Control Overview</span></span>](button-control-overview-windows-forms.md)
- [<span data-ttu-id="8216b-114">Metody výběru ovládacího prvku Windows Forms Button</span><span class="sxs-lookup"><span data-stu-id="8216b-114">Ways to Select a Windows Forms Button Control</span></span>](ways-to-select-a-windows-forms-button-control.md)
- [<span data-ttu-id="8216b-115">Ovládací prvek Button</span><span class="sxs-lookup"><span data-stu-id="8216b-115">Button Control</span></span>](button-control-windows-forms.md)
