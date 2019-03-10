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
ms.openlocfilehash: 7ebafd745290a40fa6f4f83910fb32d67cdcff75
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705249"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="eceea-102">Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eceea-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>
<span data-ttu-id="eceea-103">Kromě vytváření událostí pomocí Návrháře formulářů Windows, můžete také vytvořit obslužnou rutinu události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="eceea-103">In addition to creating events using the Windows Forms Designer, you can also create an event handler at run time.</span></span> <span data-ttu-id="eceea-104">Tato akce umožňuje připojit obslužné rutiny události na základě podmínek v kódu v době běhu na rozdíl od toho připojení při počátečním spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="eceea-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>  
  
### <a name="to-create-an-event-handler-at-run-time"></a><span data-ttu-id="eceea-105">Chcete-li vytvořit obslužnou rutinu události v době běhu</span><span class="sxs-lookup"><span data-stu-id="eceea-105">To create an event handler at run time</span></span>  
  
1.  <span data-ttu-id="eceea-106">Otevřete v editoru kódu, který chcete přidat obslužnou rutinu události pro formulář.</span><span class="sxs-lookup"><span data-stu-id="eceea-106">Open the form in the Code Editor that you want to add an event handler to.</span></span>  
  
2.  <span data-ttu-id="eceea-107">Přidání metody do svého formuláře s podpis metody pro události, ke které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="eceea-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>  
  
     <span data-ttu-id="eceea-108">Například, pokud byly zpracování <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku, vytvořili byste metodu, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="eceea-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>  
  
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
  
3.  <span data-ttu-id="eceea-109">Přidejte kód do obslužné rutiny události jako vhodné pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eceea-109">Add code to the event handler as appropriate to your application.</span></span>  
  
4.  <span data-ttu-id="eceea-110">Určete, které tvoří nebo chcete vytvořit obslužnou rutinu události pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="eceea-110">Determine which form or control you want to create an event handler for.</span></span>  
  
5.  <span data-ttu-id="eceea-111">V metodě v rámci třídy formuláře přidejte kód, který určuje chcete zpracovat událost obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="eceea-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="eceea-112">Například následující kód určuje obslužná rutina události `button1_Click` obslužné rutiny <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="eceea-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="eceea-113"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metoda jsme vám ukázali ve výše uvedeném kódu jazyka Visual Basic vytvoří obslužnou rutinu události kliknutí pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="eceea-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eceea-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eceea-114">See also</span></span>
- [<span data-ttu-id="eceea-115">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eceea-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="eceea-116">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="eceea-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="eceea-117">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eceea-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
