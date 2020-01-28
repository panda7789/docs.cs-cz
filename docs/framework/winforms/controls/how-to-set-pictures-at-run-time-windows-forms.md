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
ms.openlocfilehash: bd0509c05fd9c1cfc0c631fcd613c64d20296f6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746747"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Postupy: Nastavení obrázků za běhu (Windows Forms)
Obrázek zobrazený pomocí ovládacího prvku model Windows Forms <xref:System.Windows.Forms.PictureBox> lze programově nastavit.  
  
### <a name="to-set-a-picture-programmatically"></a>Postup při nastavování obrázku prostřednictvím kódu programu  
  
- Nastavte vlastnost <xref:System.Windows.Forms.PictureBox.Image%2A> pomocí metody <xref:System.Drawing.Image.FromFile%2A> třídy <xref:System.Drawing.Image>.  
  
     V následujícím příkladu je cesta nastavená pro umístění obrázku složkou Dokumenty. To se provádí, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows, bude obsahovat tento adresář. To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad předpokládá, že formulář s již přidaným ovládacím prvkem <xref:System.Windows.Forms.PictureBox>.  
  
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
  
- Nejdřív uvolněte paměť, kterou image používá, a pak obrázek vymažte. Uvolňování paměti uvolní paměť později, pokud dojde k potížím se správou paměti.  
  
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
    > Další informace o tom, proč byste měli použít metodu <xref:System.Drawing.Image.Dispose%2A> tímto způsobem, najdete v tématu [Vymazání nespravovaných prostředků](../../../standard/garbage-collection/unmanaged.md).  
  
     Tento kód vymaže obrázek, i když byl obrázek načten do ovládacího prvku v době návrhu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [Přehled ovládacího prvku PictureBox](picturebox-control-overview-windows-forms.md)
- [Postupy: Načtení obrázku pomocí Návrháře](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Postupy: Změna velikosti či umístění obrázku za běhu](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [Ovládací prvek PictureBox](picturebox-control-windows-forms.md)
