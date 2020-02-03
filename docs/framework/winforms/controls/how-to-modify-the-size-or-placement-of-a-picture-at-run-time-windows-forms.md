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
ms.openlocfilehash: 9bb094ce0b7945f23a2e9b8614e56c9492d5f832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736033"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)
Použijete-li ovládací prvek model Windows Forms <xref:System.Windows.Forms.PictureBox> na formuláři, můžete pro něj nastavit vlastnost <xref:System.Windows.Forms.PictureBox.SizeMode%2A> na:  
  
- Zarovnat levý horní roh obrázku do levého horního rohu ovládacího prvku  
  
- Vycentrovat obrázek v ovládacím prvku  
  
- Upravte velikost ovládacího prvku tak, aby odpovídala obrázku, který se zobrazí.  
  
- Roztáhnout libovolný obrázek, který se zobrazí, aby odpovídal ovládacímu prvku  
  
 Roztažení obrázku (zejména ve formátu rastrového obrázku) může způsobit ztrátu kvality obrazu. Metasoubory, které jsou seznamy instrukcí grafiky pro vykreslování obrázků za běhu, jsou vhodnější pro roztažení než rastry.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Nastavení vlastnosti SizeMode v době běhu  
  
1. Nastavte <xref:System.Windows.Forms.PictureBox.SizeMode%2A> na <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (výchozí), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>nebo <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> znamená, že se obrázek umístí do levého horního rohu ovládacího prvku; je-li obrázek větší než ovládací prvek, jeho dolní a pravé hrany jsou oříznuty. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> znamená, že obrázek je umístěn na střed v rámci ovládacího prvku. Pokud je obrázek větší než ovládací prvek, jsou oříznuty vnější okraje obrázku. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> znamená, že velikost ovládacího prvku se upraví na velikost obrázku. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> je reverzní a to znamená, že velikost obrázku je upravena na velikost ovládacího prvku.  
  
     V následujícím příkladu je cesta nastavená pro umístění obrázku složkou Dokumenty. To se provádí, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows, bude obsahovat tento adresář. To také umožňuje uživatelům s minimálními úrovněmi přístupu k systému bezpečně spustit aplikaci. Následující příklad předpokládá, že formulář s již přidaným ovládacím prvkem <xref:System.Windows.Forms.PictureBox>.  
  
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
- [Přehled ovládacího prvku PictureBox](picturebox-control-overview-windows-forms.md)
- [Postupy: Nastavení obrázků za běhu](how-to-set-pictures-at-run-time-windows-forms.md)
- [Ovládací prvek PictureBox](picturebox-control-windows-forms.md)
