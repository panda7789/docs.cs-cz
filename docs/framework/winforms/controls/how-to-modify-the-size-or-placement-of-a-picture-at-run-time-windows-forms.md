---
title: 'Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)'
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
ms.openlocfilehash: d0a86d7fe53dba3da6bd63587561f82877bc2f06
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59328332"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)
Pokud používáte Windows Forms <xref:System.Windows.Forms.PictureBox> ovládací prvek ve formuláři, můžete nastavit <xref:System.Windows.Forms.PictureBox.SizeMode%2A> vlastnost ji:  
  
-   Zarovnání obrázku levý horní roh s levého horního rohu ovládacího prvku  
  
-   System Center na obrázku v ovládacím prvku  
  
-   Upravte velikost ovládacího prvku obrázek, který se zobrazí podle  
  
-   Roztáhnout obrázek se zobrazí podle ovládacího prvku  
  
 Roztažení obrázku (zejména jedna ve formát rastrového obrázku) může způsobit ztrátu v kvality obrázku. Metasoubory, což jsou seznamy grafiky pokyny pro vykreslování obrázků za běhu, se lépe hodí pro roztažení než rastrové obrázky mají.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Chcete-li nastavit vlastnosti SizeMode za běhu  
  
1. Nastavte <xref:System.Windows.Forms.PictureBox.SizeMode%2A> k <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (výchozí), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, nebo <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> znamená, že v levém horním rohu ovládacího prvku; je umístěn na obrázku Pokud na obrázku je větší než ovládací prvek, jeho dolní a pravé hrany se oříznou. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> znamená to, že na obrázku je vycentrován ovládacího prvku; Pokud na obrázku je větší než ovládací prvek, na obrázku vnějšími hranami se oříznou. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> znamená to, že velikost ovládacího prvku je nastavena velikost obrázku. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> je naopak a znamená, že se upraví velikost obrázku velikosti ovládacího prvku.  
  
     V následujícím příkladu je cesta pro umístění bitové kopie složky Dokumenty. Je to, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tento adresář. Také to umožňuje uživatelům s úrovní přístupu minimální systém bezpečně spouštět aplikace. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek již přidán.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.PictureBox>
- [Postupy: Načtení obrázku pomocí návrháře](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [Přehled ovládacího prvku PictureBox](picturebox-control-overview-windows-forms.md)
- [Postupy: Nastavení obrázků za běhu](how-to-set-pictures-at-run-time-windows-forms.md)
- [Ovládací prvek PictureBox](picturebox-control-windows-forms.md)
