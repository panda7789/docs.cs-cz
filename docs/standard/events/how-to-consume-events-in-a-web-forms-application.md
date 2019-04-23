---
title: 'Postupy: Zpracování událostí v aplikaci Web Forms'
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
ms.openlocfilehash: dc1dee9377200e4c9fd575b8dcd00982db45f249
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317808"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a><span data-ttu-id="0609b-102">Postupy: Zpracování událostí v aplikaci Web Forms</span><span class="sxs-lookup"><span data-stu-id="0609b-102">How to: Consume Events in a Web Forms Application</span></span>
<span data-ttu-id="0609b-103">Běžný scénář v aplikace webových formulářů ASP.NET má naplnit webovou stránku s ovládacími prvky a pak provést konkrétní akce, podle kterého ovládacího prvku uživatel klikne.</span><span class="sxs-lookup"><span data-stu-id="0609b-103">A common scenario in ASP.NET Web Forms applications is to populate a webpage with controls, and then perform a specific action based on which control the user clicks.</span></span> <span data-ttu-id="0609b-104">Například <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> ovládací prvek vyvolá událost, když uživatel klikne na webové stránce.</span><span class="sxs-lookup"><span data-stu-id="0609b-104">For example, a <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> control raises an event when the user clicks it in the webpage.</span></span> <span data-ttu-id="0609b-105">Díky zpracování události, vaše aplikace může provádět příslušné aplikace logiky pro dané kliknutí na tlačítko.</span><span class="sxs-lookup"><span data-stu-id="0609b-105">By handling the event, your application can perform the appropriate application logic for that button click.</span></span>  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a><span data-ttu-id="0609b-106">Zpracování události kliknutí na tlačítko na webové stránce</span><span class="sxs-lookup"><span data-stu-id="0609b-106">To handle a button click event on a webpage</span></span>  
  
1. <span data-ttu-id="0609b-107">Vytvoření stránky s webovými formuláři ASP.NET (webová stránka), který má <xref:System.Web.UI.WebControls.Button> ovládacím prvkem `OnClick` hodnotu nastavte na název metody, která budou definovat v dalším kroku.</span><span class="sxs-lookup"><span data-stu-id="0609b-107">Create a ASP.NET Web Forms page (webpage) that has a <xref:System.Web.UI.WebControls.Button> control with the `OnClick` value set to the name of method that you will define in the next step.</span></span>  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. <span data-ttu-id="0609b-108">Definování obslužné rutiny události, která odpovídá <xref:System.Web.UI.WebControls.Button.Click> signatura delegáta události a, který má název definovaný pro `OnClick` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0609b-108">Define an event handler that matches the <xref:System.Web.UI.WebControls.Button.Click> event delegate signature and that has the name you defined for the `OnClick` value.</span></span>  
  
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
  
     <span data-ttu-id="0609b-109"><xref:System.Web.UI.WebControls.Button.Click> Událost používá <xref:System.EventHandler> třídy pro typ delegáta a <xref:System.EventArgs> třídu pro data události.</span><span class="sxs-lookup"><span data-stu-id="0609b-109">The <xref:System.Web.UI.WebControls.Button.Click> event uses the <xref:System.EventHandler> class for the delegate type and the <xref:System.EventArgs> class for the event data.</span></span> <span data-ttu-id="0609b-110">Rámec stránky ASP.NET automaticky generuje kód, který vytvoří instanci <xref:System.EventHandler> a přidá tuto instanci delegáta k <xref:System.Web.UI.WebControls.Button.Click> událost <xref:System.Web.UI.WebControls.Button> instance.</span><span class="sxs-lookup"><span data-stu-id="0609b-110">The ASP.NET page framework automatically generates code that creates an instance of <xref:System.EventHandler> and adds this delegate instance to the <xref:System.Web.UI.WebControls.Button.Click> event of the <xref:System.Web.UI.WebControls.Button> instance.</span></span>  
  
3. <span data-ttu-id="0609b-111">V případě obslužné metody, která jste definovali v kroku 2, přidejte kód k provedení nějaké akce, které jsou potřeba při výskytu události.</span><span class="sxs-lookup"><span data-stu-id="0609b-111">In the event handler method that you defined in step 2, add code to perform any actions that are required when the event occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0609b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0609b-112">See also</span></span>

- [<span data-ttu-id="0609b-113">Události</span><span class="sxs-lookup"><span data-stu-id="0609b-113">Events</span></span>](../../../docs/standard/events/index.md)
