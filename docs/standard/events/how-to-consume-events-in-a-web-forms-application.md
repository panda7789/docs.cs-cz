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
# <a name="how-to-consume-events-in-a-web-forms-application"></a>Postupy: Příjem událostí v aplikaci Web Forms
Běžným scénářem v aplikacích ASP.NET webových formulářů je naplnění webové stránky ovládacími prvky a následné provedení určité akce založené na ovládacím prvku, na který uživatel klepne. <xref:System.Web.UI.WebControls.Button?displayProperty=nameWithType> Ovládací prvek například vyvolá událost, když na něj uživatel klepne na webové stránce. Zpracováním události aplikace můžete provést příslušnou aplikační logiku pro toto tlačítko kliknutí.  
  
### <a name="to-handle-a-button-click-event-on-a-webpage"></a>Zpracování události kliknutí na tlačítko na webové stránce  
  
1. Vytvořte ASP.NET webovou webovou stránku <xref:System.Web.UI.WebControls.Button> (webovou stránku), která má ovládací prvek s `OnClick` hodnotou nastavenou na název metody, kterou definujete v dalším kroku.  
  
    ```xml  
    <asp:Button ID="Button1" runat="server" Text="Click Me" OnClick="Button1_Click" />  
    ```  
  
2. Definujte obslužnou rutinu události, která odpovídá <xref:System.Web.UI.WebControls.Button.Click> `OnClick` podpisu delegáta události a která má název definovaný pro hodnotu.  
  
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
  
     Událost <xref:System.Web.UI.WebControls.Button.Click> používá <xref:System.EventHandler> třídu pro typ <xref:System.EventArgs> delegáta a třídu pro data události. Rozhraní ASP.NET stránky automaticky generuje kód, <xref:System.EventHandler> který vytvoří instanci <xref:System.Web.UI.WebControls.Button.Click> a <xref:System.Web.UI.WebControls.Button> přidá tuto instanci delegáta k události instance.  
  
3. V metodě obslužné rutiny události, kterou jste definovali v kroku 2, přidejte kód k provedení všech akcí, které jsou požadovány, když dojde k události.  
  
## <a name="see-also"></a>Viz také

- [Akce](../../../docs/standard/events/index.md)
