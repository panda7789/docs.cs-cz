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
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128323"
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="cd118-102">Přepsání metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="cd118-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="cd118-103">Základní kroky pro přepsání jakékoli události definované v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jsou shodné a jsou shrnuty v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="cd118-103">The basic steps for overriding any event defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="cd118-104">K přepsání zděděné události</span><span class="sxs-lookup"><span data-stu-id="cd118-104">To override an inherited event</span></span>  
  
1.  <span data-ttu-id="cd118-105">Přepsat chráněnou `On` *EventName* metody.</span><span class="sxs-lookup"><span data-stu-id="cd118-105">Override the protected `On`*EventName* method.</span></span>  
  
2.  <span data-ttu-id="cd118-106">Volání `On` *EventName* metoda základní třídy z přepsané `On` *EventName* metodu tak, která zaregistrovaný delegáti obdrží událost.</span><span class="sxs-lookup"><span data-stu-id="cd118-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="cd118-107"><xref:System.Windows.Forms.Control.Paint> Událostí je popsáno Zde podrobně vzhledem k tomu, že každý ovládací prvek Windows Forms musí přepsat <xref:System.Windows.Forms.Control.Paint> událost, která dědí z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="cd118-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="cd118-108">Základní <xref:System.Windows.Forms.Control> není známo, jak je potřeba vykreslit ovládací prvek odvozené třídy a neposkytuje žádnou logiku vykreslování v <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cd118-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="cd118-109"><xref:System.Windows.Forms.Control.OnPaint%2A> Metodu <xref:System.Windows.Forms.Control> jednoduše odešle zprávu <xref:System.Windows.Forms.Control.Paint> události registrované události příjemcům.</span><span class="sxs-lookup"><span data-stu-id="cd118-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="cd118-110">Pokud jste již dříve pracovali prostřednictvím ukázka v [postup: vývoj jednoduchého ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), jste viděli příklad přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cd118-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="cd118-111">Následující fragment kódu je převzat z této ukázky.</span><span class="sxs-lookup"><span data-stu-id="cd118-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="cd118-112"><xref:System.Windows.Forms.PaintEventArgs> Třída obsahuje data pro <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="cd118-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="cd118-113">Má dvě vlastnosti, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="cd118-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="cd118-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> je obdélník, který se má namalovat a <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> vlastnost odkazuje na <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="cd118-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="cd118-115">Třídy v <xref:System.Drawing?displayProperty=nameWithType> obor názvů jsou spravované třídy, které poskytují přístup k funkci [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], nové grafické knihovny Windows.</span><span class="sxs-lookup"><span data-stu-id="cd118-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the new Windows graphics library.</span></span> <span data-ttu-id="cd118-116"><xref:System.Drawing.Graphics> Objekt má metody pro kreslení body, řetězce, řádky, oblouky, symbol tří teček a mnoho dalších tvarů.</span><span class="sxs-lookup"><span data-stu-id="cd118-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="cd118-117">Ovládací prvek vyvolá jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metoda pokaždé, když je potřeba změnit jeho vizuální zobrazení.</span><span class="sxs-lookup"><span data-stu-id="cd118-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="cd118-118">Tato metoda vyvolá zase <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="cd118-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd118-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd118-119">See Also</span></span>  
 [<span data-ttu-id="cd118-120">Události</span><span class="sxs-lookup"><span data-stu-id="cd118-120">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="cd118-121">Vykreslení ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd118-121">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [<span data-ttu-id="cd118-122">Definování události</span><span class="sxs-lookup"><span data-stu-id="cd118-122">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
