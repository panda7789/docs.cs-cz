---
title: 'Postupy: vytváření obslužných rutin událostí v době běhu'
description: Naučte se, jak vytvořit obslužnou rutinu události v době běhu pomocí Návrhář formulářů v aplikaci Visual Studio. Tato akce umožňuje připojit obslužné rutiny událostí v době běhu.
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
ms.openlocfilehash: 857076c46377b3276154d9b193d4bbe51841828f
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325800"
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a>Postupy: Vytváření obslužných rutin událostí v době běhu pro Windows Forms

Kromě vytváření událostí pomocí Návrhář formulářů v aplikaci Visual Studio můžete také vytvořit obslužnou rutinu události v době běhu. Tato akce umožňuje připojit obslužné rutiny událostí na základě podmínek v kódu v době běhu, a to na rozdíl od jejich připojení při počátečním spuštění programu.

## <a name="create-an-event-handler-at-run-time"></a>Vytvoření obslužné rutiny události v době běhu

1. Otevřete formulář, do kterého chcete přidat obslužnou rutinu události.

2. Přidejte metodu do formuláře s podpisem metody pro událost, kterou chcete zpracovat.

     Například pokud jste si vypracovali <xref:System.Windows.Forms.Control.Click> událost <xref:System.Windows.Forms.Button> ovládacího prvku, měli byste vytvořit metodu, například následující:

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

5. V metodě v rámci třídy formuláře přidejte kód, který určuje obslužnou rutinu události pro zpracování události. Například následující kód určuje obslužnou rutinu události, která `button1_Click` zpracovává <xref:System.Windows.Forms.Control.Click> událost <xref:System.Windows.Forms.Button> ovládacího prvku:

    ```vb
    AddHandler Button1.Click, AddressOf Button1_Click
    ```

    ```csharp
    button1.Click += new EventHandler(button1_Click);
    ```

    ```cpp
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);
    ```

     <xref:System.ComponentModel.EventHandlerList.AddHandler%2A>Metoda znázorněná ve výše uvedeném kódu Visual Basic pro tlačítko vytvoří obslužnou rutinu události kliknutí.

## <a name="see-also"></a>Viz také

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md)
- [Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic](../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
