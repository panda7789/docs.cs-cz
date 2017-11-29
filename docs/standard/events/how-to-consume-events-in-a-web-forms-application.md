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
ms.openlocfilehash: bdb0a6be309f27348ba13bf93fd5aedd3c66a792
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Postupy: Příjem událostí v aplikaci Web Forms
Běžný scénář v aplikace webových formulářů ASP.NET je naplnit webovou stránku s ovládacími prvky a pak provést určité akce založené na který uživatel klikne na ovládací prvek. Například <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> prvek vyvolá událost, když uživatel klikne na webové stránce. Pomocí zpracování události, může aplikace provádět příslušné aplikační logiku pro dané kliknutí na tlačítko.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Zpracování události kliknutí na tlačítko na webové stránce  
  
1.  Vytvoření stránky webových formulářů ASP.NET (webová stránka), který má <xref:System.Web.UI.WebControls.Button> řízení s `OnClick` hodnota nastavena na název metody, který definujete v dalším kroku.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  Definování obslužné rutiny události, který odpovídá <xref:System.Web.UI.WebControls.Button.Click> podpisu delegáta události a že má název definovaný pro `OnClick` hodnotu.  
  
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
  
     <xref:System.Web.UI.WebControls.Button.Click> Událostí se používá <xref:System.EventHandler> třídy typu delegáta a <xref:System.EventArgs> třídu pro data události. Technologie ASP.NET automaticky generuje kód, který vytvoří instanci <xref:System.EventHandler> a přidá této instance delegáta <xref:System.Web.UI.WebControls.Button.Click> události <xref:System.Web.UI.WebControls.Button> instance.  
  
3.  Události metoda obslužné rutiny, který jste zadali v kroku 2, přidat kód a proveďte všechny akce, které jsou povinné, pokud dojde k události.  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../docs/standard/events/index.md)
