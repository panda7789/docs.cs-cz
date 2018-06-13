---
title: 'Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
ms.openlocfilehash: 38453c751e6cc63827f3f1e9d20ad2ebdfc841d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538002"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="6832b-102">Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6832b-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>
<span data-ttu-id="6832b-103">Kromě vytváření událostí pomocí Návrhář formulářů Windows, můžete také vytvořit obslužnou rutinu události za běhu.</span><span class="sxs-lookup"><span data-stu-id="6832b-103">In addition to creating events using the Windows Forms Designer, you can also create an event handler at run time.</span></span> <span data-ttu-id="6832b-104">Tato akce umožňuje připojit obslužné rutiny událostí na základě podmínek v kódu v době běhu rozdíl od toho, aby připojení při počátečním spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="6832b-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>  
  
### <a name="to-create-an-event-handler-at-run-time"></a><span data-ttu-id="6832b-105">Pro vytvoření obslužné rutiny událostí v době běhu</span><span class="sxs-lookup"><span data-stu-id="6832b-105">To create an event handler at run time</span></span>  
  
1.  <span data-ttu-id="6832b-106">Otevřete v editoru kódu, kterou chcete přidat obslužné rutiny události pro formulář.</span><span class="sxs-lookup"><span data-stu-id="6832b-106">Open the form in the Code Editor that you want to add an event handler to.</span></span>  
  
2.  <span data-ttu-id="6832b-107">Přidání metody do svého formuláře s podpis metody pro událost, která chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="6832b-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>  
  
     <span data-ttu-id="6832b-108">Například, pokud byly zpracování <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> řízení, by vytvoření metody, jako jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6832b-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)  
       ' Add event handler code here.  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
    // Add event handler code here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          // Add event handler code here.  
       }  
    ```  
  
3.  <span data-ttu-id="6832b-109">Přidejte kód pro obslužnou rutinu události v závislosti na vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="6832b-109">Add code to the event handler as appropriate to your application.</span></span>  
  
4.  <span data-ttu-id="6832b-110">Určí, které tvoří nebo chcete vytvořit obslužnou rutinu události pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="6832b-110">Determine which form or control you want to create an event handler for.</span></span>  
  
5.  <span data-ttu-id="6832b-111">Metoda v rámci svého formuláře třídy přidejte kód, který určuje obslužné rutiny události ke zpracování události.</span><span class="sxs-lookup"><span data-stu-id="6832b-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="6832b-112">Například následující kód určuje obslužné rutiny události `button1_Click` obslužné rutiny <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="6832b-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="6832b-113"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metoda ukázán ve výše uvedeném kódu jazyka Visual Basic vytvoří obslužnou rutinu události kliknutí na tlačítko o velikosti.</span><span class="sxs-lookup"><span data-stu-id="6832b-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6832b-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="6832b-114">See Also</span></span>  
 [<span data-ttu-id="6832b-115">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6832b-115">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="6832b-116">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="6832b-116">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 [<span data-ttu-id="6832b-117">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6832b-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
