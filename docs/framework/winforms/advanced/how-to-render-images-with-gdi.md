---
title: 'Postupy: Vykreslení obrázků pomocí GDI +'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], creating
- GDI+, rendering existing images
ms.assetid: c128b79a-3e31-47d8-9e66-3470f570a056
ms.openlocfilehash: d2c626f46862e5fdc7c51b509a6419a3d67c4102
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702825"
---
# <a name="how-to-render-images-with-gdi"></a>Postupy: Vykreslení obrázků pomocí GDI +
Můžete použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] k vykreslování obrázků, které existují jako soubory ve svých aplikacích. To provedete tak, že vytvoříte nový objekt <xref:System.Drawing.Image> třídy (například <xref:System.Drawing.Bitmap>), vytváření <xref:System.Drawing.Graphics> objekt, který odkazuje na návrhovém povrchu, který chcete použít a volání <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu. Image bude nutné překreslit na návrhovém povrchu reprezentovaný třídou grafiky. Můžete použít Editor obrázků můžete vytvářet a upravovat soubory obrázků v době návrhu a jejich vykreslení [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] v době běhu. Další informace najdete v tématu [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Aby se vykreslil obraz pomocí GDI +  
  
1.  Vytvořte objekt představující obrázek, který chcete zobrazit. Tento objekt musí být členem třídy, která dědí z <xref:System.Drawing.Image>, jako například <xref:System.Drawing.Bitmap> nebo <xref:System.Drawing.Imaging.Metafile>. Příklad:  
  
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
  
2.  Vytvoření <xref:System.Drawing.Graphics> objekt, který reprezentuje na návrhovém povrchu, který chcete použít. Další informace najdete v tématu [jak: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3.  Volání <xref:System.Drawing.Graphics.DrawImage%2A> objektu grafiky k vykreslení obrázku. Musíte zadat obrázek, který se má a souřadnice, kde je potřeba vykreslit.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Postupy: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md)
- [Pera, čáry a obdélníky v GDI+](pens-lines-and-rectangles-in-gdi.md)
- [Postupy: Vykreslení textu ve formuláři Windows](how-to-draw-text-on-a-windows-form.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Kreslení čar nebo uzavřených obrázků](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons)
