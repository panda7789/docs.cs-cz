---
title: "Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53664bcf8c776338399297687a16ec430bca128b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms
Kromě vytváření událostí pomocí Návrhář formulářů Windows, můžete také vytvořit obslužnou rutinu události za běhu. Tato akce umožňuje připojit obslužné rutiny událostí na základě podmínek v kódu v době běhu rozdíl od toho, aby připojení při počátečním spuštění programu.  
  
### <a name="to-create-an-event-handler-at-run-time"></a>Pro vytvoření obslužné rutiny událostí v době běhu  
  
1.  Otevřete v editoru kódu, kterou chcete přidat obslužné rutiny události pro formulář.  
  
2.  Přidání metody do svého formuláře s podpis metody pro událost, která chcete zpracovat.  
  
     Například, pokud byly zpracování <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> řízení, by vytvoření metody, jako jsou následující:  
  
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
  
3.  Přidejte kód pro obslužnou rutinu události v závislosti na vaší aplikace.  
  
4.  Určí, které tvoří nebo chcete vytvořit obslužnou rutinu události pro ovládací prvek.  
  
5.  Metoda v rámci svého formuláře třídy přidejte kód, který určuje obslužné rutiny události ke zpracování události. Například následující kód určuje obslužné rutiny události `button1_Click` obslužné rutiny <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku:  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metoda ukázán ve výše uvedeném kódu jazyka Visual Basic vytvoří obslužnou rutinu události kliknutí na tlačítko o velikosti.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření obslužných rutin událostí v systému Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
