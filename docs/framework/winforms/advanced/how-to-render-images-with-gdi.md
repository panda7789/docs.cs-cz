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
ms.openlocfilehash: 6f5b139c6831a065c85e9d9889c259c859a649cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-render-images-with-gdi"></a>Postupy: Vykreslení obrázků pomocí GDI+
Můžete použít [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] vykreslování obrázků, které existují jako soubory ve svých aplikacích. To uděláte tak, že vytvoříte nový objekt <xref:System.Drawing.Image> – třída (například <xref:System.Drawing.Bitmap>), vytváření <xref:System.Drawing.Graphics> objektu, který odkazuje na kreslicí plochy, kterou chcete použít a volání <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu. Obrázek se vykresluje do kreslicí plochy reprezentována graphics – třída. Můžete použít Editor obrázků můžete vytvářet a upravovat soubory obrázků v době návrhu a vykreslit pomocí [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] za běhu. Další informace najdete v tématu [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons).  
  
### <a name="to-render-an-image-with-gdi"></a>K vykreslení bitovou kopii pomocí GDI +  
  
1.  Vytvořte objekt reprezentující bitovou kopii, kterou chcete zobrazit. Tento objekt musí být členem skupiny třídu, která dědí z <xref:System.Drawing.Image>, jako například <xref:System.Drawing.Bitmap> nebo <xref:System.Drawing.Imaging.Metafile>. Je uveden příklad:  
  
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
  
2.  Vytvoření <xref:System.Drawing.Graphics> objekt, který reprezentuje kreslicí plochy, kterou chcete použít. Další informace najdete v tématu [postupy: vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).  
  
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
  
3.  Volání <xref:System.Drawing.Graphics.DrawImage%2A> objektu grafiky k vykreslení bitovou kopii. Musíte zadat bitovou kopii, které se mají vykreslovat i souřadnice, kde má být vykreslen.  
  
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
 [Začínáme s programováním grafiky](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Postupy: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Pera, čáry a obdélníky v GDI+](../../../../docs/framework/winforms/advanced/pens-lines-and-rectangles-in-gdi.md)  
 [Postupy: Kreslení textu ve formuláři Windows](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Kreslení čar nebo uzavřených obrázků](/cpp/windows/drawing-lines-or-closed-figures-image-editor-for-icons)  
 [Editor obrázků pro ikony](/cpp/windows/image-editor-for-icons)
