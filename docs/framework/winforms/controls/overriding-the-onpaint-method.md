---
title: Přepsání metody OnPaint
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
ms.openlocfilehash: 863726a6264f01de9f00296b4a64b9fd1bb96765
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182037"
---
# <a name="overriding-the-onpaint-method"></a>Přepsání metody OnPaint
Základní kroky pro přepsání jakékoli události definované v rozhraní .NET Framework jsou identické a jsou shrnuty v následujícím seznamu.  
  
#### <a name="to-override-an-inherited-event"></a>Přepsání zděděné události  
  
1. Přepište chráněnou `On`metodu *EventName.*  
  
2. Volání *Metody EventName* základní třídy z `On`přepsané metody *EventName,* aby registrovaní delegáti obdrželi událost. `On`  
  
 Událost <xref:System.Windows.Forms.Control.Paint> je popsána podrobně zde, protože každý <xref:System.Windows.Forms.Control.Paint> ovládací prvek Windows <xref:System.Windows.Forms.Control>Forms musí přepsat událost, která dědí z . Základní <xref:System.Windows.Forms.Control> třída neví, jak musí být odvozený ovládací prvek vykreslen, a <xref:System.Windows.Forms.Control.OnPaint%2A> neposkytuje žádnou logiku malování v metodě. Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control> jednoduše odešle <xref:System.Windows.Forms.Control.Paint> událost registrovaným příjemcům událostí.  
  
 Pokud jste pracovali prostřednictvím ukázky v [Postup: Vývoj jednoduché ho Windows](how-to-develop-a-simple-windows-forms-control.md)Forms <xref:System.Windows.Forms.Control.OnPaint%2A> Control , jste viděli příklad přepsání metody. Následující fragment kódu je převzat z této ukázky.  
  
```vb  
Public Class FirstControl  
   Inherits Control  
  
   Public Sub New()  
   End Sub  
  
   Protected Overrides Sub OnPaint(e As PaintEventArgs)  
      ' Call the OnPaint method of the base class.  
      MyBase.OnPaint(e)  
      ' Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, New SolidBrush(ForeColor), RectangleF.op_Implicit(ClientRectangle))  
   End Sub  
End Class
```  
  
```csharp  
public class FirstControl : Control {  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }
}
```  
  
 Třída <xref:System.Windows.Forms.PaintEventArgs> obsahuje data <xref:System.Windows.Forms.Control.Paint> pro událost. Má dvě vlastnosti, jak je znázorněno v následujícím kódu.  
  
```vb  
Public Class PaintEventArgs  
   Inherits EventArgs  
   ...  
   Public ReadOnly Property ClipRectangle() As System.Drawing.Rectangle  
      ...  
   End Property  
  
   Public ReadOnly Property Graphics() As System.Drawing.Graphics  
      ...  
   End Property
   ...  
End Class  
```  
  
```csharp  
public class PaintEventArgs : EventArgs {  
...  
    public System.Drawing.Rectangle ClipRectangle {}  
    public System.Drawing.Graphics Graphics {}  
...  
}  
```  
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>je obdélník, který má <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> být malován <xref:System.Drawing.Graphics> a vlastnost odkazuje na objekt. Třídy v <xref:System.Drawing?displayProperty=nameWithType> oboru názvů jsou spravované třídy, které poskytují přístup k funkcím GDI+, nové grafické knihovny systému Windows. Objekt <xref:System.Drawing.Graphics> má metody pro kreslení bodů, řetězců, čar, oblouků, elips a mnoha dalších tvarů.  
  
 Ovládací prvek vyvolá <xref:System.Windows.Forms.Control.OnPaint%2A> svou metodu vždy, když potřebuje změnit vizuální zobrazení. Tato metoda zase <xref:System.Windows.Forms.Control.Paint> vyvolá událost.  
  
## <a name="see-also"></a>Viz také

- [Akce](../../../standard/events/index.md)
- [Vykreslení ovládacího prvku Windows Forms](rendering-a-windows-forms-control.md)
- [Definování události](defining-an-event-in-windows-forms-controls.md)
