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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124783"
---
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Postupy: Příjem událostí v aplikaci Web Forms
Běžným scénářem v aplikacích webových formulářů ASP.NET je naplnění webové stránky ovládacími prvky a provedení konkrétní akce na základě ovládacího prvku, na který uživatel klikne. Například ovládací prvek <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> vyvolá událost, když na ni uživatel klikne na webové stránce. Zpracováním události aplikace může pro toto kliknutí na tlačítko provést příslušnou logiku aplikace.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Zpracování události kliknutí na tlačítko na webové stránce  
  
1. Vytvořte stránku webových formulářů ASP.NET (webová stránka), která má ovládací prvek <xref:System.Web.UI.WebControls.Button> s hodnotou `OnClick` nastavenou na název metody, kterou budete definovat v dalším kroku.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. Definujte obslužnou rutinu události, která odpovídá signatuře delegáta události <xref:System.Web.UI.WebControls.Button.Click> a která má název, který jste definovali pro hodnotu `OnClick`.  
  
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
  
     Událost <xref:System.Web.UI.WebControls.Button.Click> používá třídu <xref:System.EventHandler> pro typ delegáta a třídu <xref:System.EventArgs> pro data události. Rozhraní stránky ASP.NET automaticky generuje kód, který vytvoří instanci <xref:System.EventHandler> a přidá tuto instanci delegáta do události <xref:System.Web.UI.WebControls.Button.Click> instance <xref:System.Web.UI.WebControls.Button>.  
  
3. V metodě obslužné rutiny události, kterou jste definovali v kroku 2, přidejte kód, který provede všechny akce, které jsou požadovány, když dojde k události.  
  
## <a name="see-also"></a>Viz také:

- [Události](../../../docs/standard/events/index.md)
