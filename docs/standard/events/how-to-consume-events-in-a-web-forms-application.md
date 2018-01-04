---
title: "Postupy: Příjem událostí v aplikaci Web Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d0fec2ed34968bfa8c296f08739dec28e6a6eab9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="01db4-102">Postupy: Příjem událostí v aplikaci Web Forms</span><span class="sxs-lookup"><span data-stu-id="01db4-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="01db4-103">Běžný scénář v aplikace webových formulářů ASP.NET je naplnit webovou stránku s ovládacími prvky a pak provést určité akce založené na který uživatel klikne na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="01db4-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="01db4-104">Například <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> prvek vyvolá událost, když uživatel klikne na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="01db4-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="01db4-105">Pomocí zpracování události, může aplikace provádět příslušné aplikační logiku pro dané kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="01db4-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="01db4-106">Zpracování události kliknutí na tlačítko na webové stránce</span><span class="sxs-lookup"><span data-stu-id="01db4-106">To handle a button click event on a webpage</span></span>  
  
1.  <span data-ttu-id="01db4-107">Vytvoření stránky webových formulářů ASP.NET (webová stránka), který má <xref:System.Web.UI.WebControls.Button> řízení s `OnClick` hodnota nastavena na název metody, který definujete v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="01db4-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  <span data-ttu-id="01db4-108">Definování obslužné rutiny události, který odpovídá <xref:System.Web.UI.WebControls.Button.Click> podpisu delegáta události a že má název definovaný pro `OnClick` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01db4-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="01db4-109"><xref:System.Web.UI.WebControls.Button.Click> Událostí se používá <xref:System.EventHandler> třídy typu delegáta a <xref:System.EventArgs> třídu pro data události.</span><span class="sxs-lookup"><span data-stu-id="01db4-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="01db4-110">Technologie ASP.NET automaticky generuje kód, který vytvoří instanci <xref:System.EventHandler> a přidá této instance delegáta <xref:System.Web.UI.WebControls.Button.Click> události <xref:System.Web.UI.WebControls.Button> instance.</span><span class="sxs-lookup"><span data-stu-id="01db4-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3.  <span data-ttu-id="01db4-111">Události metoda obslužné rutiny, který jste zadali v kroku 2, přidat kód a proveďte všechny akce, které jsou povinné, pokud dojde k události.</span><span class="sxs-lookup"><span data-stu-id="01db4-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01db4-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="01db4-112">See Also</span></span>  
 [<span data-ttu-id="01db4-113">Události</span><span class="sxs-lookup"><span data-stu-id="01db4-113">Events</span></span>](../../../docs/standard/events/index.md)
