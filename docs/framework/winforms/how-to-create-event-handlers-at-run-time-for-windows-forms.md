---
title: 'Postupy: vytváření obslužných rutin událostí v době běhu'
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
ms.openlocfilehash: 0b496a3da77c5bcf7a08c435edba468a7c5809cb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739507"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms

Kromě vytváření událostí pomocí Návrhář formulářů v aplikaci Visual Studio můžete také vytvořit obslužnou rutinu události v době běhu. Tato akce umožňuje připojit obslužné rutiny událostí na základě podmínek v kódu v době běhu, a to na rozdíl od jejich připojení při počátečním spuštění programu.

## <a name="create-an-event-handler-at-run-time"></a>Vytvoření obslužné rutiny události v době běhu

1. Otevřete formulář, do kterého chcete přidat obslužnou rutinu události.

2. Přidejte metodu do formuláře s podpisem metody pro událost, kterou chcete zpracovat.

     Například pokud jste pracovali <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku, měli byste vytvořit metodu, například následující:

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

3. Přidejte kód do obslužné rutiny události odpovídající vaší aplikaci.

4. Určete, který formulář nebo ovládací prvek, pro který chcete vytvořit obslužnou rutinu události.

5. V metodě v rámci třídy formuláře přidejte kód, který určuje obslužnou rutinu události pro zpracování události. Například následující kód určuje obslužnou rutinu události `button1_Click` zpracovává událost <xref:System.Windows.Forms.Control.Click> ovládacího prvku <xref:System.Windows.Forms.Button>:

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     Metoda <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> znázorněná ve výše uvedeném kódu Visual Basic vytvoří obslužnou rutinu události Click pro tlačítko.

## <a name="see-also"></a>Viz také

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md)
- [Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
