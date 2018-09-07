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
ms.openlocfilehash: c03ab0e1d493d9669f1e3821393d41d1c1b89867
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44063625"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Postupy: Příjem událostí v aplikaci Web Forms
Běžný scénář v aplikace webových formulářů ASP.NET má naplnit webovou stránku s ovládacími prvky a pak provést konkrétní akce, podle kterého ovládacího prvku uživatel klikne. Například <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> ovládací prvek vyvolá událost, když uživatel klikne na webové stránce. Díky zpracování události, vaše aplikace může provádět příslušné aplikace logiky pro dané kliknutí na tlačítko.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Zpracování události kliknutí na tlačítko na webové stránce  
  
1.  Vytvoření stránky s webovými formuláři ASP.NET (webová stránka), který má <xref:System.Web.UI.WebControls.Button> ovládacím prvkem `OnClick` hodnotu nastavte na název metody, která budou definovat v dalším kroku.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2.  Definování obslužné rutiny události, která odpovídá <xref:System.Web.UI.WebControls.Button.Click> signatura delegáta události a, který má název definovaný pro `OnClick` hodnotu.  
  
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
  
     <xref:System.Web.UI.WebControls.Button.Click> Událost používá <xref:System.EventHandler> třídy pro typ delegáta a <xref:System.EventArgs> třídu pro data události. Rámec stránky ASP.NET automaticky generuje kód, který vytvoří instanci <xref:System.EventHandler> a přidá tuto instanci delegáta k <xref:System.Web.UI.WebControls.Button.Click> událost <xref:System.Web.UI.WebControls.Button> instance.  
  
3.  V případě obslužné metody, která jste definovali v kroku 2, přidejte kód k provedení nějaké akce, které jsou potřeba při výskytu události.  
  
## <a name="see-also"></a>Viz také:

- [Události](../../../docs/standard/events/index.md)
