---
title: "Přehled obslužných rutin událostí (Windows Forms)"
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
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a>Přehled obslužných rutin událostí (Windows Forms)
Obslužné rutiny události je metoda, která je vázána k události. Když je vyvolána událost, spuštění kódu v rámci obslužné rutiny události. Každý obslužná rutina události poskytuje dva parametry, které vám umožní správně zpracovat událost. Následující příklad ukazuje obslužné rutiny události pro <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> událostí.  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 První parametr`sender`, poskytuje odkaz na objekt, který vyvolá událost. Druhý parametr `e`, v uvedeném příkladu předá objekt konkrétní událost, která se právě zpracovává. Pod položkou vlastností objektu (a v některých případech její metody), můžete získat informace o umístění myši pro události myši nebo dat přenášených v události přetažení myší.  
  
 Všechny události obvykle vytvoří obslužnou rutinu události s typem jiný objekt události pro druhý parametr. Některé obslužné rutiny událostí, například <xref:System.Windows.Forms.Control.MouseDown> a <xref:System.Windows.Forms.Control.MouseUp> události, mají stejný typ objektu pro jejich druhý parametr. Pro tyto typy událostí, které můžete použít stejné obslužné rutiny události ke zpracování obou událostí.  
  
 Můžete také stejné obslužné rutiny události ke zpracování stejné události pro různé ovládací prvky. Například, pokud máte skupinu <xref:System.Windows.Forms.RadioButton> ovládací prvky ve formuláři, můžete vytvořit obslužnou rutinu pro jednu událost <xref:System.Windows.Forms.Control.Click> událostí a mít každý ovládací prvek <xref:System.Windows.Forms.Control.Click> událost vázána jedné obslužné rutině událostí. Další informace najdete v tématu [postupy: připojení více událostí k jedné obslužné rutině událostí ve Windows Forms](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Viz také  
 [Vytváření obslužných rutin událostí v systému Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Přehled událostí](../../../docs/framework/winforms/events-overview-windows-forms.md)
