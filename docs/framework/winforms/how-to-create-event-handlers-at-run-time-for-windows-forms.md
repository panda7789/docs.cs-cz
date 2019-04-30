---
title: 'Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms'
ms.date: 03/30/2017
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
ms.openlocfilehash: 09f090c6267093e3ad59266d8c77ea13b13b63d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801573"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms
Kromě vytváření událostí pomocí Návrháře formulářů Windows, můžete také vytvořit obslužnou rutinu události v době běhu. Tato akce umožňuje připojit obslužné rutiny události na základě podmínek v kódu v době běhu na rozdíl od toho připojení při počátečním spuštění programu.  
  
### <a name="to-create-an-event-handler-at-run-time"></a>Chcete-li vytvořit obslužnou rutinu události v době běhu  
  
1. Otevřete v editoru kódu, který chcete přidat obslužnou rutinu události pro formulář.  
  
2. Přidání metody do svého formuláře s podpis metody pro události, ke které chcete zpracovat.  
  
     Například, pokud byly zpracování <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku, vytvořili byste metodu, jako je následující:  
  
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
  
3. Přidejte kód do obslužné rutiny události jako vhodné pro vaši aplikaci.  
  
4. Určete, které tvoří nebo chcete vytvořit obslužnou rutinu události pro ovládací prvek.  
  
5. V metodě v rámci třídy formuláře přidejte kód, který určuje chcete zpracovat událost obslužné rutiny události. Například následující kód určuje obslužná rutina události `button1_Click` obslužné rutiny <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku:  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metoda jsme vám ukázali ve výše uvedeném kódu jazyka Visual Basic vytvoří obslužnou rutinu události kliknutí pro tlačítko.  
  
## <a name="see-also"></a>Viz také:

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md)
- [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
