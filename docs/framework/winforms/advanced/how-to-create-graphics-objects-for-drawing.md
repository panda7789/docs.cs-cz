---
title: 'Postupy: Vytváření grafických objektů pro kreslení'
description: Naučte se vytvořit grafický objekt, který potřebujete k nakreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s imagemi pomocí GDI+.
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
ms.openlocfilehash: 1a0884c1e9956dc6f4608e32372deeea24ef4670
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903204"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="0b7ba-103">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="0b7ba-103">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="0b7ba-104">Než budete moct nakreslit čáry a tvary, vykreslovat text nebo zobrazovat a manipulovat s nimi pomocí GDI+, je potřeba vytvořit <xref:System.Drawing.Graphics> objekt.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-104">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="0b7ba-105"><xref:System.Drawing.Graphics>Objekt představuje plochu vykreslování GDI+ a je objekt, který slouží k vytváření grafických obrázků.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-105">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="0b7ba-106">Existují dva kroky při práci s grafikou:</span><span class="sxs-lookup"><span data-stu-id="0b7ba-106">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="0b7ba-107">Vytvoření <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-107">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="0b7ba-108">Použití <xref:System.Drawing.Graphics> objektu k nakreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-108">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="0b7ba-109">Vytvoření objektu grafiky</span><span class="sxs-lookup"><span data-stu-id="0b7ba-109">Creating a Graphics Object</span></span>  
 <span data-ttu-id="0b7ba-110">Objekt grafiky lze vytvořit různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-110">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="0b7ba-111">Vytvoření objektu grafiky</span><span class="sxs-lookup"><span data-stu-id="0b7ba-111">To create a graphics object</span></span>  
  
- <span data-ttu-id="0b7ba-112">Získat odkaz na objekt grafiky jako součást <xref:System.Windows.Forms.PaintEventArgs> v <xref:System.Windows.Forms.Control.Paint> případě formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-112">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="0b7ba-113">To je obvykle způsob, jak získat odkaz na objekt grafiky při vytváření kódu pro vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-113">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="0b7ba-114">Podobně můžete také získat objekt grafiky jako vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> při zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> události pro <xref:System.Drawing.Printing.PrintDocument> .</span><span class="sxs-lookup"><span data-stu-id="0b7ba-114">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="0b7ba-115">-nebo-</span><span class="sxs-lookup"><span data-stu-id="0b7ba-115">-or-</span></span>  
  
- <span data-ttu-id="0b7ba-116">Voláním <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody ovládacího prvku nebo formuláře získáte odkaz na <xref:System.Drawing.Graphics> objekt, který představuje kreslicí plochu daného ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-116">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="0b7ba-117">Tuto metodu použijte, chcete-li kreslit na formulář nebo ovládací prvek, který již existuje.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-117">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="0b7ba-118">-nebo-</span><span class="sxs-lookup"><span data-stu-id="0b7ba-118">-or-</span></span>  
  
