---
title: Přehled obslužných rutin událostí (Windows Forms)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 05acbfaf427060d015c2445360a7d73ebe97d070
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186079"
---
# <a name="event-handlers-overview-windows-forms"></a>Přehled obslužných rutin událostí (Windows Forms)
Obslužná rutina události je metoda, která je vázána na událost. Když se vyvolá událost, je proveden kód v obslužné rutině události. Každá obslužná rutina události poskytuje dva parametry, které umožňují zpracovat událost správně. Následující příklad ukazuje obslužná rutina události <xref:System.Windows.Forms.Button> ovládacího prvku <xref:System.Windows.Forms.Control.Click> událostí.  
  
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
  
 První parametr`sender`, poskytuje odkaz na objekt, který vyvolal událost. Druhý parametr `e`, v příkladu výše, předá objekt konkrétní událost, která se právě zpracovává. Pomocí odkazu na vlastnosti objektu (a v některých případech její metody), můžete získat informace, jako je poloha myši pro události myši nebo dat přenášených v událostech a přetažení.  
  
 Každá událost obvykle vytvoří obslužnou rutinu události s typem objektu na různé události pro druhý parametr. Některé obslužné rutiny událostí, třeba kroky týkající <xref:System.Windows.Forms.Control.MouseDown> a <xref:System.Windows.Forms.Control.MouseUp> události, mají stejný typ objektu pro jejich druhý parametr. Pro tyto typy událostí, které můžete použít stejný ovladač událostí zpracování obou událostí.  
  
 Stejný ovladač událostí můžete použít také pro zpracování stejné události pro různé ovládací prvky. Například, pokud máte skupinu <xref:System.Windows.Forms.RadioButton> ovládací prvky ve formuláři, můžete vytvořit obslužnou rutinu pro jednu událost <xref:System.Windows.Forms.Control.Click> událostí a mít každý ovládací prvek <xref:System.Windows.Forms.Control.Click> událost vázána jedné obslužné rutině událostí. Další informace najdete v tématu [jak: Připojení více událostí jedné obslužné rutině událostí ve Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Viz také:

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled událostí](events-overview-windows-forms.md)
