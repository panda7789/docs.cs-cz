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
ms.openlocfilehash: 3d3ab62896f6b799cd38a8180b90f33125a9929b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964344"
---
# <a name="how-to-create-graphics-objects-for-drawing"></a>Postupy: Vytváření grafických objektů pro kreslení
Než budete moct nakreslit čáry a tvary, vykreslovat text nebo zobrazovat a manipulovat s nimi pomocí GDI+, je potřeba vytvořit <xref:System.Drawing.Graphics> objekt. <xref:System.Drawing.Graphics> Objekt představuje plochu vykreslování GDI+ a je objekt, který slouží k vytváření grafických obrázků.  
  
 Existují dva kroky při práci s grafikou:  
  
1. <xref:System.Drawing.Graphics> Vytvoření objektu.  
  
2. <xref:System.Drawing.Graphics> Použití objektu k nakreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrázky.  
  
## <a name="creating-a-graphics-object"></a>Vytvoření objektu grafiky  
 Objekt grafiky lze vytvořit různými způsoby.  
  
#### <a name="to-create-a-graphics-object"></a>Vytvoření objektu grafiky  
  
- Získat odkaz na objekt grafiky jako součást <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> v případě formuláře nebo ovládacího prvku. To je obvykle způsob, jak získat odkaz na objekt grafiky při vytváření kódu pro vykreslení ovládacího prvku. Podobně můžete také získat objekt grafiky jako vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> při <xref:System.Drawing.Printing.PrintDocument.PrintPage> zpracování události pro <xref:System.Drawing.Printing.PrintDocument>.  
  
     -nebo-  
  
- Voláním <xref:System.Drawing.Graphics> metody ovládacího prvku nebo formuláře získáte odkaz na objekt, který představuje kreslicí plochu daného ovládacího prvku nebo formuláře. <xref:System.Windows.Forms.Control.CreateGraphics%2A> Tuto metodu použijte, chcete-li kreslit na formulář nebo ovládací prvek, který již existuje.  
  
     -nebo-  
  
- Vytvořte objekt z libovolného objektu, který dědí z <xref:System.Drawing.Image>. <xref:System.Drawing.Graphics> Tento přístup je užitečný, když chcete změnit už existující image.  
  
     Následující části obsahují podrobné informace o každém z těchto procesů.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs v obslužné rutině události Paint  
 <xref:System.Windows.Forms.PaintEventHandler> Při programování ovládacích prvků pro ovládací prvky <xref:System.Drawing.Printing.PrintDocument.PrintPage> nebo pro <xref:System.Drawing.Printing.PrintDocument>, <xref:System.Windows.Forms.PaintEventArgs> je objekt Graphics k dispozici jako jedna z vlastností nebo <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Získání odkazu na objekt grafiky z PaintEventArgs v události Paint  
  
1. Deklarujte <xref:System.Drawing.Graphics> objekt.  
  
2. Přiřaďte proměnnou pro odkaz na <xref:System.Drawing.Graphics> objekt předaný jako součást. <xref:System.Windows.Forms.PaintEventArgs>  
  
3. Vložte kód pro vykreslení formuláře nebo ovládacího prvku.  
  
     Následující příklad ukazuje, jak odkazovat <xref:System.Drawing.Graphics> na objekt <xref:System.Windows.Forms.PaintEventArgs> z <xref:System.Windows.Forms.Control.Paint> v události:  
  
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
  
## <a name="creategraphics-method"></a>Metoda CreateGraphics  
 Můžete také použít <xref:System.Windows.Forms.Control.CreateGraphics%2A> metodu ovládacího prvku nebo formuláře k získání odkazu <xref:System.Drawing.Graphics> na objekt, který představuje kreslicí plochu daného ovládacího prvku nebo formuláře.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Vytvoření objektu grafiky pomocí metody CreateGraphics  
  
- <xref:System.Windows.Forms.Control.CreateGraphics%2A> Zavolejte metodu formuláře nebo ovládacího prvku, na který chcete vykreslit grafiku.  
  
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
  
## <a name="create-from-an-image-object"></a>Vytvořit z objektu obrázku  
 Kromě toho můžete vytvořit objekt grafiky z libovolného objektu, který je odvozen od <xref:System.Drawing.Image> třídy.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Vytvoření objektu grafiky z obrázku  
  
- Zavolejte metodu a zadejte název proměnné obrázku, ze které chcete <xref:System.Drawing.Graphics> vytvořit objekt. <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType>  
  
     Následující příklad ukazuje, jak použít <xref:System.Drawing.Bitmap> objekt:  
  
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
> Můžete vytvářet <xref:System.Drawing.Graphics> pouze objekty z neindexovaných souborů. bmp, jako jsou 16bitové, 24bitové a 32 bitové soubory. bmp. Každý pixel neindexovaných souborů. bmp obsahuje barvu na rozdíl od pixelů indexovaných souborů. bmp, které obsahují index pro tabulku barev.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Kreslení a manipulace s obrazci a obrázky  
 Po vytvoření <xref:System.Drawing.Graphics> lze objekt použít k vykreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrázky. Objekty zabezpečení, které jsou použity s <xref:System.Drawing.Graphics> objektem, jsou:  
  
- <xref:System.Drawing.Pen> Třída – používá se pro kreslení čar, sbalení tvarů nebo vykreslování dalších geometrických reprezentací.  
  
- <xref:System.Drawing.Brush> Třída – slouží k vyplňování oblastí grafiky, jako jsou například vyplněné tvary, obrázky nebo text.  
  
- <xref:System.Drawing.Font> Třída – poskytuje popis toho, co obrazce použít při vykreslování textu.  
  
- <xref:System.Drawing.Color> Struktura – představuje různé barvy, které se mají zobrazit.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Použití objektu Graphics, který jste vytvořili  
  
- Pracujte s odpovídajícím objektem uvedeným výše a nakreslete, co potřebujete.  
  
     Další informace naleznete v následujících tématech:  
  
    |Pro vykreslení|Další informace naleznete v tématu|  
    |---------------|---------|  
    |Přím|[Postupy: Nakreslit čáru na formuláři Windows](how-to-draw-a-line-on-a-windows-form.md)|  
    |Obrazce|[Postupy: Nakreslit obrazec s obrysem](how-to-draw-an-outlined-shape.md)|  
    |Text|[Postupy: Nakreslit text na formuláři Windows](how-to-draw-text-on-a-windows-form.md)|  
    |Obrázky|[Postupy: Vykreslování imagí pomocí GDI+](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Vykreslování imagí pomocí GDI+](how-to-render-images-with-gdi.md)
