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
ms.openlocfilehash: 3c25ddcfb3a566055afd5e233c2a69b3b7a8c66e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Postupy: Vytváření grafických objektů pro kreslení
Předtím, než můžete kreslení čar a tvarů, vykreslení text, nebo zobrazit a pracovat s obrázky s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], je nutné vytvořit <xref:System.Drawing.Graphics> objektu. <xref:System.Drawing.Graphics> Objektu představuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení prostor a je objekt, který se používá k vytvoření grafické bitové kopie.  
  
 Při práci s grafiky existují dva kroky:  
  
1.  Vytváření <xref:System.Drawing.Graphics> objektu.  
  
2.  Pomocí <xref:System.Drawing.Graphics> objekt, který chcete kreslení čar a tvarů, vykreslení text, nebo zobrazit a pracovat s obrázky.  
  
## <a name="creating-a-graphics-object"></a>Vytvoření objektu grafiky  
 Objekt grafiky lze vytvořit v mnoha různými způsoby.  
  
#### <a name="to-create-a-graphics-object"></a>Chcete-li vytvořit objekt grafiky  
  
-   Získat odkaz na objekt grafiky jako součást <xref:System.Windows.Forms.PaintEventArgs> v <xref:System.Windows.Forms.Control.Paint> událost formuláře nebo ovládacího prvku. To je obvykle jak získat odkaz na objekt grafiky při vytváření kódu vykreslování ovládacího prvku. Podobně můžete také získat objekt grafiky jako vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> při zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí pro <xref:System.Drawing.Printing.PrintDocument>.  
  
     -nebo-  
  
-   Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda ovládacího prvku nebo formuláře získat odkaz na <xref:System.Drawing.Graphics> objekt, který reprezentuje kreslicí plochy tohoto ovládacího prvku nebo formuláře. Tuto metodu použijte, pokud chcete k vykreslení na formulář nebo ovládací prvek, který již existuje.  
  
     -nebo-  
  
-   Vytvoření <xref:System.Drawing.Graphics> objekt z libovolného objektu, který dědí z <xref:System.Drawing.Image>. Tento přístup je užitečné, pokud chcete změnit již existující bitové kopie.  
  
     Následujících oddílech najdete podrobnosti o každém z těchto procesů.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs v obslužné rutině události Malování  
 Při programování <xref:System.Windows.Forms.PaintEventHandler> pro ovládací prvky nebo <xref:System.Drawing.Printing.PrintDocument.PrintPage> pro <xref:System.Drawing.Printing.PrintDocument>, objekt grafiky je k dispozici jako jedna z vlastností <xref:System.Windows.Forms.PaintEventArgs> nebo <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Chcete-li získat odkaz na objekt grafiky z PaintEventArgs v událost Malování  
  
1.  Deklarovat <xref:System.Drawing.Graphics> objektu.  
  
2.  Přiřaďte proměnnou odkazovat na <xref:System.Drawing.Graphics> objekt předaný v rámci <xref:System.Windows.Forms.PaintEventArgs>.  
  
3.  Vložení kódu k vyplnění formuláře nebo ovládacího prvku.  
  
     Následující příklad ukazuje, jak odkazovat <xref:System.Drawing.Graphics> objektu z <xref:System.Windows.Forms.PaintEventArgs> v <xref:System.Windows.Forms.Control.Paint> událostí:  
  
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
  
## <a name="creategraphics-method"></a>CreateGraphics – metoda  
 Můžete také <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda ovládacího prvku nebo formuláře získat odkaz na <xref:System.Drawing.Graphics> objekt, který reprezentuje kreslicí plochy tohoto ovládacího prvku nebo formuláře.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Chcete-li vytvořit objekt grafiky s metodou CreateGraphics  
  
-   Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metoda formuláře nebo ovládacího prvku, na který chcete vykreslit grafiky.  
  
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
  
## <a name="create-from-an-image-object"></a>Vytvoření z bitové kopie objektu  
 Kromě toho můžete vytvořit objekt grafiky z libovolného objektu, která je odvozena z <xref:System.Drawing.Image> třídy.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Chcete-li vytvořit objekt grafiky z bitové kopie  
  
-   Volání <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metodu název proměnné bitové kopie, ze kterého chcete vytvořit <xref:System.Drawing.Graphics> objektu.  
  
     Následující příklad ukazuje, jak používat <xref:System.Drawing.Bitmap> objektu:  
  
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
>  Můžete vytvořit pouze <xref:System.Drawing.Graphics> objekty z neindexované .bmp soubory, jako jsou soubory .bmp 16bitové, 24bitový a 32bitové verze. Každý pixel soubory .bmp neindexované obsahuje barvu, na rozdíl od pixelů indexované .bmp souborů, které podržte index k tabulce barev.  
  
-  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Kreslení a manipulace s nimi tvarů a bitové kopie  
 Po vytvoření <xref:System.Drawing.Graphics> objekt může sloužit k kreslení čar a tvarů, vykreslení text, nebo zobrazit a pracovat s obrázky. Hlavní objekty, které se používají s <xref:System.Drawing.Graphics> objekt jsou:  
  
-   <xref:System.Drawing.Pen> Třída – používat pro kreslení čar, osnovy tvarů nebo jiných geometrickou reprezentace vykreslování.  
  
-   <xref:System.Drawing.Brush> Třída – použít pro naplnění oblastí grafiky, jako je například vyplněné tvary, Image nebo text.  
  
-   <xref:System.Drawing.Font> Třída – obsahuje popis co obrazce pro použití při vykreslování textu.  
  
-   <xref:System.Drawing.Color> Struktura – představuje různé barvy k zobrazení.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Použití grafických objektu, který jste vytvořili  
  
-   Pracovat na příslušný objekt uvedené výše k vykreslení, co potřebujete.  
  
     Další informace naleznete v následujících tématech:  
  
    |K vykreslení|Další informace naleznete v tématu|  
    |---------------|---------|  
    |řádky|[Postupy: Kreslení čáry ve formuláři Windows](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)|  
    |Obrazce|[Postupy: Kreslení obrazce s obrysem](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)|  
    |Text|[Postupy: Kreslení textu ve formuláři Windows](../../../../docs/framework/winforms/advanced/how-to-draw-text-on-a-windows-form.md)|  
    |Obrázky|[Postupy: Vykreslení obrázků pomocí GDI+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Viz také  
 [Začínáme s programováním grafiky](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Čáry, křivky a obrazce](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Postupy: Vykreslení obrázků pomocí GDI+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)
