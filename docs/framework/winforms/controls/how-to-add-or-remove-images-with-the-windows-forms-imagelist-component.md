---
title: 'Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList'
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
ms.openlocfilehash: 430b7f573b115c21b9e2fa87f0ace74205717285
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925124"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList
Komponenta model Windows Forms <xref:System.Windows.Forms.ImageList> obvykle vyplní obrázky předtím, než je přidružena k ovládacímu prvku. Po přidružení seznamu obrázků k ovládacímu prvku však můžete přidat a odebrat obrázky.  
  
> [!NOTE]
> Při odebírání imagí ověřte, zda <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> je vlastnost všech přidružených ovládacích prvků stále platná.  
  
### <a name="to-add-images-programmatically"></a>Postup při přidávání imagí prostřednictvím kódu programu  
  
- <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> Použijte metodu <xref:System.Windows.Forms.ImageList.Images%2A> vlastnosti seznamu obrázků.  
  
     V následujícím příkladu kódu je cesta nastavená pro umístění obrázku složka **dokumenty** . Toto umístění se používá, protože můžete předpokládat, že většina počítačů, ve kterých běží operační systém Windows, bude obsahovat tuto složku. Když zvolíte toto umístění, umožníte uživatelům, kteří mají minimální úrovně přístupu k systému, bezpečněji spustit aplikaci. Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.ImageList> již přidaným ovládacím prvkem.  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>Chcete-li přidat obrázky s hodnotou klíče.  
  
- Použijte jednu z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metod <xref:System.Windows.Forms.ImageList.Images%2A> vlastnosti seznamu obrázků, která přebírá klíčovou hodnotu.  
  
     V následujícím příkladu kódu je cesta nastavená pro umístění obrázku složka **dokumenty** . Toto umístění se používá, protože můžete předpokládat, že většina počítačů, ve kterých běží operační systém Windows, bude obsahovat tuto složku. Když zvolíte toto umístění, umožníte uživatelům, kteří mají minimální úrovně přístupu k systému, bezpečněji spustit aplikaci. Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.ImageList> již přidaným ovládacím prvkem.  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>Chcete-li odebrat všechny bitové kopie programově  
  
- <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> Použití metody k odebrání jednoho obrázku  
  
     ,-nebo-  
  
     <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> Pomocí metody vymažte všechny obrázky v seznamu obrázků.  
  
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
  
### <a name="to-remove-images-by-key"></a>Postup odebrání imagí podle klíče  
  
- <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> Pomocí metody odeberte jednu Image pomocí jejího klíče.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Viz také:

- [Komponenta ImageList](imagelist-component-windows-forms.md)
- [Přehled komponenty ImageList](imagelist-component-overview-windows-forms.md)
- [Obrázky, rastrové obrázky a metasoubory](../advanced/images-bitmaps-and-metafiles.md)
