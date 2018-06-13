---
title: 'Postupy: Připojení více událostí k jedné obslužné rutině událostí ve Windows Forms'
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
ms.openlocfilehash: 527a76376a4c1d5ad051f4768ca2bd42c3548b3d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538577"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Postupy: Připojení více událostí k jedné obslužné rutině událostí ve Windows Forms
Při návrhu aplikace možná bude nutné použít více událostí jedné obslužné rutině událostí nebo mít více událostí, použijte stejný postup. Je třeba často výkonné spoustu času tak, aby měl příkaz nabídky vyvolání stejné události, jak to dělá tlačítko ve formuláři, pokud jejich zpřístupnění stejné funkce. Můžete to provést pomocí zobrazení událostí okna vlastnosti v jazyce C# nebo `Handles` – klíčové slovo a **název třídy** a **název metody** rozevíracího seznamu polí v editoru kódu jazyka Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Připojení více událostí k jedné obslužné rutině událostí v jazyce Visual Basic  
  
1.  Klikněte pravým tlačítkem na formulář a zvolte **kód zobrazení**.  
  
2.  Z **název třídy** rozevíracího seznamu vyberte jednu z ovládacích prvků, které chcete mít obslužné rutiny události zpracovat.  
  
3.  Z **název metody** rozevíracího seznamu vyberte jednu z události, které chcete obslužné rutiny události pro zpracování.  
  
4.  Editor kódu vloží obslužné rutiny odpovídající události a umístění kurzoru v rámci metody. V následujícím příkladu je <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  Připojit ostatní události, které chcete využívá ke `Handles` klauzule.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  Přidejte příslušný kód do obslužné rutiny události.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Připojení více událostí k jedné obslužné rutině událostí v jazyce C#  
  
1.  Vyberte ovládací prvek, ke kterému se chcete připojit obslužné rutiny události.  
  
2.  V okně vlastností klikněte **události** tlačítko (![tlačítko události](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3.  Klikněte na název události, která chcete zpracovat.  
  
4.  V části hodnotu vedle názvu události klikněte na tlačítko rozevíracího seznamu můžete zobrazit seznam existujících obslužné rutiny, které odpovídají podpis metody události, kterou chcete zpracovat.  
  
5.  Obslužné rutiny události odpovídající vyberte ze seznamu.  
  
     Kód bude přidán do formuláře pro vazbu události pro stávající obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření obslužných rutin událostí ve Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
