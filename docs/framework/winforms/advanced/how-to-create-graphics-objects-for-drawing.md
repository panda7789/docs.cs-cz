---
title: 'Postupy: Vytváření grafických objektů pro kreslení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], creating
- images [Windows Forms], creating
- GDI+, creating images
ms.assetid: 162861f9-f050-445e-8abb-b2c43a918b8b
ms.openlocfilehash: 3d3ab62896f6b799cd38a8180b90f33125a9929b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964344"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="9f9fa-102">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="9f9fa-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="9f9fa-103">Než budete moct nakreslit čáry a tvary, vykreslovat text nebo zobrazovat a manipulovat s nimi pomocí GDI+, je potřeba vytvořit <xref:System.Drawing.Graphics> objekt.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="9f9fa-104"><xref:System.Drawing.Graphics> Objekt představuje plochu vykreslování GDI+ a je objekt, který slouží k vytváření grafických obrázků.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="9f9fa-105">Existují dva kroky při práci s grafikou:</span><span class="sxs-lookup"><span data-stu-id="9f9fa-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="9f9fa-106"><xref:System.Drawing.Graphics> Vytvoření objektu.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="9f9fa-107"><xref:System.Drawing.Graphics> Použití objektu k nakreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="9f9fa-108">Vytvoření objektu grafiky</span><span class="sxs-lookup"><span data-stu-id="9f9fa-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="9f9fa-109">Objekt grafiky lze vytvořit různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="9f9fa-110">Vytvoření objektu grafiky</span><span class="sxs-lookup"><span data-stu-id="9f9fa-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="9f9fa-111">Získat odkaz na objekt grafiky jako součást <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> v případě formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="9f9fa-112">To je obvykle způsob, jak získat odkaz na objekt grafiky při vytváření kódu pro vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="9f9fa-113">Podobně můžete také získat objekt grafiky jako vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> při <xref:System.Drawing.Printing.PrintDocument.PrintPage> zpracování události pro <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="9f9fa-114">-nebo-</span><span class="sxs-lookup"><span data-stu-id="9f9fa-114">-or-</span></span>  
  
- <span data-ttu-id="9f9fa-115">Voláním <xref:System.Drawing.Graphics> metody ovládacího prvku nebo formuláře získáte odkaz na objekt, který představuje kreslicí plochu daného ovládacího prvku nebo formuláře. <xref:System.Windows.Forms.Control.CreateGraphics%2A></span><span class="sxs-lookup"><span data-stu-id="9f9fa-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="9f9fa-116">Tuto metodu použijte, chcete-li kreslit na formulář nebo ovládací prvek, který již existuje.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="9f9fa-117">-nebo-</span><span class="sxs-lookup"><span data-stu-id="9f9fa-117">-or-</span></span>  
  
