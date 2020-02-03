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
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743493"
---
# <a name="event-handlers-overview-windows-forms"></a>Přehled obslužných rutin událostí (Windows Forms)
Obslužná rutina události je metoda, která je svázána s událostí. Při vyvolání události je proveden kód v rámci obslužné rutiny události. Každá obslužná rutina události poskytuje dva parametry, které umožňují správné zpracování události. Následující příklad ukazuje obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> ovládacího prvku <xref:System.Windows.Forms.Button>.  
  
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
  
 První parametr,`sender`, poskytuje odkaz na objekt, který vyvolal událost. Druhý parametr `e`, v příkladu výše, předává objekt specifický pro událost, která je zpracovávána. Odkazem na vlastnosti objektu (a někdy na jeho metody) můžete získat informace, jako je například umístění myši pro události myši nebo přenášená data v událostech přetažení.  
  
 Každá událost obvykle vytváří obslužnou rutinu události s jiným typem objektu Event pro druhý parametr. Některé obslužné rutiny událostí, jako jsou například pro události <xref:System.Windows.Forms.Control.MouseDown> a <xref:System.Windows.Forms.Control.MouseUp>, mají stejný typ objektu pro svůj druhý parametr. Pro tyto typy událostí můžete použít stejnou obslužnou rutinu události pro zpracování obou událostí.  
  
 Můžete také použít stejnou obslužnou rutinu události pro zpracování stejné události pro různé ovládací prvky. Například pokud máte ve formuláři skupinu <xref:System.Windows.Forms.RadioButton> ovládací prvky, můžete vytvořit jedinou obslužnou rutinu události pro událost <xref:System.Windows.Forms.Control.Click> a nechat událost <xref:System.Windows.Forms.Control.Click> každého ovládacího prvku svázat s jednou obslužnou rutinou události. Další informace najdete v tématu [Postup: připojení více událostí k jedné obslužné rutině události v model Windows Forms](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Viz také

- [Vytváření obslužných rutin událostí ve Windows Forms](creating-event-handlers-in-windows-forms.md)
- [Přehled událostí](events-overview-windows-forms.md)
