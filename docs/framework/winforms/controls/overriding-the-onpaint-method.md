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
ms.openlocfilehash: fc41158e9a3d5d331b391f0f28701612012becf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="overriding-the-onpaint-method"></a>Přepsání metody OnPaint
Základní kroky pro všechny události definované v přepsání [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jsou identické a jsou shrnuty v následujícím seznamu.  
  
#### <a name="to-override-an-inherited-event"></a>Chcete-li přepsat zděděné události  
  
1.  Přepsání chráněného `On` *EventName* metoda.  
  
2.  Volání `On` *EventName* metoda základní třídy z přepsané `On` *EventName* metody, které registrováno delegáti přijímat události.  
  
 <xref:System.Windows.Forms.Control.Paint> Událostí je podrobněji zde protože každé ovládacího prvku Windows Forms musí přepsat <xref:System.Windows.Forms.Control.Paint> událost, která dědí z <xref:System.Windows.Forms.Control>. Základní <xref:System.Windows.Forms.Control> třídy nebude vědět, jak je nutné vykreslit odvozené ovládací prvek a neposkytuje žádné Malování logiku <xref:System.Windows.Forms.Control.OnPaint%2A> metoda. <xref:System.Windows.Forms.Control.OnPaint%2A> Metodu <xref:System.Windows.Forms.Control> jednoduše odešle zprávu <xref:System.Windows.Forms.Control.Paint> událost, která má přijímače událostí registrované.  
  
 Pokud jste pracovali prostřednictvím vzorku v [postup: vývoj jednoduchého prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), jste viděli příklad přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> metoda. Následující fragment kódu je převzat z této ukázky.  
  
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
public class FirstControl : Control{  
   public FirstControl() {}  
   protected override void OnPaint(PaintEventArgs e) {  
      // Call the OnPaint method of the base class.  
      base.OnPaint(e);  
      // Call methods of the System.Drawing.Graphics object.  
      e.Graphics.DrawString(Text, Font, new SolidBrush(ForeColor), ClientRectangle);  
   }   
}   
```  
  
 <xref:System.Windows.Forms.PaintEventArgs> Třída obsahuje data <xref:System.Windows.Forms.Control.Paint> událostí. Má dvě vlastnosti, jak je znázorněno v následujícím kódu.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> je nutné překreslit rámeček a <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> vlastnost odkazuje <xref:System.Drawing.Graphics> objektu. Třídy v <xref:System.Drawing?displayProperty=nameWithType> obor názvů se spravují třídy, které poskytují přístup k funkci [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], nové knihovny grafika systému Windows. <xref:System.Drawing.Graphics> Objekt má metody k vykreslení body, řetězce, řádky, oblouky, tři tečky a mnoho ostatním tvarům.  
  
 Vyvolá ovládacího prvku jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metoda kdykoli bude potřeba změnit jeho visual zobrazení. Tato metoda vyvolá zase <xref:System.Windows.Forms.Control.Paint> událostí.  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../../docs/standard/events/index.md)  
 [Vykreslení ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [Definování události](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