- <span data-ttu-id="0b7ba-119">Vytvořte <xref:System.Drawing.Graphics> objekt z libovolného objektu, který dědí z <xref:System.Drawing.Image> .</span><span class="sxs-lookup"><span data-stu-id="0b7ba-119">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="0b7ba-120">Tento přístup je užitečný, když chcete změnit už existující image.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-120">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="0b7ba-121">Následující části obsahují podrobné informace o každém z těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-121">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="0b7ba-122">PaintEventArgs v obslužné rutině události Paint</span><span class="sxs-lookup"><span data-stu-id="0b7ba-122">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="0b7ba-123">Při programování <xref:System.Windows.Forms.PaintEventHandler> ovládacích prvků pro ovládací prvky nebo <xref:System.Drawing.Printing.PrintDocument.PrintPage> pro <xref:System.Drawing.Printing.PrintDocument> , je objekt Graphics k dispozici jako jedna z vlastností <xref:System.Windows.Forms.PaintEventArgs> nebo <xref:System.Drawing.Printing.PrintPageEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="0b7ba-123">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="0b7ba-124">Získání odkazu na objekt grafiky z PaintEventArgs v události Paint</span><span class="sxs-lookup"><span data-stu-id="0b7ba-124">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="0b7ba-125">Deklarujte <xref:System.Drawing.Graphics> objekt.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-125">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="0b7ba-126">Přiřaďte proměnnou pro odkaz na <xref:System.Drawing.Graphics> objekt předaný jako součást <xref:System.Windows.Forms.PaintEventArgs> .</span><span class="sxs-lookup"><span data-stu-id="0b7ba-126">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="0b7ba-127">Vložte kód pro vykreslení formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-127">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="0b7ba-128">Následující příklad ukazuje, jak odkazovat na <xref:System.Drawing.Graphics> objekt z v <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> události:</span><span class="sxs-lookup"><span data-stu-id="0b7ba-128">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="0b7ba-129">Metoda CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="0b7ba-129">CreateGraphics Method</span></span>  
 <span data-ttu-id="0b7ba-130">Můžete také použít <xref:System.Windows.Forms.Control.CreateGraphics%2A> metodu ovládacího prvku nebo formuláře k získání odkazu na <xref:System.Drawing.Graphics> objekt, který představuje kreslicí plochu daného ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-130">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="0b7ba-131">Vytvoření objektu grafiky pomocí metody CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="0b7ba-131">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="0b7ba-132">Zavolejte <xref:System.Windows.Forms.Control.CreateGraphics%2A> metodu formuláře nebo ovládacího prvku, na který chcete vykreslit grafiku.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-132">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="0b7ba-133">Vytvořit z objektu obrázku</span><span class="sxs-lookup"><span data-stu-id="0b7ba-133">Create from an Image Object</span></span>  
 <span data-ttu-id="0b7ba-134">Kromě toho můžete vytvořit objekt grafiky z libovolného objektu, který je odvozen od <xref:System.Drawing.Image> třídy.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-134">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="0b7ba-135">Vytvoření objektu grafiky z obrázku</span><span class="sxs-lookup"><span data-stu-id="0b7ba-135">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="0b7ba-136">Zavolejte <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metodu a zadejte název proměnné obrázku, ze které chcete vytvořit <xref:System.Drawing.Graphics> objekt.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-136">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="0b7ba-137">Následující příklad ukazuje, jak použít <xref:System.Drawing.Bitmap> objekt:</span><span class="sxs-lookup"><span data-stu-id="0b7ba-137">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="0b7ba-138">Můžete vytvářet pouze <xref:System.Drawing.Graphics> objekty z neindexovaných souborů. bmp, jako jsou 16bitové, 24bitové a 32 bitové soubory. bmp.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-138">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="0b7ba-139">Každý pixel neindexovaných souborů. bmp obsahuje barvu na rozdíl od pixelů indexovaných souborů. bmp, které obsahují index pro tabulku barev.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-139">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="0b7ba-140">Kreslení a manipulace s obrazci a obrázky</span><span class="sxs-lookup"><span data-stu-id="0b7ba-140">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="0b7ba-141">Po vytvoření <xref:System.Drawing.Graphics> lze objekt použít k vykreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-141">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="0b7ba-142">Objekty zabezpečení, které jsou použity s <xref:System.Drawing.Graphics> objektem, jsou:</span><span class="sxs-lookup"><span data-stu-id="0b7ba-142">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="0b7ba-143"><xref:System.Drawing.Pen>Třída – používá se pro kreslení čar, sbalení tvarů nebo vykreslování dalších geometrických reprezentací.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-143">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="0b7ba-144"><xref:System.Drawing.Brush>Třída – slouží k vyplňování oblastí grafiky, jako jsou například vyplněné tvary, obrázky nebo text.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-144">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="0b7ba-145"><xref:System.Drawing.Font>Třída – poskytuje popis toho, co obrazce použít při vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-145">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="0b7ba-146"><xref:System.Drawing.Color>Struktura – představuje různé barvy, které se mají zobrazit.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-146">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="0b7ba-147">Použití objektu Graphics, který jste vytvořili</span><span class="sxs-lookup"><span data-stu-id="0b7ba-147">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="0b7ba-148">Pracujte s odpovídajícím objektem uvedeným výše a nakreslete, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="0b7ba-148">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="0b7ba-149">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="0b7ba-149">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="0b7ba-150">Pro vykreslení</span><span class="sxs-lookup"><span data-stu-id="0b7ba-150">To render</span></span>|<span data-ttu-id="0b7ba-151">Seznamte se s </span><span class="sxs-lookup"><span data-stu-id="0b7ba-151">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="0b7ba-152">Spojnice</span><span class="sxs-lookup"><span data-stu-id="0b7ba-152">Lines</span></span>|[<span data-ttu-id="0b7ba-153">Postupy: Kreslení čáry ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="0b7ba-153">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="0b7ba-154">Obrazce</span><span class="sxs-lookup"><span data-stu-id="0b7ba-154">Shapes</span></span>|[<span data-ttu-id="0b7ba-155">Postupy: Kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="0b7ba-155">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="0b7ba-156">Text</span><span class="sxs-lookup"><span data-stu-id="0b7ba-156">Text</span></span>|[<span data-ttu-id="0b7ba-157">Postupy: Kreslení textu v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b7ba-157">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="0b7ba-158">Obrázky</span><span class="sxs-lookup"><span data-stu-id="0b7ba-158">Images</span></span>|[<span data-ttu-id="0b7ba-159">Postupy: Vykreslení obrázků pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="0b7ba-159">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="0b7ba-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b7ba-160">See also</span></span>

- [<span data-ttu-id="0b7ba-161">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="0b7ba-161">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="0b7ba-162">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0b7ba-162">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="0b7ba-163">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="0b7ba-163">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="0b7ba-164">Postupy: Vykreslení obrázků pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="0b7ba-164">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
