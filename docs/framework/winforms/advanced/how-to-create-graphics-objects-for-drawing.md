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
ms.openlocfilehash: 79eae4d37c056fc95ac73c78e00dd1a2b68bcd24
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324198"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="54faa-102">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="54faa-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="54faa-103">Předtím, než můžete kreslení čar a obrazců, vykreslení textu, nebo zobrazení a manipulaci s obrázky s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], je potřeba vytvořit <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="54faa-103">Before you can draw lines and shapes, render text, or display and manipulate images with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="54faa-104"><xref:System.Drawing.Graphics> Objekt představuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení ploše a je objekt, který se používá k vytvoření grafické obrázky.</span><span class="sxs-lookup"><span data-stu-id="54faa-104">The <xref:System.Drawing.Graphics> object represents a [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="54faa-105">Při práci s grafikou existují dva kroky:</span><span class="sxs-lookup"><span data-stu-id="54faa-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="54faa-106">Vytváření <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="54faa-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="54faa-107">Použití <xref:System.Drawing.Graphics> objektů pro kreslení čar a obrazců, vykreslení textu, nebo zobrazení a manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="54faa-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="54faa-108">Vytvoření objektu grafiky</span><span class="sxs-lookup"><span data-stu-id="54faa-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="54faa-109">Grafický objekt můžete vytvořit mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="54faa-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="54faa-110">Chcete-li vytvořit objekt grafiky</span><span class="sxs-lookup"><span data-stu-id="54faa-110">To create a graphics object</span></span>  
  
-   <span data-ttu-id="54faa-111">Jako součást, zobrazí se odkaz na objekt grafiky <xref:System.Windows.Forms.PaintEventArgs> v <xref:System.Windows.Forms.Control.Paint> události formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="54faa-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="54faa-112">To je obvykle získání odkazu na objekt grafiky při vytváření Malování kódu pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="54faa-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="54faa-113">Podobně můžete získat také grafický objekt jako vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> při zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí pro <xref:System.Drawing.Printing.PrintDocument>.</span><span class="sxs-lookup"><span data-stu-id="54faa-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="54faa-114">-nebo-</span><span class="sxs-lookup"><span data-stu-id="54faa-114">-or-</span></span>  
  
-   <span data-ttu-id="54faa-115">Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> ovládacího prvku nebo formuláře k získání odkazu na metodu <xref:System.Drawing.Graphics> objekt, který reprezentuje na návrhovém povrchu tohoto ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="54faa-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="54faa-116">Tuto metodu použijte, pokud chcete vykreslovat na formulář nebo ovládací prvek, který již existuje.</span><span class="sxs-lookup"><span data-stu-id="54faa-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="54faa-117">-nebo-</span><span class="sxs-lookup"><span data-stu-id="54faa-117">-or-</span></span>  
  
-   <span data-ttu-id="54faa-118">Vytvoření <xref:System.Drawing.Graphics> objekt z libovolného objektu, která dědí z <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="54faa-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="54faa-119">Tento přístup je užitečný, pokud chcete změnit již existující image.</span><span class="sxs-lookup"><span data-stu-id="54faa-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="54faa-120">Následující části obsahují podrobné informace o každé z těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="54faa-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="54faa-121">PaintEventArgs v obslužné rutině události Malování</span><span class="sxs-lookup"><span data-stu-id="54faa-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="54faa-122">Při programování <xref:System.Windows.Forms.PaintEventHandler> pro ovládací prvky nebo <xref:System.Drawing.Printing.PrintDocument.PrintPage> pro <xref:System.Drawing.Printing.PrintDocument>, grafický objekt je k dispozici jako jedna z vlastností objektu <xref:System.Windows.Forms.PaintEventArgs> nebo <xref:System.Drawing.Printing.PrintPageEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="54faa-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="54faa-123">K získání odkazu na objekt grafiky z PaintEventArgs v událost malby</span><span class="sxs-lookup"><span data-stu-id="54faa-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="54faa-124">Deklarovat <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="54faa-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="54faa-125">Přiřazení proměnné odkazovat <xref:System.Drawing.Graphics> objekt předán jako součást <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="54faa-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="54faa-126">Vložte kód pro vykreslení formulář nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="54faa-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="54faa-127">Následující příklad ukazuje způsob vytvoření odkazu <xref:System.Drawing.Graphics> objektu z <xref:System.Windows.Forms.PaintEventArgs> v <xref:System.Windows.Forms.Control.Paint> události:</span><span class="sxs-lookup"><span data-stu-id="54faa-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="54faa-128">Metodu CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="54faa-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="54faa-129">Můžete také použít <xref:System.Windows.Forms.Control.CreateGraphics%2A> ovládacího prvku nebo formuláře k získání odkazu na metodu <xref:System.Drawing.Graphics> objekt, který reprezentuje na návrhovém povrchu tohoto ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="54faa-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="54faa-130">Chcete-li vytvořit grafický objekt s metodu CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="54faa-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
-   <span data-ttu-id="54faa-131">Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formuláře nebo ovládacího prvku, na který chcete vykreslit grafiky.</span><span class="sxs-lookup"><span data-stu-id="54faa-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="54faa-132">Vytvořit z Image objektu</span><span class="sxs-lookup"><span data-stu-id="54faa-132">Create from an Image Object</span></span>  
 <span data-ttu-id="54faa-133">Kromě toho můžete vytvořit grafický objekt z libovolného objektu, která je odvozena od <xref:System.Drawing.Image> třídy.</span><span class="sxs-lookup"><span data-stu-id="54faa-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="54faa-134">Chcete-li vytvořit objekt grafiky z bitové kopie</span><span class="sxs-lookup"><span data-stu-id="54faa-134">To create a Graphics object from an Image</span></span>  
  
-   <span data-ttu-id="54faa-135">Volání <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metodu název proměnné Image, ze kterého chcete vytvořit <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="54faa-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="54faa-136">Následující příklad ukazuje způsob použití <xref:System.Drawing.Bitmap> objektu:</span><span class="sxs-lookup"><span data-stu-id="54faa-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
>  <span data-ttu-id="54faa-137">Můžete vytvořit pouze <xref:System.Drawing.Graphics> objekty ze souborů neindexované .bmp, jako jsou například soubory .bmp 16-bit, 24 bitů a 32-bit.</span><span class="sxs-lookup"><span data-stu-id="54faa-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="54faa-138">Každý pixel neindexované BMP obsahuje barvu, na rozdíl od indexované .bmp soubory, které uložení indexu tabulky barev v pixelech.</span><span class="sxs-lookup"><span data-stu-id="54faa-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="54faa-139">Kreslení a manipulace s nimi obrazce a obrázky</span><span class="sxs-lookup"><span data-stu-id="54faa-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="54faa-140">Po jeho vytvoření, <xref:System.Drawing.Graphics> objekt slouží k vykreslení čar a obrazců, vykreslení textu, nebo zobrazení a manipulaci s imagí.</span><span class="sxs-lookup"><span data-stu-id="54faa-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="54faa-141">Instanční objekty, které se používají s <xref:System.Drawing.Graphics> objektu jsou:</span><span class="sxs-lookup"><span data-stu-id="54faa-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
-   <span data-ttu-id="54faa-142"><xref:System.Drawing.Pen> Třídy – používat pro kreslení čar, osnovy obrazce nebo jiné geometrické reprezentace vykreslování.</span><span class="sxs-lookup"><span data-stu-id="54faa-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
-   <span data-ttu-id="54faa-143"><xref:System.Drawing.Brush> Třídy – používané pro vyplnění oblasti grafiky, jako je například vyplněné obrazce, Image nebo text.</span><span class="sxs-lookup"><span data-stu-id="54faa-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
-   <span data-ttu-id="54faa-144"><xref:System.Drawing.Font> Třídy – popisuje, co budou použity při generování text obrazce.</span><span class="sxs-lookup"><span data-stu-id="54faa-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
-   <span data-ttu-id="54faa-145"><xref:System.Drawing.Color> Struktura – představuje různé barvy pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="54faa-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="54faa-146">Použití objektu grafiky, které jste vytvořili</span><span class="sxs-lookup"><span data-stu-id="54faa-146">To use the Graphics object you have created</span></span>  
  
-   <span data-ttu-id="54faa-147">Práce s odpovídající objekt uvedené výše, chcete-li nakreslit, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="54faa-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="54faa-148">Další informace naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="54faa-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="54faa-149">K vykreslení</span><span class="sxs-lookup"><span data-stu-id="54faa-149">To render</span></span>|<span data-ttu-id="54faa-150">Další informace naleznete v tématu</span><span class="sxs-lookup"><span data-stu-id="54faa-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="54faa-151">řádky</span><span class="sxs-lookup"><span data-stu-id="54faa-151">Lines</span></span>|[<span data-ttu-id="54faa-152">Postupy: Nakreslit čáru na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="54faa-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="54faa-153">Obrazce</span><span class="sxs-lookup"><span data-stu-id="54faa-153">Shapes</span></span>|[<span data-ttu-id="54faa-154">Postupy: Kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="54faa-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="54faa-155">Text</span><span class="sxs-lookup"><span data-stu-id="54faa-155">Text</span></span>|[<span data-ttu-id="54faa-156">Postupy: Vykreslení textu ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="54faa-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="54faa-157">Obrázky</span><span class="sxs-lookup"><span data-stu-id="54faa-157">Images</span></span>|[<span data-ttu-id="54faa-158">Postupy: Vykreslení obrázků pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="54faa-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="54faa-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54faa-159">See also</span></span>

- [<span data-ttu-id="54faa-160">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="54faa-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="54faa-161">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="54faa-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="54faa-162">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="54faa-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="54faa-163">Postupy: Vykreslení obrázků pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="54faa-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
