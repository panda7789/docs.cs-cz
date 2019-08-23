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
ms.openlocfilehash: 50036f5bef323368b4970a080ca7a70cf94252d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966488"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="aec61-102">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="aec61-102">User-Drawn Controls</span></span>
<span data-ttu-id="aec61-103">.NET Framework poskytuje možnost snadného vývoje vlastních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="aec61-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="aec61-104">Můžete vytvořit uživatelský ovládací prvek, což je sada standardních ovládacích prvků, které jsou vázány pomocí kódu, nebo můžete navrhnout vlastní ovládací prvek od základu.</span><span class="sxs-lookup"><span data-stu-id="aec61-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="aec61-105">Dědičnost můžete dokonce použít k vytvoření ovládacího prvku, který dědí z existujícího ovládacího prvku a jeho přidáním do své vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="aec61-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="aec61-106">Bez ohledu na to, kterou metodu použijete, .NET Framework poskytuje funkce pro nakreslení vlastního grafického rozhraní pro jakýkoli ovládací prvek, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="aec61-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="aec61-107">Malování ovládacího prvku je provedeno spuštěním kódu v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aec61-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="aec61-108">Jediný argument <xref:System.Windows.Forms.Control.OnPaint%2A> metody <xref:System.Windows.Forms.PaintEventArgs> je objekt, který poskytuje všechny informace a funkce požadované pro vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aec61-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="aec61-109"><xref:System.Windows.Forms.PaintEventArgs> Poskytuje jako vlastnosti dva objekty zabezpečení, které budou použity při vykreslování ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="aec61-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
- <span data-ttu-id="aec61-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A>Object – obdélník, který představuje část ovládacího prvku, který bude vykreslen.</span><span class="sxs-lookup"><span data-stu-id="aec61-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="aec61-111">Může to být celý ovládací prvek nebo část ovládacího prvku v závislosti na tom, jak je ovládací prvek vykreslen.</span><span class="sxs-lookup"><span data-stu-id="aec61-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
- <span data-ttu-id="aec61-112"><xref:System.Drawing.Graphics>objekt – zapouzdřuje několik grafických objektů a metod, které poskytují funkcionalitu nutnou k nakreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aec61-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="aec61-113">Další informace o <xref:System.Drawing.Graphics> objektu a jeho použití naleznete v tématu [How to: Vytvoření grafických objektů pro kreslení](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="aec61-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="aec61-114">Událost se aktivuje vždy, když se ovládací prvek vykreslí nebo aktualizuje na obrazovce <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> a objekt představuje obdélník, ve kterém bude provedeno malování. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="aec61-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="aec61-115">Pokud je nutné celý ovládací prvek aktualizovat, <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> bude reprezentovat velikost celého ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aec61-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="aec61-116">Je-li však <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> nutné aktualizovat pouze část ovládacího prvku, bude objekt představovat pouze oblast, která je zapotřebí překreslit.</span><span class="sxs-lookup"><span data-stu-id="aec61-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="aec61-117">Příkladem takového případu by bylo, že ovládací prvek byl částečně skryt jiným ovládacím prvkem nebo formulářem v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aec61-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="aec61-118">Při dědění z <xref:System.Windows.Forms.Control> třídy je nutné <xref:System.Windows.Forms.Control.OnPaint%2A> přepsat metodu a zadat kód pro vykreslování grafiky v rámci.</span><span class="sxs-lookup"><span data-stu-id="aec61-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="aec61-119">Pokud chcete zadat vlastní grafické rozhraní pro uživatelský ovládací prvek nebo Zděděný ovládací prvek, můžete to provést také přepsáním <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="aec61-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="aec61-120">Příklad je uveden níže:</span><span class="sxs-lookup"><span data-stu-id="aec61-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="aec61-121">Předchozí příklad ukazuje, jak vykreslit ovládací prvek pomocí velmi jednoduché grafické reprezentace.</span><span class="sxs-lookup"><span data-stu-id="aec61-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="aec61-122">Volá <xref:System.Windows.Forms.Control.OnPaint%2A> metodu základní třídy, <xref:System.Drawing.Pen> vytvoří objekt, který se má kreslit, a nakonec nakreslí elipsu v obdélníku určeném <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Size%2A> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="aec61-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="aec61-123">I když je většina vykreslování kódu podstatně složitější, tento příklad ukazuje použití <xref:System.Drawing.Graphics> objektu obsaženého <xref:System.Windows.Forms.PaintEventArgs> v objektu.</span><span class="sxs-lookup"><span data-stu-id="aec61-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="aec61-124">Všimněte si, že pokud dědíte z třídy, která již obsahuje grafické znázornění, například <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Button>, a nechcete začlenit tuto reprezentaci do vykreslování, neměli byste <xref:System.Windows.Forms.Control.OnPaint%2A> volat třídu základní třídy. Metoda.</span><span class="sxs-lookup"><span data-stu-id="aec61-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="aec61-125">Kód v <xref:System.Windows.Forms.Control.OnPaint%2A> metodě ovládacího prvku bude proveden při prvním vykreslení ovládacího prvku a při každém jeho aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="aec61-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="aec61-126">Chcete-li zajistit, aby byl ovládací prvek překreslen při každé změně velikosti, přidejte následující řádek do konstruktoru ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="aec61-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
> <span data-ttu-id="aec61-127"><xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> Použijte vlastnost k implementaci ovládacího prvku, který není pravoúhlý.</span><span class="sxs-lookup"><span data-stu-id="aec61-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec61-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aec61-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="aec61-129">Postupy: Vytvoření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="aec61-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="aec61-130">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="aec61-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="aec61-131">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="aec61-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
