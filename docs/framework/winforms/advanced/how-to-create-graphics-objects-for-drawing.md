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
ms.openlocfilehash: e609fbff29d058c04a839a5dcb79aab16a518298
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709046"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Postupy: Vytváření grafických objektů pro kreslení
Předtím, než můžete kreslení čar a obrazců, vykreslení textu, nebo zobrazení a manipulaci s obrázky s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], je potřeba vytvořit <xref:System.Drawing.Graphics> objektu. <xref:System.Drawing.Graphics> Objekt představuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kreslení ploše a je objekt, který se používá k vytvoření grafické obrázky.  
  
 Při práci s grafikou existují dva kroky:  
  
1.  Vytváření <xref:System.Drawing.Graphics> objektu.  
  
2.  Použití <xref:System.Drawing.Graphics> objektů pro kreslení čar a obrazců, vykreslení textu, nebo zobrazení a manipulaci s obrázky.  
  
## <a name="creating-a-graphics-object"></a>Vytvoření objektu grafiky  
 Grafický objekt můžete vytvořit mnoha různými způsoby.  
  
#### <a name="to-create-a-graphics-object"></a>Chcete-li vytvořit objekt grafiky  
  
-   Jako součást, zobrazí se odkaz na objekt grafiky <xref:System.Windows.Forms.PaintEventArgs> v <xref:System.Windows.Forms.Control.Paint> události formuláře nebo ovládacího prvku. To je obvykle získání odkazu na objekt grafiky při vytváření Malování kódu pro ovládací prvek. Podobně můžete získat také grafický objekt jako vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> při zpracování <xref:System.Drawing.Printing.PrintDocument.PrintPage> událostí pro <xref:System.Drawing.Printing.PrintDocument>.  
  
     -nebo-  
  
-   Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> ovládacího prvku nebo formuláře k získání odkazu na metodu <xref:System.Drawing.Graphics> objekt, který reprezentuje na návrhovém povrchu tohoto ovládacího prvku nebo formuláře. Tuto metodu použijte, pokud chcete vykreslovat na formulář nebo ovládací prvek, který již existuje.  
  
     -nebo-  
  
-   Vytvoření <xref:System.Drawing.Graphics> objekt z libovolného objektu, která dědí z <xref:System.Drawing.Image>. Tento přístup je užitečný, pokud chcete změnit již existující image.  
  
     Následující části obsahují podrobné informace o každé z těchto procesů.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs v obslužné rutině události Malování  
 Při programování <xref:System.Windows.Forms.PaintEventHandler> pro ovládací prvky nebo <xref:System.Drawing.Printing.PrintDocument.PrintPage> pro <xref:System.Drawing.Printing.PrintDocument>, grafický objekt je k dispozici jako jedna z vlastností objektu <xref:System.Windows.Forms.PaintEventArgs> nebo <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>K získání odkazu na objekt grafiky z PaintEventArgs v událost malby  
  
1.  Deklarovat <xref:System.Drawing.Graphics> objektu.  
  
2.  Přiřazení proměnné odkazovat <xref:System.Drawing.Graphics> objekt předán jako součást <xref:System.Windows.Forms.PaintEventArgs>.  
  
3.  Vložte kód pro vykreslení formulář nebo ovládací prvek.  
  
     Následující příklad ukazuje způsob vytvoření odkazu <xref:System.Drawing.Graphics> objektu z <xref:System.Windows.Forms.PaintEventArgs> v <xref:System.Windows.Forms.Control.Paint> události:  
  
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
  
## <a name="creategraphics-method"></a>Metodu CreateGraphics  
 Můžete také použít <xref:System.Windows.Forms.Control.CreateGraphics%2A> ovládacího prvku nebo formuláře k získání odkazu na metodu <xref:System.Drawing.Graphics> objekt, který reprezentuje na návrhovém povrchu tohoto ovládacího prvku nebo formuláře.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Chcete-li vytvořit grafický objekt s metodu CreateGraphics  
  
-   Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formuláře nebo ovládacího prvku, na který chcete vykreslit grafiky.  
  
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
  
## <a name="create-from-an-image-object"></a>Vytvořit z Image objektu  
 Kromě toho můžete vytvořit grafický objekt z libovolného objektu, která je odvozena od <xref:System.Drawing.Image> třídy.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Chcete-li vytvořit objekt grafiky z bitové kopie  
  
-   Volání <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metodu název proměnné Image, ze kterého chcete vytvořit <xref:System.Drawing.Graphics> objektu.  
  
     Následující příklad ukazuje způsob použití <xref:System.Drawing.Bitmap> objektu:  
  
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
>  Můžete vytvořit pouze <xref:System.Drawing.Graphics> objekty ze souborů neindexované .bmp, jako jsou například soubory .bmp 16-bit, 24 bitů a 32-bit. Každý pixel neindexované BMP obsahuje barvu, na rozdíl od indexované .bmp soubory, které uložení indexu tabulky barev v pixelech.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Kreslení a manipulace s nimi obrazce a obrázky  
 Po jeho vytvoření, <xref:System.Drawing.Graphics> objekt slouží k vykreslení čar a obrazců, vykreslení textu, nebo zobrazení a manipulaci s imagí. Instanční objekty, které se používají s <xref:System.Drawing.Graphics> objektu jsou:  
  
-   <xref:System.Drawing.Pen> Třídy – používat pro kreslení čar, osnovy obrazce nebo jiné geometrické reprezentace vykreslování.  
  
-   <xref:System.Drawing.Brush> Třídy – používané pro vyplnění oblasti grafiky, jako je například vyplněné obrazce, Image nebo text.  
  
-   <xref:System.Drawing.Font> Třídy – popisuje, co budou použity při generování text obrazce.  
  
-   <xref:System.Drawing.Color> Struktura – představuje různé barvy pro zobrazení.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Použití objektu grafiky, které jste vytvořili  
  
-   Práce s odpovídající objekt uvedené výše, chcete-li nakreslit, co potřebujete.  
  
     Další informace naleznete v následujících tématech:  
  
    |K vykreslení|Další informace naleznete v tématu|  
    |---------------|---------|  
    |řádky|[Postupy: Nakreslit čáru na formuláři Windows](how-to-draw-a-line-on-a-windows-form.md)|  
    |Obrazce|[Postupy: Kreslení obrazce s obrysem](how-to-draw-an-outlined-shape.md)|  
    |Text|[Postupy: Vykreslení textu ve formuláři Windows](how-to-draw-text-on-a-windows-form.md)|  
    |Obrázky|[Postupy: Vykreslení obrázků pomocí GDI +](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Viz také:
- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Vykreslení obrázků pomocí GDI +](how-to-render-images-with-gdi.md)
