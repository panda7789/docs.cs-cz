---
title: 'Postupy: Vykreslení obrázků pomocí GDI+'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: fffe1f1052d7323d234985b7e752866f2e89657d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182506"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="6d7eb-102">Postupy: Vykreslení obrázků pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="6d7eb-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="6d7eb-103">Pomocí gdi+ můžete vykreslit obrázky, které existují jako soubory ve vašich aplikacích.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-103">You can use GDI+ to render images that exist as files in your applications.</span></span> <span data-ttu-id="6d7eb-104">To provést vytvořením nového <xref:System.Drawing.Image> objektu <xref:System.Drawing.Bitmap>třídy (například ) vytvořením objektu, <xref:System.Drawing.Graphics> který odkazuje <xref:System.Drawing.Graphics.DrawImage%2A> na kreslicí plochu, kterou chcete použít, a voláním metody objektu. <xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="6d7eb-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="6d7eb-105">Obraz bude namalován na kreslicí plochu reprezentovanou grafickou třídou.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="6d7eb-106">Editor obrázků můžete použít k vytváření a úpravám obrazových souborů v době návrhu a jejich vykreslení pomocí rozhraní GDI+ za běhu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-106">You can use the Image Editor to create and edit image files at design time, and render them with GDI+ at run time.</span></span> <span data-ttu-id="6d7eb-107">Další informace naleznete v [editoru obrázků pro ikony](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="6d7eb-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="6d7eb-108">Vykreslení obrazu pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="6d7eb-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="6d7eb-109">Vytvořte objekt představující obraz, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="6d7eb-110">Tento objekt musí být členem třídy, <xref:System.Drawing.Image>která <xref:System.Drawing.Bitmap> dědí z , například nebo <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="6d7eb-111">Příklad je zobrazen:</span><span class="sxs-lookup"><span data-stu-id="6d7eb-111">An example is shown:</span></span>  
  
    ```vb  
    ' Uses the System.Environment.GetFolderPath to get the path to the
    ' current user's MyPictures folder.  
    Dim myBitmap as New Bitmap _  
       (System.Environment.GetFolderPath _  
          (System.Environment.SpecialFolder.MyPictures))  
    ```  
  
    ```csharp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap myBitmap = new Bitmap  
       (System.Environment.GetFolderPath  
          (System.Environment.SpecialFolder.MyPictures));  
    ```  
  
    ```cpp  
    // Uses the System.Environment.GetFolderPath to get the path to the
    // current user's MyPictures folder.  
    Bitmap^ myBitmap = gcnew Bitmap  
       (System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::MyPictures));  
    ```  
  
2. <span data-ttu-id="6d7eb-112">Vytvořte <xref:System.Drawing.Graphics> objekt, který představuje kreslicí plochu, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="6d7eb-113">Další informace naleznete v [tématu How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="6d7eb-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
    ```vb  
    ' Creates a Graphics object that represents the drawing surface of
    ' Button1.  
    Dim g as Graphics = Button1.CreateGraphics  
    ```  
  
    ```csharp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics g = Button1.CreateGraphics();  
    ```  
  
    ```cpp  
    // Creates a Graphics object that represents the drawing surface of
    // Button1.  
    Graphics^ g = button1->CreateGraphics();  
    ```  
  
3. <span data-ttu-id="6d7eb-114">Volání <xref:System.Drawing.Graphics.DrawImage%2A> grafického objektu k vykreslení obrazu.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="6d7eb-115">Je nutné zadat obrázek, který má být nakreslen, i souřadnice, kde má být nakreslen.</span><span class="sxs-lookup"><span data-stu-id="6d7eb-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6d7eb-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d7eb-116">See also</span></span>

- [<span data-ttu-id="6d7eb-117">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="6d7eb-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="6d7eb-118">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="6d7eb-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="6d7eb-119">Pera, čáry a obdélníky v GDI+</span><span class="sxs-lookup"><span data-stu-id="6d7eb-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="6d7eb-120">Postupy: Kreslení textu v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d7eb-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="6d7eb-121">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6d7eb-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="6d7eb-122">Kreslení čar nebo uzavřených obrázků</span><span class="sxs-lookup"><span data-stu-id="6d7eb-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="6d7eb-123">Editor obrázků pro ikony</span><span class="sxs-lookup"><span data-stu-id="6d7eb-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
