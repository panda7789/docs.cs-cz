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
ms.openlocfilehash: e038da545bb3f56cc757710bcaa93aa2c86bfa67
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342542"
---
# <a name="how-to-render-images-with-gdi"></a><span data-ttu-id="6b323-102">Postupy: Vykreslení obrázků pomocí GDI+</span><span class="sxs-lookup"><span data-stu-id="6b323-102">How to: Render Images with GDI+</span></span>
<span data-ttu-id="6b323-103">Můžete použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] k vykreslování obrázků, které existují jako soubory ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="6b323-103">You can use [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] to render images that exist as files in your applications.</span></span> <span data-ttu-id="6b323-104">To provedete tak, že vytvoříte nový objekt <xref:System.Drawing.Image> třídy (například <xref:System.Drawing.Bitmap>), vytváření <xref:System.Drawing.Graphics> objekt, který odkazuje na návrhovém povrchu, který chcete použít a volání <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="6b323-104">You do this by creating a new object of an <xref:System.Drawing.Image> class (such as <xref:System.Drawing.Bitmap>), creating a <xref:System.Drawing.Graphics> object that refers to the drawing surface you want to use, and calling the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="6b323-105">Image bude nutné překreslit na návrhovém povrchu reprezentovaný třídou grafiky.</span><span class="sxs-lookup"><span data-stu-id="6b323-105">The image will be painted onto the drawing surface represented by the graphics class.</span></span> <span data-ttu-id="6b323-106">Můžete použít Editor obrázků můžete vytvářet a upravovat soubory obrázků v době návrhu a jejich vykreslení [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] v době běhu.</span><span class="sxs-lookup"><span data-stu-id="6b323-106">You can use the Image Editor to create and edit image files at design time, and render them with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] at run time.</span></span> <span data-ttu-id="6b323-107">Další informace najdete v tématu [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons).</span><span class="sxs-lookup"><span data-stu-id="6b323-107">For more information, see [Image Editor for Icons](/cpp/windows/image-editor-for-icons).</span></span>  
  
### <a name="to-render-an-image-with-gdi"></a><span data-ttu-id="6b323-108">Aby se vykreslil obraz pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="6b323-108">To render an image with GDI+</span></span>  
  
1. <span data-ttu-id="6b323-109">Vytvořte objekt představující obrázek, který chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="6b323-109">Create an object representing the image you want to display.</span></span> <span data-ttu-id="6b323-110">Tento objekt musí být členem třídy, která dědí z <xref:System.Drawing.Image>, jako například <xref:System.Drawing.Bitmap> nebo <xref:System.Drawing.Imaging.Metafile>.</span><span class="sxs-lookup"><span data-stu-id="6b323-110">This object must be a member of a class that inherits from <xref:System.Drawing.Image>, such as <xref:System.Drawing.Bitmap> or <xref:System.Drawing.Imaging.Metafile>.</span></span> <span data-ttu-id="6b323-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6b323-111">An example is shown:</span></span>  
  
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
  
2. <span data-ttu-id="6b323-112">Vytvoření <xref:System.Drawing.Graphics> objekt, který reprezentuje na návrhovém povrchu, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="6b323-112">Create a <xref:System.Drawing.Graphics> object that represents the drawing surface you want to use.</span></span> <span data-ttu-id="6b323-113">Další informace najdete v tématu [jak: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="6b323-113">For more information, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span>  
  
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
  
3. <span data-ttu-id="6b323-114">Volání <xref:System.Drawing.Graphics.DrawImage%2A> objektu grafiky k vykreslení obrázku.</span><span class="sxs-lookup"><span data-stu-id="6b323-114">Call the <xref:System.Drawing.Graphics.DrawImage%2A> of your graphics object to render the image.</span></span> <span data-ttu-id="6b323-115">Musíte zadat obrázek, který se má a souřadnice, kde je potřeba vykreslit.</span><span class="sxs-lookup"><span data-stu-id="6b323-115">You must specify both the image to be drawn, and the coordinates where it is to be drawn.</span></span>  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6b323-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b323-116">See also</span></span>

- [<span data-ttu-id="6b323-117">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="6b323-117">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="6b323-118">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="6b323-118">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="6b323-119">Pera, čáry a obdélníky v GDI+</span><span class="sxs-lookup"><span data-stu-id="6b323-119">Pens, Lines, and Rectangles in GDI+</span></span>](pens-lines-and-rectangles-in-gdi.md)
- [<span data-ttu-id="6b323-120">Postupy: Vykreslení textu ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="6b323-120">How to: Draw Text on a Windows Form</span></span>](how-to-draw-text-on-a-windows-form.md)
- [<span data-ttu-id="6b323-121">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b323-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="6b323-122">Kreslení čar nebo uzavřených obrázků</span><span class="sxs-lookup"><span data-stu-id="6b323-122">Drawing Lines or Closed Figures</span></span>](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [<span data-ttu-id="6b323-123">Editor obrázků pro ikony</span><span class="sxs-lookup"><span data-stu-id="6b323-123">Image Editor for Icons</span></span>](/cpp/windows/image-editor-for-icons)
