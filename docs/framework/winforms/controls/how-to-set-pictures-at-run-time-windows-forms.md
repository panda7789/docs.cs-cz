---
title: 'Postupy: Nastavení obrázků za běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: cd599ac7e07b5210f8bcff1ffbc76b3d9ee563d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182120"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Postupy: Nastavení obrázků za běhu (Windows Forms)
Můžete programově nastavit obrázek zobrazený ovládacím prvkem Windows Forms. <xref:System.Windows.Forms.PictureBox>  
  
### <a name="to-set-a-picture-programmatically"></a>Nastavení obrázku programově  
  
- Nastavte <xref:System.Windows.Forms.PictureBox.Image%2A> vlastnost pomocí <xref:System.Drawing.Image.FromFile%2A> metody <xref:System.Drawing.Image> třídy.  
  
     V níže uvedeném příkladu je nastavenou cestou pro umístění obrázku složka Dokumenty. To je provedeno, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář. To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> již přidaným ovládacím prvkem.  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a>Vymazání grafiky  
  
- Nejprve uvolněte paměť používanou obrazem a potom vymažte grafiku. Uvolnění paměti uvolní paměť později, pokud se správa paměti stane problémem.  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    > Další informace o tom, <xref:System.Drawing.Image.Dispose%2A> proč byste měli použít metodu tímto způsobem, naleznete v [tématu Vyčištění nespravovaných prostředků](../../../standard/garbage-collection/unmanaged.md).  
  
     Tento kód vymaže obraz i v případě, že grafika byla načtena do ovládacího prvku v době návrhu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [PictureBox – přehled ovládacího prvku](picturebox-control-overview-windows-forms.md)
- [Postupy: Načtení obrázku pomocí Návrháře](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Postupy: Změna velikosti či umístění obrázku za běhu](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [PictureBox – ovládací prvek](picturebox-control-windows-forms.md)
