---
title: "Postupy: Vytváření grafických objektů pro kreslení"
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
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72f1af49a5c64395e018707d1f71cc0feaa2d22c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="82d55-102">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="82d55-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="82d55-103">Předtím, než můžete kreslení čar a tvarů, vykreslení text, nebo zobrazit a pracovat s obrázky s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], je nutné vytvořit <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="82d55-103">Before you can draw lines and shapes, render text, or display and manipulate images with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="82d55-104"><xref:System.Drawing.Graphics> Objektu představuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení prostor a je objekt, který se používá k vytvoření grafické bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="82d55-104">The <xref:System.Drawing.Graphics> object represents a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="82d55-105">Při práci s grafiky existují dva kroky:</span><span class="sxs-lookup"><span data-stu-id="82d55-105">There are two steps in working with graphics:</span></span>  
  
1.  <span data-ttu-id="82d55-106">Vytváření <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="82d55-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="82d55-107">Pomocí <xref:System.Drawing.Graphics> objekt, který chcete kreslení čar a tvarů, vykreslení text, nebo zobrazit a pracovat s obrázky.</span><span class="sxs-lookup"><span data-stu-id="82d55-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="82d55-108">Vytvoření objektu grafiky</span><span class="sxs-lookup"><span data-stu-id="82d55-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="82d55-109">Objekt grafiky lze vytvořit v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="82d55-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="82d55-110">Chcete-li vytvořit objekt grafiky</span><span class="sxs-lookup"><span data-stu-id="82d55-110">To create a graphics object</span></span>  
  
-   <span data-ttu-id="82d55-111">Získat odkaz na objekt grafiky jako součást <xref:System.Windows.Forms.PaintEventArgs> v <xref:System.Windows.Forms.Control.Paint> událost formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="82d55-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="82d55-112">To je obvykle jak získat odkaz na objekt grafiky při vytváření kódu vykreslování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="82d55-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="82d55-113">Podobně můžete také získat objekt grafiky jako vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> při zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí pro <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="82d55-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="82d55-114">-nebo-</span><span class="sxs-lookup"><span data-stu-id="82d55-114">-or-</span></span>  
  
-   <span data-ttu-id="82d55-115">Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda ovládacího prvku nebo formuláře získat odkaz na <xref:System.Drawing.Graphics> objekt, který reprezentuje kreslicí plochy tohoto ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="82d55-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="82d55-116">Tuto metodu použijte, pokud chcete k vykreslení na formulář nebo ovládací prvek, který již existuje.</span><span class="sxs-lookup"><span data-stu-id="82d55-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="82d55-117">-nebo-</span><span class="sxs-lookup"><span data-stu-id="82d55-117">-or-</span></span>  
  
