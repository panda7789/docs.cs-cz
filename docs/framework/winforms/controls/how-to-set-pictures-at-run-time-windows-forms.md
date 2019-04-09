---
title: 'Postupy: Nastavení obrázků za běhu (Windows Forms)'
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
ms.openlocfilehash: 8ed3ba9050a9117a53b5f4f1cccd26381f55ab32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073595"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Postupy: Nastavení obrázků za běhu (Windows Forms)
Můžete programově nastavení obrázku zobrazovaného rozhraním Windows Forms <xref:System.Windows.Forms.PictureBox> ovládacího prvku.  
  
### <a name="to-set-a-picture-programmatically"></a>Chcete-li nastavit obrázek prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.PictureBox.Image%2A> pomocí vlastnosti <xref:System.Drawing.Image.FromFile%2A> metodu <xref:System.Drawing.Image> třídy.  
  
     V následujícím příkladu je cesta pro umístění bitové kopie složky Dokumenty. Je to, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář. Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek již přidán.  
  
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
  
### <a name="to-clear-a-graphic"></a>Vymazat obrázek  
  
-   Nejprve uvolnění paměti používané bitovou kopii a zrušte na obrázku. Uvolňování paměti uvolní se paměť později Pokud Správa paměti stane problém.  
  
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
    >  Další informace o důvod, proč byste měli použít <xref:System.Drawing.Image.Dispose%2A> najdete v článku metoda tímto způsobem [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).  
  
     Tento kód se vymažou bitovou kopii, i v případě, že grafický objekt byl načten do ovládacího prvku v době návrhu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [Přehled ovládacího prvku PictureBox](picturebox-control-overview-windows-forms.md)
- [Postupy: Načtení obrázku pomocí Návrháře](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Postupy: Změna velikosti či umístění obrázku za běhu](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Ovládací prvek PictureBox](picturebox-control-windows-forms.md)
