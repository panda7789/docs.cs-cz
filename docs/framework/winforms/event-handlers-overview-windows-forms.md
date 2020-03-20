---
title: Přehled obslužných rutin událostí
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
ms.openlocfilehash: ffec8a9f8e080dec78152e62e00e2dceefbdaab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141689"
---
# <a name="event-handlers-overview-windows-forms"></a>Přehled obslužných rutin událostí (Windows Forms)
Obslužná rutina události je metoda, která je vázána na událost. Při vyvolání události je spuštěn kód v rámci obslužné rutiny události. Každá obslužná rutina události poskytuje dva parametry, které umožňují správně zpracovat událost. Následující příklad ukazuje obslužnou <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Click> rutinu události pro událost ovládacího prvku.  
  
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
  
 První parametr`sender`, poskytuje odkaz na objekt, který vyvolal událost. Druhý parametr `e`, ve výše uvedeném příkladu, předá objekt specifický pro událost, která je zpracovávána. Odkazem na vlastnosti objektu (a někdy jeho metody), můžete získat informace, jako je například umístění myši pro události myši nebo data přenášená v přetažení události.  
  
 Obvykle každá událost vytvoří obslužnou rutinu události s jiným typem objektu události pro druhý parametr. Některé obslužné rutiny <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseUp> událostí, například pro události a, mají stejný typ objektu pro jejich druhý parametr. Pro tyto typy událostí můžete použít stejnou obslužnou rutinu události ke zpracování obou událostí.  
  
 Stejnou obslužnou rutinu události můžete také použít ke zpracování stejné události pro různé ovládací prvky. Například pokud máte skupinu <xref:System.Windows.Forms.RadioButton> ovládacích prvků ve formuláři, můžete <xref:System.Windows.Forms.Control.Click> vytvořit jednu obslužnou rutinu události pro událost a mít <xref:System.Windows.Forms.Control.Click> každý ovládací prvek událost vázána na jednu obslužnou rutinu události. Další informace naleznete v [tématu Postup: Připojení více událostí k obslužné rutině jedné události ve formulářích systému Windows](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Viz také

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled událostí](events-overview-windows-forms.md)
