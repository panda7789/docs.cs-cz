---
title: Přidání nebo odebrání obrázků pomocí komponenty ImageList
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
ms.openlocfilehash: e045be7ea9407bc379b0c22282fcd2184ff5db51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182304"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Postupy: Přidání a odebrání obrázků se součástí Windows Forms ImageList
Součást Windows <xref:System.Windows.Forms.ImageList> Forms je obvykle naplněna obrázky před tím, než je přidružena k ovládacímu prvku. Obrázky však můžete přidat a odebrat po přidružení seznamu obrázků k ovládacímu prvku.  
  
> [!NOTE]
> Při odebrání obrázků ověřte, zda je <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> vlastnost všech přidružených ovládacích prvků stále platná.  
  
### <a name="to-add-images-programmatically"></a>Chcete-li přidat obrázky programově  
  
- Použijte <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metodu <xref:System.Windows.Forms.ImageList.Images%2A> vlastnosti seznamu obrázků.  
  
     V následujícím příkladu kódu je nastavená cesta pro umístění obrázku složka **Dokumenty.** Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tuto složku. Výběr tohoto umístění také umožňuje uživatelům, kteří mají minimální úrovně přístupu k systému bezpečněji spustit aplikaci. Následující příklad kódu vyžaduje, abyste měli <xref:System.Windows.Forms.ImageList> formulář s již přidaným ovládacím prvkem.  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add(myImage)  
    End Sub  
    ```  
  
    ```csharp  
    public void addImage()  
    {  
    // Be sure that you use an appropriate escape sequence (such as the
    // @) when specifying the location of the file.  
       System.Drawing.Image myImage =
         Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
       imageList1.Images.Add(myImage);  
    }  
    ```  
  
    ```cpp  
    public:  
       void addImage()  
       {  
       // Replace the bold image in the following sample
       // with your own icon.  
       // Be sure that you use an appropriate escape sequence (such as
       // \\) when specifying the location of the file.  
          System::Drawing::Image ^ myImage =
             Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
          imageList1->Images->Add(myImage);  
       }  
    ```  
  
### <a name="to-add-images-with-a-key-value"></a>Přidání obrázků s klíčovou hodnotou.  
  
- Použijte jednu <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> z metod <xref:System.Windows.Forms.ImageList.Images%2A> vlastnosti seznamu obrázků, která přebírá hodnotu klíče.  
  
     V následujícím příkladu kódu je nastavená cesta pro umístění obrázku složka **Dokumenty.** Toto umístění se používá, protože můžete předpokládat, že většina počítačů s operačním systémem Windows bude obsahovat tuto složku. Výběr tohoto umístění také umožňuje uživatelům, kteří mají minimální úrovně přístupu k systému bezpečněji spustit aplikaci. Následující příklad kódu vyžaduje, abyste měli <xref:System.Windows.Forms.ImageList> formulář s již přidaným ovládacím prvkem.  
  
    ```vb  
    Public Sub LoadImage()  
       Dim myImage As System.Drawing.Image = _  
         Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
       ImageList1.Images.Add("myPhoto", myImage)  
    End Sub  
    ```  
  
```csharp  
public void addImage()  
{  
// Be sure that you use an appropriate escape sequence (such as the
// @) when specifying the location of the file.  
   System.Drawing.Image myImage =
     Image.FromFile  
   (System.Environment.GetFolderPath  
   (System.Environment.SpecialFolder.Personal)  
   + @"\Image.gif");  
   imageList1.Images.Add("myPhoto", myImage);  
}  
```  
  
### <a name="to-remove-all-images-programmatically"></a>Chcete-li odstranit všechny obrázky programově  
  
- Pomocí <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> metody můžete odstranit jeden obrázek.  
  
     ,-nebo-  
  
     Pomocí <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> této metody vymažte všechny obrázky v seznamu obrázků.  
  
    ```vb  
    ' Removes the first image in the image list  
    ImageList1.Images.Remove(myImage)  
    ' Clears all images in the image list  
    ImageList1.Images.Clear()  
    ```  
  
```csharp  
// Removes the first image in the image list.  
imageList1.Images.Remove(myImage);  
// Clears all images in the image list.  
imageList1.Images.Clear();  
```  
  
### <a name="to-remove-images-by-key"></a>Odstranění obrázků pomocí kláves  
  
- Pomocí <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> této metody odeberte jeden obrázek jeho klíčem.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Viz také

- [Komponenta ImageList](imagelist-component-windows-forms.md)
- [Přehled komponenty ImageList](imagelist-component-overview-windows-forms.md)
- [Obrázky, rastrové obrázky a metasoubory](../advanced/images-bitmaps-and-metafiles.md)
