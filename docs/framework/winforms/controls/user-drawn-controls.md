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
ms.openlocfilehash: 06513fc44782c78d2d69b82130542949519c0107
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158441"
---
# <a name="user-drawn-controls"></a><span data-ttu-id="bd56c-102">Ovládací prvky vykreslované uživatelem</span><span class="sxs-lookup"><span data-stu-id="bd56c-102">User-Drawn Controls</span></span>
<span data-ttu-id="bd56c-103">Rozhraní .NET Framework poskytuje možnost snadno vyvíjet vlastní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="bd56c-103">The .NET Framework provides you with the ability to easily develop your own controls.</span></span> <span data-ttu-id="bd56c-104">Můžete vytvořit uživatelský ovládací prvek je sada standardních ovládacích prvků kódu jsou technologicky propojené, nebo si můžete navrhnout vlastní ovládací prvek od základů.</span><span class="sxs-lookup"><span data-stu-id="bd56c-104">You can create a user control, which is a set of standard controls bound together by code, or you can design your own control from the ground up.</span></span> <span data-ttu-id="bd56c-105">Dědičnost můžete použít i k vytvoření ovládacího prvku, který dědí z existujícího ovládacího prvku a přidejte do jeho vlastní funkce.</span><span class="sxs-lookup"><span data-stu-id="bd56c-105">You can even use inheritance to create a control that inherits from an existing control and add to its inherent functionality.</span></span> <span data-ttu-id="bd56c-106">Jakýkoli přístup, můžete použít, rozhraní .NET Framework poskytuje funkce pro kreslení vlastní grafické rozhraní pro libovolný ovládací prvek, který vytvoříte.</span><span class="sxs-lookup"><span data-stu-id="bd56c-106">Whatever approach you use, the .NET Framework provides the functionality to draw a custom graphical interface for any control you create.</span></span>  
  
 <span data-ttu-id="bd56c-107">Vykreslování ovládacího prvku lze dosáhnout spuštění kódu v ovládacím prvku <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bd56c-107">Painting of a control is accomplished by the execution of code in the control's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="bd56c-108">Jediný argument <xref:System.Windows.Forms.Control.OnPaint%2A> je metoda <xref:System.Windows.Forms.PaintEventArgs> objektu, který obsahuje všechny informace a funkce pro vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd56c-108">The single argument of the <xref:System.Windows.Forms.Control.OnPaint%2A> method is a <xref:System.Windows.Forms.PaintEventArgs> object that provides all of the information and functionality required to render your control.</span></span> <span data-ttu-id="bd56c-109"><xref:System.Windows.Forms.PaintEventArgs> Jako vlastnosti poskytuje dva hlavní objekty, které se použije při vykreslování ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="bd56c-109">The <xref:System.Windows.Forms.PaintEventArgs> provides as properties two principal objects that will be used in the rendering of your control:</span></span>  
  
-   <span data-ttu-id="bd56c-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objekt - obdélník, který představuje část ovládacího prvku, který bude vykreslen.</span><span class="sxs-lookup"><span data-stu-id="bd56c-110"><xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object - the rectangle that represents the part of the control that will be drawn.</span></span> <span data-ttu-id="bd56c-111">To může být celý ovládací prvek nebo část ovládacího prvku v závislosti na tom, jak vykreslit ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="bd56c-111">This can be the entire control, or part of the control depending on how the control is drawn.</span></span>  
  
