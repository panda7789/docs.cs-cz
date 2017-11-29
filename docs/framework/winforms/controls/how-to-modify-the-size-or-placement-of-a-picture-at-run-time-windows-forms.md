---
title: "Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df67871b0b133297a6f53ff9e4a42c7630a5f56d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a>Postupy: Změna velikosti či umístění obrázku za běhu (Windows Forms)
Pokud používáte Windows Forms <xref:System.Windows.Forms.PictureBox> ovládací prvek na formuláři, můžete nastavit <xref:System.Windows.Forms.PictureBox.SizeMode%2A> vlastnost na jeho:  
  
-   Zarovnat na obrázku levém horním rohu s levém horním rohu ovládacího prvku  
  
-   Center obrázků v ovládacím prvku  
  
-   Upravit velikost přizpůsobit obrázek, který se zobrazí ovládacího prvku  
  
-   Funkce Stretch jakýkoli obrázek zobrazuje podle ovládacího prvku  
  
 Roztažení obrázku (zejména jeden ve formátu rastrového obrázku) může vytvářet ztráty bitové kopie kvality. Metasoubory, které jsou seznamy grafiky pokyny pro vykreslování obrázků za běhu, se hodí pro roztažení než jsou.  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a>Chcete-li nastavit vlastnost Režim velikosti za běhu  
  
1.  Nastavit <xref:System.Windows.Forms.PictureBox.SizeMode%2A> k <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (výchozí), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, nebo <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>. <xref:System.Windows.Forms.PictureBoxSizeMode.Normal>znamená, že obrázek je umístěn v levém horním rohu ovládacího prvku; Pokud bitovou kopii je větší než ovládacího prvku, jsou oříznut jeho dolní a pravé hrany. <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>znamená, že bitovou kopii je umístěn na střed ovládacího prvku; Pokud bitovou kopii je větší než ovládacího prvku, jsou oříznut na obrázku mimo okraje. <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>znamená, že velikost ovládacího prvku je nastavena velikost bitové kopie. <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>je naopak a znamená, že se upraví velikost obrázku velikosti ovládacího prvku.  
  
     V následujícím příkladu je cesta pro umístění bitové kopie nastavit složky Dokumenty. Důvodem je, protože můžete předpokládat, že většina počítačů s operačním systémem Windows budou obsahovat tento adresář. To také umožňuje uživatelům s minimální systém úrovně přístupu pro aplikaci bezpečně spustit. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek již přidán.  
  
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
 <xref:System.Windows.Forms.PictureBox>  
 [Postupy: načtení obrázku pomocí návrháře](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [Přehled ovládacího prvku PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Postupy: nastavení obrázků za běhu](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [PictureBox – ovládací prvek](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