- <span data-ttu-id="9f9fa-118">Vytvořte objekt z libovolného objektu, který dědí z <xref:System.Drawing.Image>. <xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="9f9fa-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="9f9fa-119">Tento přístup je užitečný, když chcete změnit už existující image.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="9f9fa-120">Následující části obsahují podrobné informace o každém z těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="9f9fa-121">PaintEventArgs v obslužné rutině události Paint</span><span class="sxs-lookup"><span data-stu-id="9f9fa-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="9f9fa-122"><xref:System.Windows.Forms.PaintEventHandler> Při programování ovládacích prvků pro ovládací prvky <xref:System.Drawing.Printing.PrintDocument.PrintPage> nebo pro <xref:System.Drawing.Printing.PrintDocument>, <xref:System.Windows.Forms.PaintEventArgs> je objekt Graphics k dispozici jako jedna z vlastností nebo <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="9f9fa-123">Získání odkazu na objekt grafiky z PaintEventArgs v události Paint</span><span class="sxs-lookup"><span data-stu-id="9f9fa-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="9f9fa-124">Deklarujte <xref:System.Drawing.Graphics> objekt.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="9f9fa-125">Přiřaďte proměnnou pro odkaz na <xref:System.Drawing.Graphics> objekt předaný jako součást. <xref:System.Windows.Forms.PaintEventArgs></span><span class="sxs-lookup"><span data-stu-id="9f9fa-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="9f9fa-126">Vložte kód pro vykreslení formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="9f9fa-127">Následující příklad ukazuje, jak odkazovat <xref:System.Drawing.Graphics> na objekt <xref:System.Windows.Forms.PaintEventArgs> z <xref:System.Windows.Forms.Control.Paint> v události:</span><span class="sxs-lookup"><span data-stu-id="9f9fa-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="9f9fa-128">Metoda CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="9f9fa-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="9f9fa-129">Můžete také použít <xref:System.Windows.Forms.Control.CreateGraphics%2A> metodu ovládacího prvku nebo formuláře k získání odkazu <xref:System.Drawing.Graphics> na objekt, který představuje kreslicí plochu daného ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="9f9fa-130">Vytvoření objektu grafiky pomocí metody CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="9f9fa-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="9f9fa-131"><xref:System.Windows.Forms.Control.CreateGraphics%2A> Zavolejte metodu formuláře nebo ovládacího prvku, na který chcete vykreslit grafiku.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="9f9fa-132">Vytvořit z objektu obrázku</span><span class="sxs-lookup"><span data-stu-id="9f9fa-132">Create from an Image Object</span></span>  
 <span data-ttu-id="9f9fa-133">Kromě toho můžete vytvořit objekt grafiky z libovolného objektu, který je odvozen od <xref:System.Drawing.Image> třídy.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="9f9fa-134">Vytvoření objektu grafiky z obrázku</span><span class="sxs-lookup"><span data-stu-id="9f9fa-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="9f9fa-135">Zavolejte metodu a zadejte název proměnné obrázku, ze které chcete <xref:System.Drawing.Graphics> vytvořit objekt. <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="9f9fa-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="9f9fa-136">Následující příklad ukazuje, jak použít <xref:System.Drawing.Bitmap> objekt:</span><span class="sxs-lookup"><span data-stu-id="9f9fa-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="9f9fa-137">Můžete vytvářet <xref:System.Drawing.Graphics> pouze objekty z neindexovaných souborů. bmp, jako jsou 16bitové, 24bitové a 32 bitové soubory. bmp.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="9f9fa-138">Každý pixel neindexovaných souborů. bmp obsahuje barvu na rozdíl od pixelů indexovaných souborů. bmp, které obsahují index pro tabulku barev.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="9f9fa-139">Kreslení a manipulace s obrazci a obrázky</span><span class="sxs-lookup"><span data-stu-id="9f9fa-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="9f9fa-140">Po vytvoření <xref:System.Drawing.Graphics> lze objekt použít k vykreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="9f9fa-141">Objekty zabezpečení, které jsou použity s <xref:System.Drawing.Graphics> objektem, jsou:</span><span class="sxs-lookup"><span data-stu-id="9f9fa-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="9f9fa-142"><xref:System.Drawing.Pen> Třída – používá se pro kreslení čar, sbalení tvarů nebo vykreslování dalších geometrických reprezentací.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="9f9fa-143"><xref:System.Drawing.Brush> Třída – slouží k vyplňování oblastí grafiky, jako jsou například vyplněné tvary, obrázky nebo text.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="9f9fa-144"><xref:System.Drawing.Font> Třída – poskytuje popis toho, co obrazce použít při vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="9f9fa-145"><xref:System.Drawing.Color> Struktura – představuje různé barvy, které se mají zobrazit.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="9f9fa-146">Použití objektu Graphics, který jste vytvořili</span><span class="sxs-lookup"><span data-stu-id="9f9fa-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="9f9fa-147">Pracujte s odpovídajícím objektem uvedeným výše a nakreslete, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="9f9fa-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="9f9fa-148">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9f9fa-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="9f9fa-149">Pro vykreslení</span><span class="sxs-lookup"><span data-stu-id="9f9fa-149">To render</span></span>|<span data-ttu-id="9f9fa-150">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="9f9fa-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="9f9fa-151">Přím</span><span class="sxs-lookup"><span data-stu-id="9f9fa-151">Lines</span></span>|[<span data-ttu-id="9f9fa-152">Postupy: Nakreslit čáru na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="9f9fa-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="9f9fa-153">Obrazce</span><span class="sxs-lookup"><span data-stu-id="9f9fa-153">Shapes</span></span>|[<span data-ttu-id="9f9fa-154">Postupy: Nakreslit obrazec s obrysem</span><span class="sxs-lookup"><span data-stu-id="9f9fa-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="9f9fa-155">Text</span><span class="sxs-lookup"><span data-stu-id="9f9fa-155">Text</span></span>|[<span data-ttu-id="9f9fa-156">Postupy: Nakreslit text na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="9f9fa-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="9f9fa-157">Obrázky</span><span class="sxs-lookup"><span data-stu-id="9f9fa-157">Images</span></span>|[<span data-ttu-id="9f9fa-158">Postupy: Vykreslování imagí pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="9f9fa-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="9f9fa-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f9fa-159">See also</span></span>

- [<span data-ttu-id="9f9fa-160">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="9f9fa-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="9f9fa-161">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f9fa-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="9f9fa-162">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="9f9fa-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="9f9fa-163">Postupy: Vykreslování imagí pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="9f9fa-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
