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
ms.openlocfilehash: d591d65904484e33285e5db7aa99760f3e1909d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142430"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a><span data-ttu-id="eb8ca-102">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="eb8ca-102">How to: Create Graphics Objects for Drawing</span></span>
<span data-ttu-id="eb8ca-103">Než budete moci kreslit čáry a tvary, vykreslovat text nebo <xref:System.Drawing.Graphics> zobrazovat obrazy a manipulovat s nimi pomocí GDI+, musíte vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-103">Before you can draw lines and shapes, render text, or display and manipulate images with GDI+, you need to create a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="eb8ca-104">Objekt <xref:System.Drawing.Graphics> představuje kreslicí plochu GDI+ a je objektem, který se používá k vytváření grafických obrazů.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-104">The <xref:System.Drawing.Graphics> object represents a GDI+ drawing surface, and is the object that is used to create graphical images.</span></span>  
  
 <span data-ttu-id="eb8ca-105">Práce s grafikou je dva kroky:</span><span class="sxs-lookup"><span data-stu-id="eb8ca-105">There are two steps in working with graphics:</span></span>  
  
1. <span data-ttu-id="eb8ca-106">Vytvoření <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-106">Creating a <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="eb8ca-107">Použití <xref:System.Drawing.Graphics> objektu k kreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-107">Using the <xref:System.Drawing.Graphics> object to draw lines and shapes, render text, or display and manipulate images.</span></span>  
  
## <a name="creating-a-graphics-object"></a><span data-ttu-id="eb8ca-108">Vytvoření grafického objektu</span><span class="sxs-lookup"><span data-stu-id="eb8ca-108">Creating a Graphics Object</span></span>  
 <span data-ttu-id="eb8ca-109">Grafický objekt lze vytvořit různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-109">A graphics object can be created in a variety of ways.</span></span>  
  
#### <a name="to-create-a-graphics-object"></a><span data-ttu-id="eb8ca-110">Vytvoření grafického objektu</span><span class="sxs-lookup"><span data-stu-id="eb8ca-110">To create a graphics object</span></span>  
  
- <span data-ttu-id="eb8ca-111">Příjem odkazu na grafický objekt jako <xref:System.Windows.Forms.PaintEventArgs> součást <xref:System.Windows.Forms.Control.Paint> v případě formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-111">Receive a reference to a graphics object as part of the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event of a form or control.</span></span> <span data-ttu-id="eb8ca-112">Toje obvykle způsob, jakým získáte odkaz na grafický objekt při vytváření malačního kódu pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-112">This is usually how you obtain a reference to a graphics object when creating painting code for a control.</span></span> <span data-ttu-id="eb8ca-113">Podobně můžete také získat grafický objekt jako vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> při <xref:System.Drawing.Printing.PrintDocument.PrintPage> zpracování události <xref:System.Drawing.Printing.PrintDocument>pro .</span><span class="sxs-lookup"><span data-stu-id="eb8ca-113">Similarly, you can also obtain a graphics object as a property of the <xref:System.Drawing.Printing.PrintPageEventArgs> when handling the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event for a <xref:System.Drawing.Printing.PrintDocument>.</span></span>  
  
     <span data-ttu-id="eb8ca-114">-nebo-</span><span class="sxs-lookup"><span data-stu-id="eb8ca-114">-or-</span></span>  
  
- <span data-ttu-id="eb8ca-115">Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody ovládacího prvku nebo formuláře získat <xref:System.Drawing.Graphics> odkaz na objekt, který představuje výkresovou plochu tohoto ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-115">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span> <span data-ttu-id="eb8ca-116">Tuto metodu použijte, pokud chcete nakreslit formulář nebo ovládací prvek, který již existuje.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-116">Use this method if you want to draw on a form or control that already exists.</span></span>  
  
     <span data-ttu-id="eb8ca-117">-nebo-</span><span class="sxs-lookup"><span data-stu-id="eb8ca-117">-or-</span></span>  
  