-   <span data-ttu-id="82d55-118">Vytvoření <xref:System.Drawing.Graphics> objekt z libovolného objektu, který dědí z <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="82d55-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="82d55-119">Tento přístup je užitečné, pokud chcete změnit již existující bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="82d55-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="82d55-120">Následujících oddílech najdete podrobnosti o každém z těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="82d55-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="82d55-121">PaintEventArgs v obslužné rutině události Malování</span><span class="sxs-lookup"><span data-stu-id="82d55-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="82d55-122">Při programování <xref:System.Windows.Forms.PaintEventHandler> pro ovládací prvky nebo <xref:System.Drawing.Printing.PrintDocument.PrintPage> pro <xref:System.Drawing.Printing.PrintDocument>, objekt grafiky je k dispozici jako jedna z vlastností <xref:System.Windows.Forms.PaintEventArgs> nebo <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="82d55-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="82d55-123">Chcete-li získat odkaz na objekt grafiky z PaintEventArgs v událost Malování</span><span class="sxs-lookup"><span data-stu-id="82d55-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1.  <span data-ttu-id="82d55-124">Deklarovat <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="82d55-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2.  <span data-ttu-id="82d55-125">Přiřaďte proměnnou odkazovat na <xref:System.Drawing.Graphics> objekt předaný v rámci <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="82d55-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3.  <span data-ttu-id="82d55-126">Vložení kódu k vyplnění formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="82d55-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="82d55-127">Následující příklad ukazuje, jak odkazovat <xref:System.Drawing.Graphics> objektu z <xref:System.Windows.Forms.PaintEventArgs> v <xref:System.Windows.Forms.Control.Paint> událostí:</span><span class="sxs-lookup"><span data-stu-id="82d55-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
    ```vb  
    Private Sub Form1_Paint(sender As Object, pe As PaintEventArgs) Handles _  
       MyBase.Paint  
       ' Declares the Graphics object and sets it to the Graphics object  
       ' supplied in the PaintEventArgs.  
       Dim g As Graphics = pe.Graphics  
       ' Insert code to paint the form here.  
    End Sub  
    ```  
  
    ```csharp  
    private void Form1_Paint(object sender,   
       System.Windows.Forms.PaintEventArgs pe)   
    {  
       // Declares the Graphics object and sets it to the Graphics object  
       // supplied in the PaintEventArgs.  
       Graphics g = pe.Graphics;  
       // Insert code to paint the form here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void Form1_Paint(System::Object ^ sender,  
          System::Windows::Forms::PaintEventArgs ^ pe)  
       {  
          // Declares the Graphics object and sets it to the Graphics object  
          // supplied in the PaintEventArgs.  
          Graphics ^ g = pe->Graphics;  
          // Insert code to paint the form here.  
       }  
    ```  
  
## <a name="creategraphics-method"></a><span data-ttu-id="82d55-128">CreateGraphics – metoda</span><span class="sxs-lookup"><span data-stu-id="82d55-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="82d55-129">Můžete také <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda ovládacího prvku nebo formuláře získat odkaz na <xref:System.Drawing.Graphics> objekt, který reprezentuje kreslicí plochy tohoto ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="82d55-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="82d55-130">Chcete-li vytvořit objekt grafiky s metodou CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="82d55-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
-   <span data-ttu-id="82d55-131">Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda formuláře nebo ovládacího prvku, na který chcete vykreslit grafiky.</span><span class="sxs-lookup"><span data-stu-id="82d55-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
    ```vb  
    Dim g as Graphics  
    ' Sets g to a Graphics object representing the drawing surface of the  
    ' control or form g is a member of.  
    g = Me.CreateGraphics  
    ```  
  
    ```csharp  
    Graphics g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this.CreateGraphics();  
    ```  
  
    ```cpp  
    Graphics ^ g;  
    // Sets g to a graphics object representing the drawing surface of the  
    // control or form g is a member of.  
    g = this->CreateGraphics();  
    ```  
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="82d55-132">Vytvoření z bitové kopie objektu</span><span class="sxs-lookup"><span data-stu-id="82d55-132">Create from an Image Object</span></span>  
 <span data-ttu-id="82d55-133">Kromě toho můžete vytvořit objekt grafiky z libovolného objektu, která je odvozena z <xref:System.Drawing.Image> třídy.</span><span class="sxs-lookup"><span data-stu-id="82d55-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="82d55-134">Chcete-li vytvořit objekt grafiky z bitové kopie</span><span class="sxs-lookup"><span data-stu-id="82d55-134">To create a Graphics object from an Image</span></span>  
  
