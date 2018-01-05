---
title: "Postupy: Nastavení obrázků za běhu (Windows Forms)"
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
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fd0e990b494bc0b7a3008f211aa6ded9e04d732
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a>Postupy: Nastavení obrázků za běhu (Windows Forms)
Můžete programově nastavení obrázku zobrazovaného ve Windows Forms <xref:System.Windows.Forms.PictureBox> ovládacího prvku.  
  
### <a name="to-set-a-picture-programmatically"></a>Chcete-li nastavit obrázek prostřednictvím kódu programu  
  
-   Nastavit <xref:System.Windows.Forms.PictureBox.Image%2A> pomocí vlastnosti <xref:System.Drawing.Image.FromFile%2A> metodu <xref:System.Drawing.Image> třídy.  
  
     V následujícím příkladu je cesta pro umístění bitové kopie nastavit složky Dokumenty. Důvodem je, protože můžete předpokládat, že většina počítačů s operačním systémem Windows budou obsahovat tento adresář. To také umožňuje uživatelům s minimální systém úrovně přístupu pro aplikaci bezpečně spustit. Následující příklad předpokládá formulář s <xref:System.Windows.Forms.PictureBox> ovládací prvek již přidán.  
  
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
  
### <a name="to-clear-a-graphic"></a>Zrušte grafiky  
  
-   Nejprve uvolnění paměti používané bitovou kopii a zrušte zaškrtnutí políčka na obrázku. Uvolňování paměti se uvolní paměť později Správa paměti přestane být problém.  
  
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
    >  Další informace o důvod, proč byste měli používat <xref:System.Drawing.Image.Dispose%2A> najdete v článku metoda tímto způsobem [čištění nespravovaných prostředků](../../../../docs/standard/garbage-collection/unmanaged.md).  
  
     Tento kód vymaže bitovou kopii, i když grafiky byla načtena do ovládacího prvku v době návrhu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.PictureBox>  
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>  
 [Přehled ovládacího prvku PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [Postupy: Načtení obrázku pomocí Návrháře](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [Postupy: Změna velikosti či umístění obrázku za běhu](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [Ovládací prvek PictureBox](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
