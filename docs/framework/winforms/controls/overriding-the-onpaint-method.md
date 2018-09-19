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
ms.openlocfilehash: fbc0a82f82afcc59384246b58437d521d56d708b
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46005606"
---
# <a name="overriding-the-onpaint-method"></a>Přepsání metody OnPaint
Základní kroky pro přepsání jakékoli události definované v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jsou shodné a jsou shrnuty v následujícím seznamu.  
  
#### <a name="to-override-an-inherited-event"></a>K přepsání zděděné události  
  
1.  Přepsat chráněnou `On` *EventName* metody.  
  
2.  Volání `On` *EventName* metoda základní třídy z přepsané `On` *EventName* metodu tak, která zaregistrovaný delegáti obdrží událost.  
  
 <xref:System.Windows.Forms.Control.Paint> Událostí je popsáno Zde podrobně vzhledem k tomu, že každý ovládací prvek Windows Forms musí přepsat <xref:System.Windows.Forms.Control.Paint> událost, která dědí z <xref:System.Windows.Forms.Control>. Základní <xref:System.Windows.Forms.Control> není známo, jak je potřeba vykreslit ovládací prvek odvozené třídy a neposkytuje žádnou logiku vykreslování v <xref:System.Windows.Forms.Control.OnPaint%2A> metody. <xref:System.Windows.Forms.Control.OnPaint%2A> Metodu <xref:System.Windows.Forms.Control> jednoduše odešle zprávu <xref:System.Windows.Forms.Control.Paint> události registrované události příjemcům.  
  
 Pokud jste již dříve pracovali prostřednictvím ukázka v [postup: vývoj jednoduchého ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), jste viděli příklad přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> metody. Následující fragment kódu je převzat z této ukázky.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs> Třída obsahuje data pro <xref:System.Windows.Forms.Control.Paint> událostí. Má dvě vlastnosti, jak je znázorněno v následujícím kódu.  
  
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
  
 <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> je obdélník, který se má namalovat a <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> vlastnost odkazuje na <xref:System.Drawing.Graphics> objektu. Třídy v <xref:System.Drawing?displayProperty=nameWithType> obor názvů jsou spravované třídy, které poskytují přístup k funkci [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], nové grafické knihovny Windows. <xref:System.Drawing.Graphics> Objekt má metody pro kreslení body, řetězce, řádky, oblouky, symbol tří teček a mnoho dalších tvarů.  
  
 Ovládací prvek vyvolá jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metoda pokaždé, když je potřeba změnit jeho vizuální zobrazení. Tato metoda vyvolá zase <xref:System.Windows.Forms.Control.Paint> událostí.  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../../docs/standard/events/index.md)  
 [Vykreslení ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [Definování události](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
