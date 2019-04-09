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
ms.openlocfilehash: 3c1dca420b9e63fe8a2cb93b2e7918d9dc35e84d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158545"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="019c6-102">Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="019c6-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>
<span data-ttu-id="019c6-103">Kromě vytváření událostí pomocí Návrháře formulářů Windows, můžete také vytvořit obslužnou rutinu události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="019c6-103">In addition to creating events using the Windows Forms Designer, you can also create an event handler at run time.</span></span> <span data-ttu-id="019c6-104">Tato akce umožňuje připojit obslužné rutiny události na základě podmínek v kódu v době běhu na rozdíl od toho připojení při počátečním spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="019c6-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>  
  
### <a name="to-create-an-event-handler-at-run-time"></a><span data-ttu-id="019c6-105">Chcete-li vytvořit obslužnou rutinu události v době běhu</span><span class="sxs-lookup"><span data-stu-id="019c6-105">To create an event handler at run time</span></span>  
  
1.  <span data-ttu-id="019c6-106">Otevřete v editoru kódu, který chcete přidat obslužnou rutinu události pro formulář.</span><span class="sxs-lookup"><span data-stu-id="019c6-106">Open the form in the Code Editor that you want to add an event handler to.</span></span>  
  
2.  <span data-ttu-id="019c6-107">Přidání metody do svého formuláře s podpis metody pro události, ke které chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="019c6-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>  
  
     <span data-ttu-id="019c6-108">Například, pokud byly zpracování <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku, vytvořili byste metodu, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="019c6-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>  
  
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
  
3.  <span data-ttu-id="019c6-109">Přidejte kód do obslužné rutiny události jako vhodné pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="019c6-109">Add code to the event handler as appropriate to your application.</span></span>  
  
4.  <span data-ttu-id="019c6-110">Určete, které tvoří nebo chcete vytvořit obslužnou rutinu události pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="019c6-110">Determine which form or control you want to create an event handler for.</span></span>  
  
5.  <span data-ttu-id="019c6-111">V metodě v rámci třídy formuláře přidejte kód, který určuje chcete zpracovat událost obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="019c6-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="019c6-112">Například následující kód určuje obslužná rutina události `button1_Click` obslužné rutiny <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="019c6-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="019c6-113"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metoda jsme vám ukázali ve výše uvedeném kódu jazyka Visual Basic vytvoří obslužnou rutinu události kliknutí pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="019c6-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="019c6-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="019c6-114">See also</span></span>

- [<span data-ttu-id="019c6-115">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="019c6-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="019c6-116">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="019c6-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="019c6-117">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="019c6-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
