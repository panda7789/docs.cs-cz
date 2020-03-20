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
# <a name="how-to-render-images-with-gdi"></a>Postupy: Vykreslení obrázků pomocí GDI+
Pomocí gdi+ můžete vykreslit obrázky, které existují jako soubory ve vašich aplikacích. To provést vytvořením nového <xref:System.Drawing.Image> objektu <xref:System.Drawing.Bitmap>třídy (například ) vytvořením objektu, <xref:System.Drawing.Graphics> který odkazuje <xref:System.Drawing.Graphics.DrawImage%2A> na kreslicí plochu, kterou chcete použít, a voláním metody objektu. <xref:System.Drawing.Graphics> Obraz bude namalován na kreslicí plochu reprezentovanou grafickou třídou. Editor obrázků můžete použít k vytváření a úpravám obrazových souborů v době návrhu a jejich vykreslení pomocí rozhraní GDI+ za běhu. Další informace naleznete v [editoru obrázků pro ikony](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>Vykreslení obrazu pomocí GDI+  
  
1. Vytvořte objekt představující obraz, který chcete zobrazit. Tento objekt musí být členem třídy, <xref:System.Drawing.Image>která <xref:System.Drawing.Bitmap> dědí z , například nebo <xref:System.Drawing.Imaging.Metafile>. Příklad je zobrazen:  
  
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
  
2. Vytvořte <xref:System.Drawing.Graphics> objekt, který představuje kreslicí plochu, kterou chcete použít. Další informace naleznete v [tématu How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3. Volání <xref:System.Drawing.Graphics.DrawImage%2A> grafického objektu k vykreslení obrazu. Je nutné zadat obrázek, který má být nakreslen, i souřadnice, kde má být nakreslen.  
  
    ```vb  
    g.DrawImage(myBitmap, 1, 1)  
    ```  
  
    ```csharp  
    g.DrawImage(myBitmap, 1, 1);  
    ```  
  
    ```cpp  
    g->DrawImage(myBitmap, 1, 1);  
    ```  
  
## <a name="see-also"></a>Viz také

- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Postupy: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md)
- [Pera, čáry a obdélníky v GDI+](pens-lines-and-rectangles-in-gdi.md)
- [Postupy: Kreslení textu v rozhraní Windows Forms](how-to-draw-text-on-a-windows-form.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Kreslení čar nebo uzavřených obrázků](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)
- [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons)