-   <span data-ttu-id="bd56c-112"><xref:System.Drawing.Graphics> objekt - zapouzdřuje několik orientované grafické objekty a metody, které poskytují funkce, které jsou potřebné k vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd56c-112"><xref:System.Drawing.Graphics> object - encapsulates several graphics-oriented objects and methods that provide the functionality necessary to draw your control.</span></span>  
  
 <span data-ttu-id="bd56c-113">Další informace o <xref:System.Drawing.Graphics> objekt a jak ho použít, najdete v článku [jak: Vytváření grafických objektů pro kreslení](../advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="bd56c-113">For more information on the <xref:System.Drawing.Graphics> object and how to use it, see [How to: Create Graphics Objects for Drawing](../advanced/how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
 <span data-ttu-id="bd56c-114"><xref:System.Windows.Forms.Control.OnPaint%2A> Událost se aktivuje vždy, když je ovládací prvek vykreslen nebo aktualizovat na obrazovce a <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objekt představuje obdélník, ve kterém se Malování proběhnout.</span><span class="sxs-lookup"><span data-stu-id="bd56c-114">The <xref:System.Windows.Forms.Control.OnPaint%2A> event is fired whenever the control is drawn or refreshed on the screen, and the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object represents the rectangle in which painting will take place.</span></span> <span data-ttu-id="bd56c-115">Pokud je potřeba aktualizovat, celý ovládací prvek <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> bude představovat velikost celý ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="bd56c-115">If the entire control needs to be refreshed, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> will represent the size of the entire control.</span></span> <span data-ttu-id="bd56c-116">Pokud pouze část ovládacího prvku musí aktualizovat, ale <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> objektů bude představovat jenom oblasti, kterou je potřeba se měl překreslit.</span><span class="sxs-lookup"><span data-stu-id="bd56c-116">If only part of the control needs to be refreshed, however, the <xref:System.Windows.Forms.PaintEventArgs.ClipRectangle%2A> object will represent only the region that needs to be redrawn.</span></span> <span data-ttu-id="bd56c-117">Příklad takovém případě se při ovládacího prvku byla částečně zakrytý jiného ovládacího prvku nebo formuláře v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd56c-117">An example of such a case would be when a control was partially obscured by another control or form in the user interface.</span></span>  
  
 <span data-ttu-id="bd56c-118">Při dědění z <xref:System.Windows.Forms.Control> třídy, je nutné přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu a zadejte kód pro vykreslování grafiky v rámci.</span><span class="sxs-lookup"><span data-stu-id="bd56c-118">When inheriting from the <xref:System.Windows.Forms.Control> class, you must override the <xref:System.Windows.Forms.Control.OnPaint%2A> method and provide graphics-rendering code within.</span></span> <span data-ttu-id="bd56c-119">Pokud chcete poskytnout vlastní grafické rozhraní pro uživatelský ovládací prvek nebo zděděný ovládací prvek, lze také uděláte tak, že přepíšete <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bd56c-119">If you want to provide a custom graphical interface to a user control or an inherited control, you can also do so by overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span> <span data-ttu-id="bd56c-120">Příklad je uveden níže:</span><span class="sxs-lookup"><span data-stu-id="bd56c-120">An example is shown below:</span></span>  
  
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
  
 <span data-ttu-id="bd56c-121">Předchozí příklad ukazuje, jak k vykreslení ovládacího prvku pomocí velmi jednoduchá grafická reprezentace.</span><span class="sxs-lookup"><span data-stu-id="bd56c-121">The preceding example demonstrates how to render a control with a very simple graphical representation.</span></span> <span data-ttu-id="bd56c-122">Volá <xref:System.Windows.Forms.Control.OnPaint%2A> metody základní třídy, vytvoří <xref:System.Drawing.Pen> objektu, pomocí kterého se má kreslit a nakonec kreslení na tři tečky v obdélníku určené <xref:System.Windows.Forms.Control.Location%2A> a <xref:System.Windows.Forms.Control.Size%2A> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd56c-122">It calls the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class, it creates a <xref:System.Drawing.Pen> object with which to draw, and finally draws an ellipse in the rectangle determined by the <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Size%2A> of the control.</span></span> <span data-ttu-id="bd56c-123">I když většina vykreslování kód bude složitější než toto, tento příklad ukazuje použití <xref:System.Drawing.Graphics> obsažené v objektu <xref:System.Windows.Forms.PaintEventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="bd56c-123">Although most rendering code will be significantly more complicated than this, this example demonstrates the use of the <xref:System.Drawing.Graphics> object contained within the <xref:System.Windows.Forms.PaintEventArgs> object.</span></span> <span data-ttu-id="bd56c-124">Všimněte si, že pokud se dědí z třídy, která už má grafickou reprezentaci, například <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Button>a nechcete, aby začlenit tohoto vyjádření do vaší vykreslování, neměli by jste volat základní třídy <xref:System.Windows.Forms.Control.OnPaint%2A> Metoda.</span><span class="sxs-lookup"><span data-stu-id="bd56c-124">Note that if you are inheriting from a class that already has a graphical representation, such as <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Button>, and you do not wish to incorporate that representation into your rendering, you should not call your base class's <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
 <span data-ttu-id="bd56c-125">Kód v <xref:System.Windows.Forms.Control.OnPaint%2A> metoda ovládacího prvku se spustí při prvním vykreslení ovládacího prvku a pokaždé, když se aktualizuje.</span><span class="sxs-lookup"><span data-stu-id="bd56c-125">The code in the <xref:System.Windows.Forms.Control.OnPaint%2A> method of your control will execute when the control is first drawn, and whenever it is refreshed.</span></span> <span data-ttu-id="bd56c-126">Aby bylo zajištěno, že pokaždé, když je velikost překreslení ovládacího prvku, přidejte následující řádek do konstruktoru ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="bd56c-126">To ensure that your control is redrawn every time it is resized, add the following line to the constructor of your control:</span></span>  
  
```vb  
SetStyle(ControlStyles.ResizeRedraw, True)  
```  
  
```csharp  
SetStyle(ControlStyles.ResizeRedraw, true);  
```  
  
> [!NOTE]
>  <span data-ttu-id="bd56c-127">Použití <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> vlastnost pro implementaci neobdélníkových ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="bd56c-127">Use the <xref:System.Windows.Forms.Control.Region%2A?displayProperty=nameWithType> property to implement a non-rectangular control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd56c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd56c-128">See also</span></span>

- <xref:System.Windows.Forms.Control.Region%2A>
- <xref:System.Windows.Forms.ControlStyles>
- <xref:System.Drawing.Graphics>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Windows.Forms.PaintEventArgs>
- [<span data-ttu-id="bd56c-129">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="bd56c-129">How to: Create Graphics Objects for Drawing</span></span>](../advanced/how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="bd56c-130">Základní ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="bd56c-130">Constituent Controls</span></span>](constituent-controls.md)
- [<span data-ttu-id="bd56c-131">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="bd56c-131">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
