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
ms.openlocfilehash: 26b4f062c120bf543a5e597fc8c734e8cc336bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542194"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="4a2c7-102">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="4a2c7-102">User-Drawn Controls</span></span>
<span data-ttu-id="4a2c7-103">Rozhraní .NET Framework poskytuje možnost snadno vyvíjet vlastní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="4a2c7-104">Můžete vytvořit uživatelský ovládací prvek, což je sada standardních ovládacích prvků spojuje kód, nebo můžete navrhnout vlastní ovládací prvek od základů nahoru.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="4a2c7-105">Dědičnost i slouží k vytvoření ovládacího prvku, který dědí z existujícího ovládacího prvku a přidejte do jeho vyplývajících funkce.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="4a2c7-106">Libovolnou metodu použijete, rozhraní .NET Framework poskytuje funkce pro kreslení vlastní grafické rozhraní pro libovolný ovládací prvek, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="4a2c7-107">Vykreslování ovládacího prvku provádí spuštění kódu v ovládacím prvku <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="4a2c7-108">Jeden argument <xref:System.Windows.Forms.Control.OnPaint%2A> je metoda <xref:System.Windows.Forms.PaintEventArgs> objektu, který obsahuje všechny informace a funkce vyžadovaná k vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="4a2c7-109"><xref:System.Windows.Forms.PaintEventArgs> Poskytuje jako vlastnosti dva hlavní objekty, které se použijí při vykreslování ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="4a2c7-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
-   <span data-ttu-id="4a2c7-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objekt - obdélníku, která reprezentuje část ovládací prvek, který budou vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="4a2c7-111">To může být celý ovládací prvek, nebo její část ovládacího prvku v závislosti na tom, jak se nevykreslí ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
-   <span data-ttu-id="4a2c7-112"><xref:System.Drawing.Graphics> objekt - zapouzdří několik orientované grafické objekty a metody, které poskytují funkce, které jsou potřebné k vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="4a2c7-113">Další informace o <xref:System.Drawing.Graphics> objekt a jak ho použít, najdete v části [postupy: vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="4a2c7-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="4a2c7-114"><xref:System.Windows.Forms.Control.OnPaint%2A> Událost je aktivována vždy, když je ovládací prvek vykreslovat nebo aktualizovat na obrazovce a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objekt představuje obdélníku, ve kterém bude Malování probíhat.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="4a2c7-115">Pokud celý ovládací prvek, je potřeba aktualizovat, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> bude reprezentovat velikost celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="4a2c7-116">Pokud jenom část ovládacího prvku, je potřeba aktualizovat, ale <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objektů bude představovat pouze oblast, která musí být překreslen.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="4a2c7-117">Příkladem takové případě může být kdy ovládacího prvku byla částečně zakrytý jiného ovládacího prvku nebo formuláře v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="4a2c7-118">Když je zděděný z <xref:System.Windows.Forms.Control> třídy, je nutné přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda a poskytnout grafiky vykreslování kódu v rámci.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="4a2c7-119">Pokud chcete zadat vlastní grafické rozhraní pro uživatelský ovládací prvek nebo ovládací prvek zděděné, můžete provést také tak přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="4a2c7-120">Níže je uveden příklad:</span><span class="sxs-lookup"><span data-stu-id="4a2c7-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="4a2c7-121">Předchozí příklad ukazuje, jak k vykreslení ovládacího prvku s velmi jednoduché grafické reprezentace.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="4a2c7-122">Zavolá <xref:System.Windows.Forms.Control.OnPaint%2A> metoda základní třídy, vytvoří <xref:System.Drawing.Pen> objektu, ke které má být kreslení a nakonec nakreslí na elipsy v obdélníku dáno <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Size%2A> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="4a2c7-123">I když většina vykreslování kód bude výrazně složitější než to, tento příklad ukazuje použití <xref:System.Drawing.Graphics> objektů obsažených v rámci <xref:System.Windows.Forms.PaintEventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="4a2c7-124">Všimněte si, že pokud se dědí z třídy, která již má grafické reprezentace, jako například <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Button>a nechcete, aby k této reprezentace začlenit do vaší vykreslování, by neměla volat základní třída <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="4a2c7-125">Kód <xref:System.Windows.Forms.Control.OnPaint%2A> metoda ovládacího prvku, budou spuštěny při první vykreslením ovládacího prvku a vždy, když je aktualizována.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="4a2c7-126">Aby se zajistilo, že vlastní ovládací prvek bude překreslen pokaždé, když se změnila velikost, přidejte následující řádek do konstruktoru objektu vlastního ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="4a2c7-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="4a2c7-127">Použití <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> vlastnost implementaci obdélníkový ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4a2c7-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a2c7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="4a2c7-128">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Region%2A>  
 <xref:System.Windows.Forms.ControlStyles>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Windows.Forms.PaintEventArgs>  
 [<span data-ttu-id="4a2c7-129">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="4a2c7-129">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="4a2c7-130">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="4a2c7-130">Constituent Controls</span></span>](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 [<span data-ttu-id="4a2c7-131">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="4a2c7-131">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
