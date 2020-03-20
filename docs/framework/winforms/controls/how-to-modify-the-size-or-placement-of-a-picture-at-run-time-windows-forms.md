---
title: 'Postupy: Změna velikosti či umístění obrázku za běhu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: fea813d7b9fe585e35b729b8b64e3a5f414ef76d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141963"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)
Pokud ve formuláři <xref:System.Windows.Forms.PictureBox> používáte ovládací prvek Windows <xref:System.Windows.Forms.PictureBox.SizeMode%2A> Forms, můžete vlastnost v něm nastavit tak, aby:  
  
- Zarovnání levého horního rohu obrázku s levým horním rohem ovládacího prvku  
  
- Vystředit obrázek v ovládacím prvku  
  
- Upravte velikost ovládacího prvku tak, aby odpovídal zobrazený obrázek  
  
- Roztažení libovolného obrázku, který se zobrazí, aby se vešel do ovládacího prvku  
  
 Roztažení obrázku (zejména v bitmapovém formátu) může způsobit ztrátu kvality obrazu. Metasoubory, které jsou seznamy grafických pokynů pro kreslení obrázků za běhu, jsou vhodnější pro roztahování než bitmapy.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Nastavení vlastnosti SizeMode v době běhu  
  
1. <xref:System.Windows.Forms.PictureBox.SizeMode%2A> Nastaveno <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (výchozí), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>nebo . <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>znamená, že obraz je umístěn v levém horním rohu ovládacího prvku; pokud je obraz větší než ovládací prvek, jeho dolní a pravé okraje se oříznou. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>znamená, že obraz je vystředěn v ovládacím prvku; pokud je obraz větší než ovládací prvek, vnější okraje obrázku se oříznou. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>znamená, že velikost ovládacího prvku je přizpůsobena velikosti obrázku. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>je naopak a znamená, že velikost obrázku je upravena na velikost ovládacího prvku.  
  
     V níže uvedeném příkladu je nastavenou cestou pro umístění obrázku složka Dokumenty. To je provedeno, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář. To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> již přidaným ovládacím prvkem.  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.PictureBox>
- [Postupy: Načtení obrázku pomocí Návrháře](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [PictureBox – přehled ovládacího prvku](picturebox-control-overview-windows-forms.md)
- [Postupy: Nastavení obrázků za běhu](how-to-set-pictures-at-run-time-windows-forms.md)
- [PictureBox – ovládací prvek](picturebox-control-windows-forms.md)
