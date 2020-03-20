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
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="7deae-102">Přepsání metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="7deae-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="7deae-103">Základní kroky pro přepsání jakékoli události definované v rozhraní .NET Framework jsou identické a jsou shrnuty v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="7deae-103">The basic steps for overriding any event defined in the .NET Framework are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="7deae-104">Přepsání zděděné události</span><span class="sxs-lookup"><span data-stu-id="7deae-104">To override an inherited event</span></span>  
  
1. <span data-ttu-id="7deae-105">Přepište chráněnou `On`metodu *EventName.*</span><span class="sxs-lookup"><span data-stu-id="7deae-105">Override the protected `On`*EventName* method.</span></span>  
  
2. <span data-ttu-id="7deae-106">Volání *Metody EventName* základní třídy z `On`přepsané metody *EventName,* aby registrovaní delegáti obdrželi událost. `On`</span><span class="sxs-lookup"><span data-stu-id="7deae-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="7deae-107">Událost <xref:System.Windows.Forms.Control.Paint> je popsána podrobně zde, protože každý <xref:System.Windows.Forms.Control.Paint> ovládací prvek Windows <xref:System.Windows.Forms.Control>Forms musí přepsat událost, která dědí z .</span><span class="sxs-lookup"><span data-stu-id="7deae-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="7deae-108">Základní <xref:System.Windows.Forms.Control> třída neví, jak musí být odvozený ovládací prvek vykreslen, a <xref:System.Windows.Forms.Control.OnPaint%2A> neposkytuje žádnou logiku malování v metodě.</span><span class="sxs-lookup"><span data-stu-id="7deae-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="7deae-109">Metoda <xref:System.Windows.Forms.Control.OnPaint%2A> <xref:System.Windows.Forms.Control> jednoduše odešle <xref:System.Windows.Forms.Control.Paint> událost registrovaným příjemcům událostí.</span><span class="sxs-lookup"><span data-stu-id="7deae-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="7deae-110">Pokud jste pracovali prostřednictvím ukázky v [Postup: Vývoj jednoduché ho Windows](how-to-develop-a-simple-windows-forms-control.md)Forms <xref:System.Windows.Forms.Control.OnPaint%2A> Control , jste viděli příklad přepsání metody.</span><span class="sxs-lookup"><span data-stu-id="7deae-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="7deae-111">Následující fragment kódu je převzat z této ukázky.</span><span class="sxs-lookup"><span data-stu-id="7deae-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="7deae-112">Třída <xref:System.Windows.Forms.PaintEventArgs> obsahuje data <xref:System.Windows.Forms.Control.Paint> pro událost.</span><span class="sxs-lookup"><span data-stu-id="7deae-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="7deae-113">Má dvě vlastnosti, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7deae-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="7deae-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>je obdélník, který má <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> být malován <xref:System.Drawing.Graphics> a vlastnost odkazuje na objekt.</span><span class="sxs-lookup"><span data-stu-id="7deae-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="7deae-115">Třídy v <xref:System.Drawing?displayProperty=nameWithType> oboru názvů jsou spravované třídy, které poskytují přístup k funkcím GDI+, nové grafické knihovny systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7deae-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of GDI+, the new Windows graphics library.</span></span> <span data-ttu-id="7deae-116">Objekt <xref:System.Drawing.Graphics> má metody pro kreslení bodů, řetězců, čar, oblouků, elips a mnoha dalších tvarů.</span><span class="sxs-lookup"><span data-stu-id="7deae-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="7deae-117">Ovládací prvek vyvolá <xref:System.Windows.Forms.Control.OnPaint%2A> svou metodu vždy, když potřebuje změnit vizuální zobrazení.</span><span class="sxs-lookup"><span data-stu-id="7deae-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="7deae-118">Tato metoda zase <xref:System.Windows.Forms.Control.Paint> vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="7deae-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7deae-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7deae-119">See also</span></span>

- [<span data-ttu-id="7deae-120">Akce</span><span class="sxs-lookup"><span data-stu-id="7deae-120">Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="7deae-121">Vykreslení ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7deae-121">Rendering a Windows Forms Control</span></span>](rendering-a-windows-forms-control.md)
- [<span data-ttu-id="7deae-122">Definování události</span><span class="sxs-lookup"><span data-stu-id="7deae-122">Defining an Event</span></span>](defining-an-event-in-windows-forms-controls.md)