- <span data-ttu-id="eb8ca-118">Vytvořte <xref:System.Drawing.Graphics> objekt z libovolného <xref:System.Drawing.Image>objektu, který dědí z .</span><span class="sxs-lookup"><span data-stu-id="eb8ca-118">Create a <xref:System.Drawing.Graphics> object from any object that inherits from <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="eb8ca-119">Tento přístup je užitečný, pokud chcete změnit již existující bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-119">This approach is useful when you want to alter an already existing image.</span></span>  
  
     <span data-ttu-id="eb8ca-120">V následujících částech jsou uvedeny podrobnosti o každém z těchto procesů.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-120">The following sections give details about each of these processes.</span></span>  
  
## <a name="painteventargs-in-the-paint-event-handler"></a><span data-ttu-id="eb8ca-121">PaintEventArgs v obslužné rutině události malby</span><span class="sxs-lookup"><span data-stu-id="eb8ca-121">PaintEventArgs in the Paint Event Handler</span></span>  
 <span data-ttu-id="eb8ca-122">Při programování <xref:System.Windows.Forms.PaintEventHandler> for controls <xref:System.Drawing.Printing.PrintDocument.PrintPage> nebo <xref:System.Drawing.Printing.PrintDocument>for a je grafický objekt k <xref:System.Windows.Forms.PaintEventArgs> dispozici <xref:System.Drawing.Printing.PrintPageEventArgs>jako jedna z vlastností nebo .</span><span class="sxs-lookup"><span data-stu-id="eb8ca-122">When programming the <xref:System.Windows.Forms.PaintEventHandler> for controls or the <xref:System.Drawing.Printing.PrintDocument.PrintPage> for a <xref:System.Drawing.Printing.PrintDocument>, a graphics object is provided as one of the properties of <xref:System.Windows.Forms.PaintEventArgs> or <xref:System.Drawing.Printing.PrintPageEventArgs>.</span></span>  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a><span data-ttu-id="eb8ca-123">Chcete-li získat odkaz na Graphics objekt u PaintEventArgs v paint události</span><span class="sxs-lookup"><span data-stu-id="eb8ca-123">To obtain a reference to a Graphics object from the PaintEventArgs in the Paint event</span></span>  
  
1. <span data-ttu-id="eb8ca-124">Deklarujte <xref:System.Drawing.Graphics> objekt.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-124">Declare the <xref:System.Drawing.Graphics> object.</span></span>  
  
2. <span data-ttu-id="eb8ca-125">Přiřaďte proměnnou <xref:System.Drawing.Graphics> odkazna objekt <xref:System.Windows.Forms.PaintEventArgs>předaný jako součást .</span><span class="sxs-lookup"><span data-stu-id="eb8ca-125">Assign the variable to refer to the <xref:System.Drawing.Graphics> object passed as part of the <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
3. <span data-ttu-id="eb8ca-126">Vložením kódu namalujte formulář nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-126">Insert code to paint the form or control.</span></span>  
  
     <span data-ttu-id="eb8ca-127">Následující příklad ukazuje, jak <xref:System.Drawing.Graphics> odkazovat <xref:System.Windows.Forms.PaintEventArgs> na <xref:System.Windows.Forms.Control.Paint> objekt z v události:</span><span class="sxs-lookup"><span data-stu-id="eb8ca-127">The following example shows how to reference a <xref:System.Drawing.Graphics> object from the <xref:System.Windows.Forms.PaintEventArgs> in the <xref:System.Windows.Forms.Control.Paint> event:</span></span>  
  
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
  
