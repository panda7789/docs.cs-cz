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
ms.openlocfilehash: 1f95fd0dcc12f2d4e47ee07e1e6bb15d91000f0f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124783"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="43f9f-102">Postupy: Příjem událostí v aplikaci Web Forms</span><span class="sxs-lookup"><span data-stu-id="43f9f-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="43f9f-103">Běžným scénářem v aplikacích ASP.NET webových formulářů je naplnění webové stránky ovládacími prvky a následné provedení určité akce založené na ovládacím prvku, na který uživatel klepne.</span><span class="sxs-lookup"><span data-stu-id="43f9f-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="43f9f-104"><xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> Ovládací prvek například vyvolá událost, když na něj uživatel klepne na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="43f9f-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="43f9f-105">Zpracováním události aplikace můžete provést příslušnou aplikační logiku pro toto tlačítko kliknutí.</span><span class="sxs-lookup"><span data-stu-id="43f9f-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="43f9f-106">Zpracování události kliknutí na tlačítko na webové stránce</span><span class="sxs-lookup"><span data-stu-id="43f9f-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="43f9f-107">Vytvořte ASP.NET webovou webovou stránku <xref:System.Web.UI.WebControls.Button> (webovou stránku), která má ovládací prvek s `OnClick` hodnotou nastavenou na název metody, kterou definujete v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="43f9f-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="43f9f-108">Definujte obslužnou rutinu události, která odpovídá <xref:System.Web.UI.WebControls.Button.Click> `OnClick` podpisu delegáta události a která má název definovaný pro hodnotu.</span><span class="sxs-lookup"><span data-stu-id="43f9f-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="43f9f-109">Událost <xref:System.Web.UI.WebControls.Button.Click> používá <xref:System.EventHandler> třídu pro typ <xref:System.EventArgs> delegáta a třídu pro data události.</span><span class="sxs-lookup"><span data-stu-id="43f9f-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="43f9f-110">Rozhraní ASP.NET stránky automaticky generuje kód, <xref:System.EventHandler> který vytvoří instanci <xref:System.Web.UI.WebControls.Button.Click> a <xref:System.Web.UI.WebControls.Button> přidá tuto instanci delegáta k události instance.</span><span class="sxs-lookup"><span data-stu-id="43f9f-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="43f9f-111">V metodě obslužné rutiny události, kterou jste definovali v kroku 2, přidejte kód k provedení všech akcí, které jsou požadovány, když dojde k události.</span><span class="sxs-lookup"><span data-stu-id="43f9f-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f9f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="43f9f-112">See also</span></span>

- [<span data-ttu-id="43f9f-113">Akce</span><span class="sxs-lookup"><span data-stu-id="43f9f-113">Events</span></span>](../../../docs/standard/events/index.md)