-   <span data-ttu-id="82d55-135">Volání <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metodu název proměnné bitové kopie, ze kterého chcete vytvořit <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="82d55-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="82d55-136">Následující příklad ukazuje, jak používat <xref:System.Drawing.Bitmap> objektu:</span><span class="sxs-lookup"><span data-stu-id="82d55-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
    ```vb  
    Dim myBitmap as New Bitmap("C:\Documents and Settings\Joe\Pics\myPic.bmp")  
    Dim g as Graphics = Graphics.FromImage(myBitmap)  
    ```  
  
    ```csharp  
    Bitmap myBitmap = new Bitmap(@"C:\Documents and   
       Settings\Joe\Pics\myPic.bmp");  
    Graphics g = Graphics.FromImage(myBitmap);  
    ```  
  
    ```cpp  
    Bitmap ^ myBitmap = gcnew  
       Bitmap("D:\\Documents and Settings\\Joe\\Pics\\myPic.bmp");  
    Graphics ^ g = Graphics::FromImage(myBitmap);  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="82d55-137">Můžete vytvořit pouze <xref:System.Drawing.Graphics> objekty z neindexované .bmp soubory, jako jsou soubory .bmp 16bitové, 24bitový a 32bitové verze.</span><span class="sxs-lookup"><span data-stu-id="82d55-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="82d55-138">Každý pixel soubory .bmp neindexované obsahuje barvu, na rozdíl od pixelů indexované .bmp souborů, které podržte index k tabulce barev.</span><span class="sxs-lookup"><span data-stu-id="82d55-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
-  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="82d55-139">Kreslení a manipulace s nimi tvarů a bitové kopie</span><span class="sxs-lookup"><span data-stu-id="82d55-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="82d55-140">Po vytvoření <xref:System.Drawing.Graphics> objekt může sloužit k kreslení čar a tvarů, vykreslení text, nebo zobrazit a pracovat s obrázky.</span><span class="sxs-lookup"><span data-stu-id="82d55-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="82d55-141">Hlavní objekty, které se používají s <xref:System.Drawing.Graphics> objekt jsou:</span><span class="sxs-lookup"><span data-stu-id="82d55-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
-   <span data-ttu-id="82d55-142"><xref:System.Drawing.Pen> Třída – používat pro kreslení čar, osnovy tvarů nebo jiných geometrickou reprezentace vykreslování.</span><span class="sxs-lookup"><span data-stu-id="82d55-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
-   <span data-ttu-id="82d55-143"><xref:System.Drawing.Brush> Třída – použít pro naplnění oblastí grafiky, jako je například vyplněné tvary, Image nebo text.</span><span class="sxs-lookup"><span data-stu-id="82d55-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
-   <span data-ttu-id="82d55-144"><xref:System.Drawing.Font> Třída – obsahuje popis co obrazce pro použití při vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="82d55-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
-   <span data-ttu-id="82d55-145"><xref:System.Drawing.Color> Struktura – představuje různé barvy k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="82d55-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="82d55-146">Použití grafických objektu, který jste vytvořili</span><span class="sxs-lookup"><span data-stu-id="82d55-146">To use the Graphics object you have created</span></span>  
  
-   <span data-ttu-id="82d55-147">Pracovat na příslušný objekt uvedené výše k vykreslení, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="82d55-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="82d55-148">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="82d55-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="82d55-149">K vykreslení</span><span class="sxs-lookup"><span data-stu-id="82d55-149">To render</span></span>|<span data-ttu-id="82d55-150">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="82d55-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="82d55-151">řádky</span><span class="sxs-lookup"><span data-stu-id="82d55-151">Lines</span></span>|[<span data-ttu-id="82d55-152">Postupy: kreslení čáry ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="82d55-152">How to: Draw a Line on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="82d55-153">Obrazce</span><span class="sxs-lookup"><span data-stu-id="82d55-153">Shapes</span></span>|[<span data-ttu-id="82d55-154">Postupy: kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="82d55-154">How to: Draw an Outlined Shape</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="82d55-155">Text</span><span class="sxs-lookup"><span data-stu-id="82d55-155">Text</span></span>|[<span data-ttu-id="82d55-156">Postupy: kreslení textu ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="82d55-156">How to: Draw Text on a Windows Form</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="82d55-157">Obrázky</span><span class="sxs-lookup"><span data-stu-id="82d55-157">Images</span></span>|[<span data-ttu-id="82d55-158">Postupy: vykreslení obrázků pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="82d55-158">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="82d55-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="82d55-159">See Also</span></span>  
 [<span data-ttu-id="82d55-160">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="82d55-160">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="82d55-161">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82d55-161">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="82d55-162">Čar, křivek a obrazců</span><span class="sxs-lookup"><span data-stu-id="82d55-162">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="82d55-163">Postupy: vykreslení obrázků pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="82d55-163">How to: Render Images with GDI+</span></span>](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