## <a name="creategraphics-method"></a><span data-ttu-id="eb8ca-128">Metoda CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="eb8ca-128">CreateGraphics Method</span></span>  
 <span data-ttu-id="eb8ca-129">Metodu <xref:System.Windows.Forms.Control.CreateGraphics%2A> ovládacího prvku nebo formuláře můžete také použít <xref:System.Drawing.Graphics> k získání odkazu na objekt, který představuje výkresovou plochu tohoto ovládacího prvku nebo formuláře.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-129">You can also use the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of a control or form to obtain a reference to a <xref:System.Drawing.Graphics> object that represents the drawing surface of that control or form.</span></span>  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a><span data-ttu-id="eb8ca-130">Vytvoření objektu Graphics pomocí metody CreateGraphics</span><span class="sxs-lookup"><span data-stu-id="eb8ca-130">To create a Graphics object with the CreateGraphics method</span></span>  
  
- <span data-ttu-id="eb8ca-131">Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formuláře nebo ovládacího prvku, na kterém chcete vykreslit grafiku.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-131">Call the <xref:System.Windows.Forms.Control.CreateGraphics%2A> method of the form or control upon which you want to render graphics.</span></span>  
  
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
  
## <a name="create-from-an-image-object"></a><span data-ttu-id="eb8ca-132">Vytvořit z objektu obrazu</span><span class="sxs-lookup"><span data-stu-id="eb8ca-132">Create from an Image Object</span></span>  
 <span data-ttu-id="eb8ca-133">Kromě toho můžete vytvořit grafický objekt z libovolného <xref:System.Drawing.Image> objektu, který je odvozen z třídy.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-133">Additionally, you can create a graphics object from any object that derives from the <xref:System.Drawing.Image> class.</span></span>  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a><span data-ttu-id="eb8ca-134">Vytvoření objektu Graphics z obrazu</span><span class="sxs-lookup"><span data-stu-id="eb8ca-134">To create a Graphics object from an Image</span></span>  
  
- <span data-ttu-id="eb8ca-135">Volání <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metody, zadání názvu Image proměnné, ze kterého chcete <xref:System.Drawing.Graphics> vytvořit objekt.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-135">Call the <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> method, supplying the name of the Image variable from which you want to create a <xref:System.Drawing.Graphics> object.</span></span>  
  
     <span data-ttu-id="eb8ca-136">Následující příklad ukazuje, jak <xref:System.Drawing.Bitmap> používat objekt:</span><span class="sxs-lookup"><span data-stu-id="eb8ca-136">The following example shows how to use a <xref:System.Drawing.Bitmap> object:</span></span>  
  
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
> <span data-ttu-id="eb8ca-137">Můžete vytvářet <xref:System.Drawing.Graphics> pouze objekty z neindexovaných souborů BMP, například 16bitových, 24bitových a 32bitových souborů BMP.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-137">You can only create <xref:System.Drawing.Graphics> objects from nonindexed .bmp files, such as 16-bit, 24-bit, and 32-bit .bmp files.</span></span> <span data-ttu-id="eb8ca-138">Každý pixel neindexovaných souborů BMP obsahuje barvu, na rozdíl od obrazových bodů indexovaných souborů BMP, které drží index tabulky barev.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-138">Each pixel of nonindexed .bmp files holds a color, in contrast to pixels of indexed .bmp files, which hold an index to a color table.</span></span>  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a><span data-ttu-id="eb8ca-139">Kreslení a manipulace s obrazci a obrazy</span><span class="sxs-lookup"><span data-stu-id="eb8ca-139">Drawing and Manipulating Shapes and Images</span></span>  
 <span data-ttu-id="eb8ca-140">Po vytvoření může <xref:System.Drawing.Graphics> být objekt použit k kreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrazy.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-140">After it is created, a <xref:System.Drawing.Graphics> object may be used to draw lines and shapes, render text, or display and manipulate images.</span></span> <span data-ttu-id="eb8ca-141">Hlavní objekty, které <xref:System.Drawing.Graphics> se používají s objektem jsou:</span><span class="sxs-lookup"><span data-stu-id="eb8ca-141">The principal objects that are used with the <xref:System.Drawing.Graphics> object are:</span></span>  
  
