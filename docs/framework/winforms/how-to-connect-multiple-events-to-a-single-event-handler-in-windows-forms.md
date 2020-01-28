---
title: 'Postupy: připojení více událostí k jedné obslužné rutině události'
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
ms.openlocfilehash: 0591291522ab1da04fef90bf1c0a73cf33ba0518
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739605"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Postupy: Připojení více událostí k jedné obslužné rutině událostí ve Windows Forms
V návrhu aplikace může být nutné použít jednu obslužnou rutinu události pro více událostí nebo mít více událostí stejný postup. Například je často účinný časový okamžik, který má příkaz nabídky vyvolat stejnou událost jako tlačítko na formuláři, pokud vystavuje stejné funkce. To lze provést pomocí zobrazení událostí okno Vlastnosti v C# nebo pomocí klíčového slova `Handles` a rozevíracího seznamu název **třídy** a **názvu metody** v editoru kódu Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Připojení více událostí k jedné obslužné rutině události v Visual Basic  
  
1. Klikněte pravým tlačítkem na formulář a vyberte **Zobrazit kód**.  
  
2. Z rozevíracího seznamu **název třídy** vyberte jeden z ovládacích prvků, u kterých chcete obslužnou rutinu události zpracovat.  
  
3. V rozevíracím seznamu **název metody** vyberte jednu z událostí, které má obslužná rutina události zpracovat.  
  
4. Editor kódu vloží příslušnou obslužnou rutinu události a umístí kurzor do metody. V následujícím příkladu je to událost <xref:System.Windows.Forms.Control.Click> pro ovládací prvek <xref:System.Windows.Forms.Button>.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5. Přidejte další události, které chcete zpracovat, do klauzule `Handles`.  
  
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
