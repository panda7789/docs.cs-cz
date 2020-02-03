---
title: 'Postupy: vytváření obslužných rutin událostí v době běhu'
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
ms.openlocfilehash: 0b496a3da77c5bcf7a08c435edba468a7c5809cb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739507"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="fff54-102">Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fff54-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>

<span data-ttu-id="fff54-103">Kromě vytváření událostí pomocí Návrhář formulářů v aplikaci Visual Studio můžete také vytvořit obslužnou rutinu události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="fff54-103">In addition to creating events using the Windows Forms Designer in Visual Studio, you can also create an event handler at run time.</span></span> <span data-ttu-id="fff54-104">Tato akce umožňuje připojit obslužné rutiny událostí na základě podmínek v kódu v době běhu, a to na rozdíl od jejich připojení při počátečním spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="fff54-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>

## <a name="create-an-event-handler-at-run-time"></a><span data-ttu-id="fff54-105">Vytvoření obslužné rutiny události v době běhu</span><span class="sxs-lookup"><span data-stu-id="fff54-105">Create an event handler at run time</span></span>

1. <span data-ttu-id="fff54-106">Otevřete formulář, do kterého chcete přidat obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="fff54-106">Open the form that you want to add an event handler to.</span></span>

2. <span data-ttu-id="fff54-107">Přidejte metodu do formuláře s podpisem metody pro událost, kterou chcete zpracovat.</span><span class="sxs-lookup"><span data-stu-id="fff54-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>

     <span data-ttu-id="fff54-108">Například pokud jste pracovali <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku, měli byste vytvořit metodu, například následující:</span><span class="sxs-lookup"><span data-stu-id="fff54-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>

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

3. <span data-ttu-id="fff54-109">Přidejte kód do obslužné rutiny události odpovídající vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fff54-109">Add code to the event handler as appropriate to your application.</span></span>

4. <span data-ttu-id="fff54-110">Určete, který formulář nebo ovládací prvek, pro který chcete vytvořit obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="fff54-110">Determine which form or control you want to create an event handler for.</span></span>

5. <span data-ttu-id="fff54-111">V metodě v rámci třídy formuláře přidejte kód, který určuje obslužnou rutinu události pro zpracování události.</span><span class="sxs-lookup"><span data-stu-id="fff54-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="fff54-112">Například následující kód určuje obslužnou rutinu události `button1_Click` zpracovává událost <xref:System.Windows.Forms.Control.Click> ovládacího prvku <xref:System.Windows.Forms.Button>:</span><span class="sxs-lookup"><span data-stu-id="fff54-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <span data-ttu-id="fff54-113">Metoda <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> znázorněná ve výše uvedeném kódu Visual Basic vytvoří obslužnou rutinu události Click pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="fff54-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>

## <a name="see-also"></a><span data-ttu-id="fff54-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="fff54-114">See also</span></span>

- [<span data-ttu-id="fff54-115">Vytváření obslužných rutin událostí ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fff54-115">Creating Event Handlers in Windows Forms</span></span>](creating-event-handlers-in-windows-forms.md)
- [<span data-ttu-id="fff54-116">Přehled obslužných rutin událostí</span><span class="sxs-lookup"><span data-stu-id="fff54-116">Event Handlers Overview</span></span>](event-handlers-overview-windows-forms.md)
- [<span data-ttu-id="fff54-117">Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fff54-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