- <span data-ttu-id="eb8ca-142">Třída <xref:System.Drawing.Pen> – Používá se pro kreslení čar, osnovy tvarů nebo vykreslování jiných geometrických reprezentací.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-142">The <xref:System.Drawing.Pen> class—Used for drawing lines, outlining shapes, or rendering other geometric representations.</span></span>  
  
- <span data-ttu-id="eb8ca-143">Třída <xref:System.Drawing.Brush> – Používá se k vyplnění oblastí grafiky, jako jsou vyplněné tvary, obrázky nebo text.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-143">The <xref:System.Drawing.Brush> class—Used for filling areas of graphics, such as filled shapes, images, or text.</span></span>  
  
- <span data-ttu-id="eb8ca-144">Třída <xref:System.Drawing.Font> – Obsahuje popis obrazců, které mají být používány při vykreslování textu.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-144">The <xref:System.Drawing.Font> class—Provides a description of what shapes to use when rendering text.</span></span>  
  
- <span data-ttu-id="eb8ca-145">Struktura <xref:System.Drawing.Color> – Představuje různé barvy, které se mají zobrazit.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-145">The <xref:System.Drawing.Color> structure—Represents the different colors to display.</span></span>  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a><span data-ttu-id="eb8ca-146">Použití vytvořeného objektu Graphics</span><span class="sxs-lookup"><span data-stu-id="eb8ca-146">To use the Graphics object you have created</span></span>  
  
- <span data-ttu-id="eb8ca-147">Spolupracujte s příslušným objektem uvedeným výše a nakreslete, co potřebujete.</span><span class="sxs-lookup"><span data-stu-id="eb8ca-147">Work with the appropriate object listed above to draw what you need.</span></span>  
  
     <span data-ttu-id="eb8ca-148">Další informace najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="eb8ca-148">For more information, see the following topics:</span></span>  
  
    |<span data-ttu-id="eb8ca-149">Chcete-li vykreslit</span><span class="sxs-lookup"><span data-stu-id="eb8ca-149">To render</span></span>|<span data-ttu-id="eb8ca-150">Seznamte se s </span><span class="sxs-lookup"><span data-stu-id="eb8ca-150">See</span></span>|  
    |---------------|---------|  
    |<span data-ttu-id="eb8ca-151">Spojnice</span><span class="sxs-lookup"><span data-stu-id="eb8ca-151">Lines</span></span>|[<span data-ttu-id="eb8ca-152">Postupy: Kreslení čáry ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="eb8ca-152">How to: Draw a Line on a Windows Form</span></span>](how-to-draw-a-line-on-a-windows-form.md)|  
    |<span data-ttu-id="eb8ca-153">Obrazce</span><span class="sxs-lookup"><span data-stu-id="eb8ca-153">Shapes</span></span>|[<span data-ttu-id="eb8ca-154">Postupy: Kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="eb8ca-154">How to: Draw an Outlined Shape</span></span>](how-to-draw-an-outlined-shape.md)|  
    |<span data-ttu-id="eb8ca-155">Text</span><span class="sxs-lookup"><span data-stu-id="eb8ca-155">Text</span></span>|[<span data-ttu-id="eb8ca-156">Postupy: Kreslení textu v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb8ca-156">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)|  
    |<span data-ttu-id="eb8ca-157">Image</span><span class="sxs-lookup"><span data-stu-id="eb8ca-157">Images</span></span>|[<span data-ttu-id="eb8ca-158">Postupy: Vykreslení obrázků pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="eb8ca-158">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a><span data-ttu-id="eb8ca-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb8ca-159">See also</span></span>

- [<span data-ttu-id="eb8ca-160">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="eb8ca-160">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="eb8ca-161">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb8ca-161">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="eb8ca-162">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="eb8ca-162">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="eb8ca-163">Postupy: Vykreslení obrázků pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="eb8ca-163">How to: Render Images with GDI+</span></span>](how-to-render-images-with-gdi.md)
