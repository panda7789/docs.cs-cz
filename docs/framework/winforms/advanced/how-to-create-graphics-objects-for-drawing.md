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
# <a name="how-to-create-graphics-objects-for-drawing"></a>Postupy: Vytváření grafických objektů pro kreslení
Než budete moci kreslit čáry a tvary, vykreslovat text nebo <xref:System.Drawing.Graphics> zobrazovat obrazy a manipulovat s nimi pomocí GDI+, musíte vytvořit objekt. Objekt <xref:System.Drawing.Graphics> představuje kreslicí plochu GDI+ a je objektem, který se používá k vytváření grafických obrazů.  
  
 Práce s grafikou je dva kroky:  
  
1. Vytvoření <xref:System.Drawing.Graphics> objektu.  
  
2. Použití <xref:System.Drawing.Graphics> objektu k kreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrázky.  
  
## <a name="creating-a-graphics-object"></a>Vytvoření grafického objektu  
 Grafický objekt lze vytvořit různými způsoby.  
  
#### <a name="to-create-a-graphics-object"></a>Vytvoření grafického objektu  
  
- Příjem odkazu na grafický objekt jako <xref:System.Windows.Forms.PaintEventArgs> součást <xref:System.Windows.Forms.Control.Paint> v případě formuláře nebo ovládacího prvku. Toje obvykle způsob, jakým získáte odkaz na grafický objekt při vytváření malačního kódu pro ovládací prvek. Podobně můžete také získat grafický objekt jako vlastnost <xref:System.Drawing.Printing.PrintPageEventArgs> při <xref:System.Drawing.Printing.PrintDocument.PrintPage> zpracování události <xref:System.Drawing.Printing.PrintDocument>pro .  
  
     -nebo-  
  
- Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody ovládacího prvku nebo formuláře získat <xref:System.Drawing.Graphics> odkaz na objekt, který představuje výkresovou plochu tohoto ovládacího prvku nebo formuláře. Tuto metodu použijte, pokud chcete nakreslit formulář nebo ovládací prvek, který již existuje.  
  
     -nebo-  
  
- Vytvořte <xref:System.Drawing.Graphics> objekt z libovolného <xref:System.Drawing.Image>objektu, který dědí z . Tento přístup je užitečný, pokud chcete změnit již existující bitovou kopii.  
  
     V následujících částech jsou uvedeny podrobnosti o každém z těchto procesů.  
  
## <a name="painteventargs-in-the-paint-event-handler"></a>PaintEventArgs v obslužné rutině události malby  
 Při programování <xref:System.Windows.Forms.PaintEventHandler> for controls <xref:System.Drawing.Printing.PrintDocument.PrintPage> nebo <xref:System.Drawing.Printing.PrintDocument>for a je grafický objekt k <xref:System.Windows.Forms.PaintEventArgs> dispozici <xref:System.Drawing.Printing.PrintPageEventArgs>jako jedna z vlastností nebo .  
  
#### <a name="to-obtain-a-reference-to-a-graphics-object-from-the-painteventargs-in-the-paint-event"></a>Chcete-li získat odkaz na Graphics objekt u PaintEventArgs v paint události  
  
1. Deklarujte <xref:System.Drawing.Graphics> objekt.  
  
2. Přiřaďte proměnnou <xref:System.Drawing.Graphics> odkazna objekt <xref:System.Windows.Forms.PaintEventArgs>předaný jako součást .  
  
3. Vložením kódu namalujte formulář nebo ovládací prvek.  
  
     Následující příklad ukazuje, jak <xref:System.Drawing.Graphics> odkazovat <xref:System.Windows.Forms.PaintEventArgs> na <xref:System.Windows.Forms.Control.Paint> objekt z v události:  
  
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
 Metodu <xref:System.Windows.Forms.Control.CreateGraphics%2A> ovládacího prvku nebo formuláře můžete také použít <xref:System.Drawing.Graphics> k získání odkazu na objekt, který představuje výkresovou plochu tohoto ovládacího prvku nebo formuláře.  
  
#### <a name="to-create-a-graphics-object-with-the-creategraphics-method"></a>Vytvoření objektu Graphics pomocí metody CreateGraphics  
  
- Volání <xref:System.Windows.Forms.Control.CreateGraphics%2A> metody formuláře nebo ovládacího prvku, na kterém chcete vykreslit grafiku.  
  
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
  
## <a name="create-from-an-image-object"></a>Vytvořit z objektu obrazu  
 Kromě toho můžete vytvořit grafický objekt z libovolného <xref:System.Drawing.Image> objektu, který je odvozen z třídy.  
  
#### <a name="to-create-a-graphics-object-from-an-image"></a>Vytvoření objektu Graphics z obrazu  
  
- Volání <xref:System.Drawing.Graphics.FromImage%2A?displayProperty=nameWithType> metody, zadání názvu Image proměnné, ze kterého chcete <xref:System.Drawing.Graphics> vytvořit objekt.  
  
     Následující příklad ukazuje, jak <xref:System.Drawing.Bitmap> používat objekt:  
  
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
> Můžete vytvářet <xref:System.Drawing.Graphics> pouze objekty z neindexovaných souborů BMP, například 16bitových, 24bitových a 32bitových souborů BMP. Každý pixel neindexovaných souborů BMP obsahuje barvu, na rozdíl od obrazových bodů indexovaných souborů BMP, které drží index tabulky barev.  
  
## <a name="drawing-and-manipulating-shapes-and-images"></a>Kreslení a manipulace s obrazci a obrazy  
 Po vytvoření může <xref:System.Drawing.Graphics> být objekt použit k kreslení čar a tvarů, vykreslení textu nebo zobrazení a manipulaci s obrazy. Hlavní objekty, které <xref:System.Drawing.Graphics> se používají s objektem jsou:  
  
- Třída <xref:System.Drawing.Pen> – Používá se pro kreslení čar, osnovy tvarů nebo vykreslování jiných geometrických reprezentací.  
  
- Třída <xref:System.Drawing.Brush> – Používá se k vyplnění oblastí grafiky, jako jsou vyplněné tvary, obrázky nebo text.  
  
- Třída <xref:System.Drawing.Font> – Obsahuje popis obrazců, které mají být používány při vykreslování textu.  
  
- Struktura <xref:System.Drawing.Color> – Představuje různé barvy, které se mají zobrazit.  
  
#### <a name="to-use-the-graphics-object-you-have-created"></a>Použití vytvořeného objektu Graphics  
  
- Spolupracujte s příslušným objektem uvedeným výše a nakreslete, co potřebujete.  
  
     Další informace najdete v následujících tématech:  
  
    |Chcete-li vykreslit|Seznamte se s |  
    |---------------|---------|  
    |Spojnice|[Postupy: Kreslení čáry ve formuláři Windows](how-to-draw-a-line-on-a-windows-form.md)|  
    |Obrazce|[Postupy: Kreslení obrazce s obrysem](how-to-draw-an-outlined-shape.md)|  
    |Text|[Postupy: Kreslení textu v rozhraní Windows Forms](how-to-draw-text-on-a-windows-form.md)|  
    |Image|[Postupy: Vykreslení obrázků pomocí GDI+](how-to-render-images-with-gdi.md)|  
  
## <a name="see-also"></a>Viz také

- [Začínáme s programováním grafiky](getting-started-with-graphics-programming.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Čáry, křivky a obrazce](lines-curves-and-shapes.md)
- [Postupy: Vykreslení obrázků pomocí GDI+](how-to-render-images-with-gdi.md)
