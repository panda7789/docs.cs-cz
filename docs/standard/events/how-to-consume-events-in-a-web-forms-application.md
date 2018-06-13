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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b8af7b3894c010d5a7a4c712efe2458a6bb2a50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571069"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="685b7-102">Postupy: Příjem událostí v aplikaci Web Forms</span><span class="sxs-lookup"><span data-stu-id="685b7-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="685b7-103">Běžný scénář v aplikace webových formulářů ASP.NET je naplnit webovou stránku s ovládacími prvky a pak provést určité akce založené na který uživatel klikne na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="685b7-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="685b7-104">Například <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> prvek vyvolá událost, když uživatel klikne na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="685b7-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="685b7-105">Pomocí zpracování události, může aplikace provádět příslušné aplikační logiku pro dané kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="685b7-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="685b7-106">Zpracování události kliknutí na tlačítko na webové stránce</span><span class="sxs-lookup"><span data-stu-id="685b7-106">To handle a button click event on a webpage</span></span>  
  
1.  <span data-ttu-id="685b7-107">Vytvoření stránky webových formulářů ASP.NET (webová stránka), který má <xref:System.Web.UI.WebControls.Button> řízení s `OnClick` hodnota nastavena na název metody, který definujete v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="685b7-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  <span data-ttu-id="685b7-108">Definování obslužné rutiny události, který odpovídá <xref:System.Web.UI.WebControls.Button.Click> podpisu delegáta události a že má název definovaný pro `OnClick` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="685b7-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="685b7-109"><xref:System.Web.UI.WebControls.Button.Click> Událostí se používá <xref:System.EventHandler> třídy typu delegáta a <xref:System.EventArgs> třídu pro data události.</span><span class="sxs-lookup"><span data-stu-id="685b7-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="685b7-110">Technologie ASP.NET automaticky generuje kód, který vytvoří instanci <xref:System.EventHandler> a přidá této instance delegáta <xref:System.Web.UI.WebControls.Button.Click> události <xref:System.Web.UI.WebControls.Button> instance.</span><span class="sxs-lookup"><span data-stu-id="685b7-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3.  <span data-ttu-id="685b7-111">Události metoda obslužné rutiny, který jste zadali v kroku 2, přidat kód a proveďte všechny akce, které jsou povinné, pokud dojde k události.</span><span class="sxs-lookup"><span data-stu-id="685b7-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="685b7-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="685b7-112">See Also</span></span>  
 [<span data-ttu-id="685b7-113">Události</span><span class="sxs-lookup"><span data-stu-id="685b7-113">Events</span></span>](../../../docs/standard/events/index.md)
