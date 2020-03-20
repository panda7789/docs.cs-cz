---
title: Základní ovládací prvky
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], constituent controls
- constituent controls [Windows Forms]
- user controls [Windows Forms], constituent controls
ms.assetid: 5565e720-198b-4bbd-a2bd-c447ba641798
ms.openlocfilehash: 2865a3d85bd56151038ee90c18d199d3a584b5d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182418"
---
# <a name="constituent-controls"></a><span data-ttu-id="77de4-102">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="77de4-102">Constituent Controls</span></span>
<span data-ttu-id="77de4-103">Ovládací prvky, které tvoří uživatelský ovládací prvek nebo *základní ovládací prvky,* jak jsou označovány, jsou relativně nepružné, pokud jde o vlastní vykreslování grafiky.</span><span class="sxs-lookup"><span data-stu-id="77de4-103">The controls that make up a user control, or *constituent controls* as they are termed, are relatively inflexible when it comes to custom graphics rendering.</span></span> <span data-ttu-id="77de4-104">Všechny ovládací prvky Windows Forms <xref:System.Windows.Forms.Control.OnPaint%2A> zpracovávají vlastní vykreslování vlastní metodou.</span><span class="sxs-lookup"><span data-stu-id="77de4-104">All Windows Forms controls handle their own rendering through their own <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="77de4-105">Vzhledem k tomu, že tato metoda je chráněna, není přístupná vývojáři, a proto nemůže být zabráněno spuštění při vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77de4-105">Because this method is protected, it is not accessible to the developer, and thus cannot be prevented from executing when the control is painted.</span></span> <span data-ttu-id="77de4-106">To však neznamená, že nelze přidat kód ovlivnit vzhled základních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="77de4-106">This does not mean, however, that you cannot add code to affect the appearance of constituent controls.</span></span> <span data-ttu-id="77de4-107">Další vykreslování lze provést přidáním obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="77de4-107">Additional rendering can be accomplished by adding an event handler.</span></span> <span data-ttu-id="77de4-108">Předpokládejme například, že <xref:System.Windows.Forms.UserControl> jste vytvářeli `MyButton`tlačítko s názvem .</span><span class="sxs-lookup"><span data-stu-id="77de4-108">For example, suppose you were authoring a <xref:System.Windows.Forms.UserControl> with a button named `MyButton`.</span></span> <span data-ttu-id="77de4-109">Pokud jste chtěli mít další vykreslování nad rámec <xref:System.Web.UI.WebControls.Button>toho, co bylo poskytnuto , byste přidat kód do uživatelského ovládacího prvku podobně jako následující:</span><span class="sxs-lookup"><span data-stu-id="77de4-109">If you wished to have additional rendering beyond what was provided by the <xref:System.Web.UI.WebControls.Button>, you would add code to your user control similar to the following:</span></span>  
  
```vb  
Public Sub MyPaint(ByVal sender as Object, e as PaintEventArgs) Handles _  
   MyButton.Paint  
   'Additional rendering code goes here  
End Sub  
```  
  
```csharp  
// Add the event handler to the button's Paint event.  
MyButton.Paint +=
   new System.Windows.Forms.PaintEventHandler (this.MyPaint);  
// Create the custom painting method.  
protected void MyPaint (object sender,
System.Windows.Forms.PaintEventArgs e)  
{  
   // Additional rendering code goes here.  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="77de4-110">Některé ovládací prvky <xref:System.Windows.Forms.TextBox>windows forms, například , jsou malovány přímo systémem Windows.</span><span class="sxs-lookup"><span data-stu-id="77de4-110">Some Windows Forms controls, such as <xref:System.Windows.Forms.TextBox>, are painted directly by Windows.</span></span> <span data-ttu-id="77de4-111">V těchto případech <xref:System.Windows.Forms.Control.OnPaint%2A> metoda je nikdy volána, a proto výše uvedený příklad nikdy být volána.</span><span class="sxs-lookup"><span data-stu-id="77de4-111">In these instances, the <xref:System.Windows.Forms.Control.OnPaint%2A> method is never called, and thus the above example will never be called.</span></span>  
  
 <span data-ttu-id="77de4-112">Tím se vytvoří metoda, která `MyButton.Paint` se spustí při každém spuštění události, čímž se přidá další grafické znázornění ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="77de4-112">This creates a method that executes every time the `MyButton.Paint` event executes, thereby adding additional graphical representation to your control.</span></span> <span data-ttu-id="77de4-113">Všimněte si, že to `MyButton.OnPaint`nebrání provedení , a proto všechny malování obvykle provádí tlačítko bude stále provedena kromě vlastní malování.</span><span class="sxs-lookup"><span data-stu-id="77de4-113">Note that this does not prevent the execution of `MyButton.OnPaint`, and thus all of the painting usually performed by a button will still be performed in addition to your custom painting.</span></span> <span data-ttu-id="77de4-114">Podrobnosti o technologii GDI+ a vlastním vykreslování naleznete v [tématu Vytváření grafických obrazů pomocí technologie GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="77de4-114">For details about GDI+ technology and custom rendering, see the [Creating Graphical Images with GDI+](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="77de4-115">Pokud chcete mít jedinečnou reprezentaci ovládacího prvku, nejlepší postup je vytvořit zděděný ovládací prvek a napsat vlastní vykreslování kód pro něj.</span><span class="sxs-lookup"><span data-stu-id="77de4-115">If you wish to have a unique representation of your control, your best course of action is to create an inherited control, and to write custom rendering code for it.</span></span> <span data-ttu-id="77de4-116">Podrobnosti naleznete v [tématu User-Drawn Controls](user-drawn-controls.md).</span><span class="sxs-lookup"><span data-stu-id="77de4-116">For details, see [User-Drawn Controls](user-drawn-controls.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77de4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="77de4-117">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="77de4-118">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="77de4-118">User-Drawn Controls</span></span>](user-drawn-controls.md)
- [<span data-ttu-id="77de4-119">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="77de4-119">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="77de4-120">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="77de4-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
