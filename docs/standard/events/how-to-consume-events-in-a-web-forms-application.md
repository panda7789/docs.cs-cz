---
title: 'Postupy: Příjem událostí v aplikaci Web Forms'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- events [.NET Framework], Web Forms
- Web Forms controls, and events
- event handlers [.NET Framework], Web Forms
- events [.NET Framework], consuming
- Web Forms, event handling
ms.assetid: 73bf8638-c4ec-4069-b0bb-a1dc79b92e32
ms.openlocfilehash: 3490b6fb89bfe6d7ac778078f58381bb5172e2fe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288482"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="5105d-102">Postupy: Příjem událostí v aplikaci Web Forms</span><span class="sxs-lookup"><span data-stu-id="5105d-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="5105d-103">Běžným scénářem v aplikacích webových formulářů ASP.NET je naplnění webové stránky ovládacími prvky a provedení konkrétní akce na základě ovládacího prvku, na který uživatel klikne.</span><span class="sxs-lookup"><span data-stu-id="5105d-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="5105d-104"><xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType>Ovládací prvek například vyvolá událost, když na ni uživatel klikne na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="5105d-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="5105d-105">Zpracováním události aplikace může pro toto kliknutí na tlačítko provést příslušnou logiku aplikace.</span><span class="sxs-lookup"><span data-stu-id="5105d-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="5105d-106">Zpracování události kliknutí na tlačítko na webové stránce</span><span class="sxs-lookup"><span data-stu-id="5105d-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="5105d-107">Vytvořte stránku webových formulářů ASP.NET (webová stránka), která má <xref:System.Web.UI.WebControls.Button> ovládací prvek s `OnClick` hodnotou nastavenou na název metody, kterou budete definovat v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="5105d-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="5105d-108">Definujte obslužnou rutinu události, která odpovídá <xref:System.Web.UI.WebControls.Button.Click> podpisu delegáta události a která má název, který jste definovali pro `OnClick` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5105d-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
    ```csharp  
    protected void Button1_Click(object sender, EventArgs e)  
    {  
        // perform action  
    }  
    ```  
  
    ```vb  
    Protected Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' perform action  
    End Sub  
    ```  
  
     <span data-ttu-id="5105d-109"><xref:System.Web.UI.WebControls.Button.Click>Událost používá <xref:System.EventHandler> třídu pro typ delegáta a <xref:System.EventArgs> třídu pro data události.</span><span class="sxs-lookup"><span data-stu-id="5105d-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="5105d-110">Rozhraní stránky ASP.NET automaticky generuje kód, který vytvoří instanci <xref:System.EventHandler> a přidá tuto instanci delegáta do <xref:System.Web.UI.WebControls.Button.Click> události <xref:System.Web.UI.WebControls.Button> instance.</span><span class="sxs-lookup"><span data-stu-id="5105d-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="5105d-111">V metodě obslužné rutiny události, kterou jste definovali v kroku 2, přidejte kód, který provede všechny akce, které jsou požadovány, když dojde k události.</span><span class="sxs-lookup"><span data-stu-id="5105d-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5105d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="5105d-112">See also</span></span>

- [<span data-ttu-id="5105d-113">Události</span><span class="sxs-lookup"><span data-stu-id="5105d-113">Events</span></span>](index.md)
