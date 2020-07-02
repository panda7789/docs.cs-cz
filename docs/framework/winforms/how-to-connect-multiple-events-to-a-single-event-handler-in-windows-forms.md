---
title: 'Postupy: připojení více událostí k jedné obslužné rutině události'
description: Naučte se, jak připojit více událostí k jedné obslužné rutině události v model Windows Forms pomocí zobrazení událostí okno Vlastnosti v C#.
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- events [Windows Forms], connecting multiple to single event handler
- event handlers [Windows Forms], connecting events to
- menus [Windows Forms], event-handling methods for multiple menu items
- Windows Forms controls, events
- menu items [Windows Forms], multicasting event-handling methods
ms.assetid: 5a20749a-41b5-4acc-8eb1-9e5040b0a2c4
ms.openlocfilehash: cca85c223b46d9a82dbc3e34e3377fb83c075959
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621883"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Postupy: Připojení více událostí k jedné obslužné rutině událostí ve Windows Forms
V návrhu aplikace může být nutné použít jednu obslužnou rutinu události pro více událostí nebo mít více událostí stejný postup. Například je často účinný časový okamžik, který má příkaz nabídky vyvolat stejnou událost jako tlačítko na formuláři, pokud vystavuje stejné funkce. Můžete to provést pomocí zobrazení událostí okno Vlastnosti v C# nebo pomocí `Handles` rozevíracích seznamů název **třídy** a názvu **metody** v editoru kódu Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Připojení více událostí k jedné obslužné rutině události v Visual Basic  
  
1. Klikněte pravým tlačítkem na formulář a vyberte **Zobrazit kód**.  
  
2. Z rozevíracího seznamu **název třídy** vyberte jeden z ovládacích prvků, u kterých chcete obslužnou rutinu události zpracovat.  
  
3. V rozevíracím seznamu **název metody** vyberte jednu z událostí, které má obslužná rutina události zpracovat.  
  
4. Editor kódu vloží příslušnou obslužnou rutinu události a umístí kurzor do metody. V následujícím příkladu je to <xref:System.Windows.Forms.Control.Click> událost <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. Do klauzule přidejte další události, které byste chtěli zpracovat `Handles` .  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6. Přidejte příslušný kód do obslužné rutiny události.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Připojení více událostí k jedné obslužné rutině události v jazyce C\#
  
1. Vyberte ovládací prvek, ke kterému chcete připojit obslužnou rutinu události.  
  
2. V okno Vlastnosti klikněte na tlačítko **události** (![tlačítko události](./media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3. Klikněte na název události, kterou chcete zpracovat.  
  
4. V části hodnota vedle názvu události klikněte na tlačítko rozevíracího seznamu a zobrazí se seznam existujících obslužných rutin událostí, které odpovídají podpisu metody události, kterou chcete zpracovat.  
  
5. V seznamu vyberte příslušnou obslužnou rutinu události.  
  
     Kód se přidá do formuláře, aby se událost navázala na existující obslužnou rutinu události.  
  
## <a name="see-also"></a>Viz také:

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled obslužných rutin událostí](event-handlers-overview-windows-forms.md)
