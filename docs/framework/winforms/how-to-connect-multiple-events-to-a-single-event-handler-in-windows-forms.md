---
title: 'Postupy: Připojení více událostí jedné obslužné rutině událostí ve Windows Forms'
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
ms.openlocfilehash: 869ef0d7717ca64209bc61c2ae22ce929edcec5e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967864"
---
# <a name="how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms"></a>Postupy: Připojení více událostí jedné obslužné rutině událostí ve Windows Forms
V návrhu aplikace možná bude nutné použít jedné obslužné rutině událostí pro více událostí nebo mít více událostí, použijte stejný postup. Je například často výkonné spoustu času mít příkaz nabídky vyvolat stejnou událost, stejně jako tlačítko na formuláři pokud zveřejňovaly stejné funkce. Můžete to provést pomocí zobrazení události v okně Vlastnosti v C# nebo pomocí `Handles` – klíčové slovo a **název třídy** a **název metody** rozevírací seznamy v editoru kódu jazyka Visual Basic.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-visual-basic"></a>Připojení více událostí k obslužné rutině jedné události v jazyce Visual Basic  
  
1.  Klikněte pravým tlačítkem na formuláři a zvolte **zobrazit kód**.  
  
2.  Z **název třídy** rozevíracího seznamu vyberte jednu z ovládacích prvků, které chcete mít obslužná rutina události zpracovávají.  
  
3.  Z **název metody** rozevíracího seznamu vyberte jednu z událostí, které chcete, aby obslužná rutina události pro zpracování.  
  
4.  Editor kódu vloží obslužná rutina odpovídající události a umístí kurzor do metody. V následujícím příkladu je <xref:System.Windows.Forms.Control.Click> události <xref:System.Windows.Forms.Button> ovládacího prvku.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
5.  Přidat další události byste chtěli ke zpracování `Handles` klauzuli.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click, Button2.Click  
    ' Add event-handler code here.  
    End Sub  
    ```  
  
6.  Přidáte odpovídající kód do obslužné rutiny události.  
  
### <a name="to-connect-multiple-events-to-a-single-event-handler-in-c"></a>Připojení více událostí k obslužné rutině jedné události v jazyce C\#
  
1.  Vyberte ovládací prvek, ke kterému chcete připojit obslužné rutiny události.  
  
2.  V okně Vlastnosti klikněte na tlačítko **události** tlačítko (![tlačítko události](../../../docs/framework/winforms/media/vxeventsbutton-propertieswindow.png "vxEventsButton_PropertiesWindow")).  
  
3.  Klikněte na název události, ke které chcete zpracovat.  
  
4.  V části Hodnota vedle názvu události klikněte na tlačítko rozevíracího seznamu zobrazíte seznam existujících, které odpovídají podpis metody, kterou chcete zpracovat událost obslužné rutiny událostí.  
  
5.  Obslužná rutina události odpovídající vyberte ze seznamu.  
  
     Kód bude přidán do formuláře pro vazbu události do existující obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:
- [Vytváření obslužných rutin událostí ve Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
- [Přehled obslužných rutin událostí](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)
