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
ms.openlocfilehash: 440086bfd5384fc46aec2997dbdd9937f7a1b65f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964322"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="db440-102">Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db440-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="db440-103">Kromě vytváření událostí pomocí Návrhář formulářů v aplikaci Visual Studio můžete také vytvořit obslužnou rutinu události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="db440-103">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="db440-104">Tato akce umožňuje připojit obslužné rutiny událostí na základě podmínek v kódu v době běhu, a to na rozdíl od jejich připojení při počátečním spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="db440-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="db440-105">Vytvoření obslužné rutiny události v době běhu</span><span class="sxs-lookup"><span data-stu-id="db440-105">Create an event handler at run time</span></span>

1. <span data-ttu-id="db440-106">Otevřete formulář, do kterého chcete přidat obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="db440-106">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="db440-107">Přidejte metodu do formuláře s podpisem metody pro událost, kterou chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="db440-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="db440-108">Například pokud jste si vypracovali <xref:System.Windows.Forms.Control.Click> událost <xref:System.Windows.Forms.Button> ovládacího prvku, měli byste vytvořit metodu, například následující:</span><span class="sxs-lookup"><span data-stu-id="db440-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

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

3. <span data-ttu-id="db440-109">Přidejte kód do obslužné rutiny události odpovídající vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="db440-109">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="db440-110">Určete, který formulář nebo ovládací prvek, pro který chcete vytvořit obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="db440-110">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="db440-111">V metodě v rámci třídy formuláře přidejte kód, který určuje obslužnou rutinu události pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="db440-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="db440-112">Například následující kód určuje obslužnou rutinu `button1_Click` události, která <xref:System.Windows.Forms.Control.Click> zpracovává událost <xref:System.Windows.Forms.Button> ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="db440-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="db440-113"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metoda znázorněná ve výše uvedeném kódu Visual Basic pro tlačítko vytvoří obslužnou rutinu události kliknutí.</span><span class="sxs-lookup"><span data-stu-id="db440-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="db440-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db440-114">See also</span></span>

- [<span data-ttu-id="db440-115">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="db440-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="db440-116">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="db440-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="db440-117">Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db440-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
