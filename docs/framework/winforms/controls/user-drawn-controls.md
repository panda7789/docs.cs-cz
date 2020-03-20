---
title: Ovládací prvky vykreslované uživatelem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user-drawn
- OnPaint method [Windows Forms]
- user-drawn controls [Windows Forms]
ms.assetid: 034af4b5-457f-4160-a937-22891817faa8
ms.openlocfilehash: c68c8c88376cfe7295962264c466030115f2f3db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182013"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="9b2dd-102">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="9b2dd-102">User-Drawn Controls</span></span>
<span data-ttu-id="9b2dd-103">Rozhraní .NET Framework poskytuje možnost snadno vyvíjet vlastní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="9b2dd-104">Můžete vytvořit uživatelský ovládací prvek, což je sada standardních ovládacích prvků vázaných kódem, nebo můžete navrhnout vlastní ovládací prvek od základů.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="9b2dd-105">Dědičnost můžete dokonce použít k vytvoření ovládacího prvku, který dědí z existujícího ovládacího prvku a přidat k jeho vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="9b2dd-106">Bez ohledu na přístup, který použijete, rozhraní .NET Framework poskytuje funkce pro nakreslení vlastního grafického rozhraní pro libovolný ovládací prvek, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="9b2dd-107">Malování ovládacího prvku se provádí spuštěním kódu v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="9b2dd-108">Jediný argument <xref:System.Windows.Forms.Control.OnPaint%2A> metody je <xref:System.Windows.Forms.PaintEventArgs> objekt, který poskytuje všechny informace a funkce potřebné k vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="9b2dd-109">Poskytuje <xref:System.Windows.Forms.PaintEventArgs> jako vlastnosti dva hlavní objekty, které budou použity při vykreslování ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="9b2dd-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="9b2dd-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>objekt - obdélník, který představuje část ovládacího prvku, který bude nakreslena.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="9b2dd-111">To může být celý ovládací prvek nebo část ovládacího prvku v závislosti na tom, jak je nakreslena ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="9b2dd-112"><xref:System.Drawing.Graphics>object - zapouzdřuje několik objektů a metod orientovaných na grafiku, které poskytují funkce potřebné k nakreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="9b2dd-113">Další informace o <xref:System.Drawing.Graphics> objektu a jeho použití naleznete v [tématu How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="9b2dd-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="9b2dd-114">Událost <xref:System.Windows.Forms.Control.OnPaint%2A> je aktivována vždy, když je ovládací prvek <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nakreslena nebo aktualizována na obrazovce a objekt představuje obdélník, ve kterém bude malování probíhat.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="9b2dd-115">Pokud je třeba aktualizovat celý ovládací <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> prvek, bude představovat velikost celého ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="9b2dd-116">Pokud je však třeba aktualizovat pouze část <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> ovládacího prvku, bude objekt představovat pouze oblast, kterou je třeba překreslit.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="9b2dd-117">Příkladem takového případu by bylo, když byl ovládací prvek částečně zakryt jiným ovládacím prvkem nebo formulářem v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="9b2dd-118">Při dědění <xref:System.Windows.Forms.Control> z třídy, <xref:System.Windows.Forms.Control.OnPaint%2A> je nutné přepsat metodu a poskytnout kód vykreslování grafiky uvnitř.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="9b2dd-119">Pokud chcete poskytnout vlastní grafické rozhraní uživatelského ovládacího prvku nebo zděděného ovládacího prvku, můžete tak učinit také přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="9b2dd-120">Příklad najdete níže:</span><span class="sxs-lookup"><span data-stu-id="9b2dd-120">An example is shown below:</span></span>  
  
```vb  
Protected Overrides Sub OnPaint(ByVal e As PaintEventArgs)  
   ' Call the OnPaint method of the base class.  
   MyBase.OnPaint(e)  
  
   ' Declare and instantiate a drawing pen.  
   Using myPen As System.Drawing.Pen = New System.Drawing.Pen(Color.Aqua)  
      ' Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, New Rectangle(Me.Location, Me.Size))  
   End Using
End Sub  
```  
  
```csharp  
protected override void OnPaint(PaintEventArgs e)  
{  
   // Call the OnPaint method of the base class.  
   base.OnPaint(e);  
  
   // Declare and instantiate a new pen.  
   using (System.Drawing.Pen myPen = new System.Drawing.Pen(Color.Aqua))  
   {
      // Draw an aqua rectangle in the rectangle represented by the control.  
      e.Graphics.DrawRectangle(myPen, new Rectangle(this.Location,
         this.Size));  
   }
}  
```  
  
 <span data-ttu-id="9b2dd-121">Předchozí příklad ukazuje, jak vykreslit ovládací prvek s velmi jednoduchou grafickou reprezentací.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="9b2dd-122">Volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu základní třídy, vytvoří <xref:System.Drawing.Pen> objekt, se kterým chcete kreslit, a nakonec nakreslí <xref:System.Windows.Forms.Control.Location%2A> <xref:System.Windows.Forms.Control.Size%2A> elipsu v obdélníku určeném ovládacím prvkem a.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="9b2dd-123">Ačkoli většina vykreslovací kód bude výrazně složitější <xref:System.Drawing.Graphics> než tento, <xref:System.Windows.Forms.PaintEventArgs> tento příklad ukazuje použití objektu obsaženého v objektu.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="9b2dd-124">Všimněte si, že pokud dědíte z třídy, <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>která již má grafické znázornění, například nebo , a nechcete <xref:System.Windows.Forms.Control.OnPaint%2A> začlenit tuto reprezentaci do vykreslování, neměli byste volat metodu základní třídy.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="9b2dd-125">Kód v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě ovládacího prvku se spustí při prvním vykreslení ovládacího prvku a při každém aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="9b2dd-126">Chcete-li zajistit, že váš ovládací prvek je překreslen při každém jeho velikosti, přidejte následující řádek k konstruktoru ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="9b2dd-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="9b2dd-127">Pomocí <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> vlastnosti implementujte neobdélníkový ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9b2dd-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b2dd-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b2dd-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="9b2dd-129">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="9b2dd-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="9b2dd-130">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="9b2dd-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="9b2dd-131">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="9b2dd-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
