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
ms.openlocfilehash: 31ae91958dbc02a2f64945af896b4a2408224d05
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624025"
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Postupy: Přidání a odebrání obrázků pomocí komponenty Windows Forms ImageList
Windows Forms <xref:System.Windows.Forms.ImageList> komponenty se obvykle vyplní imagí dřív, než bude přidružena k ovládacímu prvku. Můžete ale přidávat a odebírat Image po přidružení seznamu obrázků s ovládacím prvkem.  
  
> [!NOTE]
>  Když odeberete Image, ověřte, že <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> vlastnosti všech přidružených ovládacích prvků je stále platný.  
  
### <a name="to-add-images-programmatically"></a>Přidání bitové kopie prostřednictvím kódu programu  
  
- Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metoda seznamu obrázků <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost.  
  
     V následujícím příkladu kódu nastavena cesta pro umístění image je **dokumenty** složky. Toto umístění se používá, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows bude obsahovat této složky. Výběrem tohoto umístění také umožňuje uživatelům, kteří mají minimální systém úrovně přístupu Další bezpečné spuštění aplikace. Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.ImageList> ovládací prvek již přidán.  
  
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
  
### <a name="to-add-images-with-a-key-value"></a>Přidání bitové kopie s hodnotou klíče.  
  
- Použijte jednu z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody ze seznamu obrázků <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost, která přebírá hodnotu klíče.  
  
     V následujícím příkladu kódu nastavena cesta pro umístění image je **dokumenty** složky. Toto umístění se používá, protože můžete předpokládat, že většina počítačů, na kterých běží operační systém Windows bude obsahovat této složky. Výběrem tohoto umístění také umožňuje uživatelům, kteří mají minimální systém úrovně přístupu Další bezpečné spuštění aplikace. Následující příklad kódu vyžaduje, abyste měli formulář s <xref:System.Windows.Forms.ImageList> ovládací prvek již přidán.  
  
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
  
### <a name="to-remove-all-images-programmatically"></a>Chcete-li odebrat všechny bitové kopie prostřednictvím kódu programu  
  
- Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> metoda odebrání jedné image  
  
     , - nebo -  
  
     Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> metoda zrušte všechny Image v seznamu obrázků.  
  
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
  
### <a name="to-remove-images-by-key"></a>Chcete-li odebrat imagí pomocí klíče  
  
- Použití <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> metoda odebrání jedné image podle jeho klíče.  
  
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
