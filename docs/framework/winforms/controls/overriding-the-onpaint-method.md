---
title: "Přepsání metody OnPaint"
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
helpviewer_keywords:
- Paint event [Windows Forms], handling in Windows Forms custom control
- OnPaint method [Windows Forms], overriding in Windows Forms custom controls
ms.assetid: e9ca2723-0107-4540-bb21-4f5ffb4a9906
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41205f7f0ec21e27b97d0b12415fca89ae526552
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="overriding-the-onpaint-method"></a><span data-ttu-id="5778a-102">Přepsání metody OnPaint</span><span class="sxs-lookup"><span data-stu-id="5778a-102">Overriding the OnPaint Method</span></span>
<span data-ttu-id="5778a-103">Základní kroky pro všechny události definované v přepsání [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jsou identické a jsou shrnuty v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="5778a-103">The basic steps for overriding any event defined in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] are identical and are summarized in the following list.</span></span>  
  
#### <a name="to-override-an-inherited-event"></a><span data-ttu-id="5778a-104">Chcete-li přepsat zděděné události</span><span class="sxs-lookup"><span data-stu-id="5778a-104">To override an inherited event</span></span>  
  
1.  <span data-ttu-id="5778a-105">Přepsání chráněného `On` *EventName* metoda.</span><span class="sxs-lookup"><span data-stu-id="5778a-105">Override the protected `On`*EventName* method.</span></span>  
  
2.  <span data-ttu-id="5778a-106">Volání `On` *EventName* metoda základní třídy z přepsané `On` *EventName* metody, které registrováno delegáti přijímat události.</span><span class="sxs-lookup"><span data-stu-id="5778a-106">Call the `On`*EventName* method of the base class from the overridden `On`*EventName* method, so that registered delegates receive the event.</span></span>  
  
 <span data-ttu-id="5778a-107"><xref:System.Windows.Forms.Control.Paint> Událostí je podrobněji zde protože každé ovládacího prvku Windows Forms musí přepsat <xref:System.Windows.Forms.Control.Paint> událost, která dědí z <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="5778a-107">The <xref:System.Windows.Forms.Control.Paint> event is discussed in detail here because every Windows Forms control must override the <xref:System.Windows.Forms.Control.Paint> event that it inherits from <xref:System.Windows.Forms.Control>.</span></span> <span data-ttu-id="5778a-108">Základní <xref:System.Windows.Forms.Control> třídy nebude vědět, jak je nutné vykreslit odvozené ovládací prvek a neposkytuje žádné Malování logiku <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5778a-108">The base <xref:System.Windows.Forms.Control> class does not know how a derived control needs to be drawn and does not provide any painting logic in the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="5778a-109"><xref:System.Windows.Forms.Control.OnPaint%2A> Metodu <xref:System.Windows.Forms.Control> jednoduše odešle zprávu <xref:System.Windows.Forms.Control.Paint> událost, která má přijímače událostí registrované.</span><span class="sxs-lookup"><span data-stu-id="5778a-109">The <xref:System.Windows.Forms.Control.OnPaint%2A> method of <xref:System.Windows.Forms.Control> simply dispatches the <xref:System.Windows.Forms.Control.Paint> event to registered event receivers.</span></span>  
  
 <span data-ttu-id="5778a-110">Pokud jste pracovali prostřednictvím vzorku v [postup: vývoj jednoduchého prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), jste viděli příklad přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5778a-110">If you worked through the sample in [How to: Develop a Simple Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md), you have seen an example of overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="5778a-111">Následující fragment kódu je převzat z této ukázky.</span><span class="sxs-lookup"><span data-stu-id="5778a-111">The following code fragment is taken from that sample.</span></span>  
  
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
  
 <span data-ttu-id="5778a-112"><xref:System.Windows.Forms.PaintEventArgs> Třída obsahuje data <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="5778a-112">The <xref:System.Windows.Forms.PaintEventArgs> class contains data for the <xref:System.Windows.Forms.Control.Paint> event.</span></span> <span data-ttu-id="5778a-113">Má dvě vlastnosti, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5778a-113">It has two properties, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="5778a-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>je nutné překreslit rámeček a <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> vlastnost odkazuje <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="5778a-114"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> is the rectangle to be painted, and the <xref:System.Windows.Forms.PaintEventArgs.Graphics%2A> property refers to a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="5778a-115">Třídy v <xref:System.Drawing?displayProperty=nameWithType> obor názvů se spravují třídy, které poskytují přístup k funkci [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], nové knihovny grafika systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5778a-115">The classes in the <xref:System.Drawing?displayProperty=nameWithType> namespace are managed classes that provide access to the functionality of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], the new Windows graphics library.</span></span> <span data-ttu-id="5778a-116"><xref:System.Drawing.Graphics> Objekt má metody k vykreslení body, řetězce, řádky, oblouky, tři tečky a mnoho ostatním tvarům.</span><span class="sxs-lookup"><span data-stu-id="5778a-116">The <xref:System.Drawing.Graphics> object has methods to draw points, strings, lines, arcs, ellipses, and many other shapes.</span></span>  
  
 <span data-ttu-id="5778a-117">Vyvolá ovládacího prvku jeho <xref:System.Windows.Forms.Control.OnPaint%2A> metoda kdykoli bude potřeba změnit jeho visual zobrazení.</span><span class="sxs-lookup"><span data-stu-id="5778a-117">A control invokes its <xref:System.Windows.Forms.Control.OnPaint%2A> method whenever it needs to change its visual display.</span></span> <span data-ttu-id="5778a-118">Tato metoda vyvolá zase <xref:System.Windows.Forms.Control.Paint> událostí.</span><span class="sxs-lookup"><span data-stu-id="5778a-118">This method in turn raises the <xref:System.Windows.Forms.Control.Paint> event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5778a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="5778a-119">See Also</span></span>  
 [<span data-ttu-id="5778a-120">Události</span><span class="sxs-lookup"><span data-stu-id="5778a-120">Events</span></span>](../../../../docs/standard/events/index.md)  
 [<span data-ttu-id="5778a-121">Vykreslování ovládacího prvku Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5778a-121">Rendering a Windows Forms Control</span></span>](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 [<span data-ttu-id="5778a-122">Definování události</span><span class="sxs-lookup"><span data-stu-id="5778a-122">Defining an Event</span></span>](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)
