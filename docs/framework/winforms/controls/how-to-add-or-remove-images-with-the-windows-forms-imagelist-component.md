---
title: "Postupy: Přidání a odebrání obrázků se součástí Windows Forms ImageList"
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
- images [Windows Forms], removing from ImageList component
- images [Windows Forms], storing for controls
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
- images [Windows Forms], displaying with controls
ms.assetid: c5eacc56-f769-4e2e-bfb7-f756620913db
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4e09448cb834453a4c8fce4494ab9fbb53eb0dc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a>Postupy: Přidání a odebrání obrázků se součástí Windows Forms ImageList
Windows Forms <xref:System.Windows.Forms.ImageList> součásti obvykle naplněný obrázky dříve, než je přidružena k ovládacímu prvku. Můžete však přidat a odebrat bitové kopie po přidružení seznamu obrázků s ovládacím prvkem.  
  
> [!NOTE]
>  Když odeberete bitové kopie, ověřte, zda <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> vlastnosti všech přidružených ovládacích prvků je stále platný.  
  
### <a name="to-add-images-programmatically"></a>Přidání bitové kopie prostřednictvím kódu programu  
  
-   Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metoda seznamu obrázků <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost.  
  
     V následujícím příkladu kódu cesta pro umístění image je nastavena **dokumenty** složky. Toto umístění se používá, protože můžete předpokládat, že většina počítačů, které je spuštěn operační systém Windows bude obsahovat této složky. Výběr toto umístění také umožňuje uživatelům, kteří mají minimální systém úrovně přístupu další aplikaci bezpečně spustit. Následující příklad kódu vyžaduje, abyste měli formuláře se <xref:System.Windows.Forms.ImageList> ovládací prvek již přidán.  
  
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
  
-   Použijte jednu z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody seznamu obrázků <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost, která přebírá hodnotu klíče.  
  
     V následujícím příkladu kódu cesta pro umístění image je nastavena **dokumenty** složky. Toto umístění se používá, protože můžete předpokládat, že většina počítačů, které je spuštěn operační systém Windows bude obsahovat této složky. Výběr toto umístění také umožňuje uživatelům, kteří mají minimální systém úrovně přístupu další aplikaci bezpečně spustit. Následující příklad kódu vyžaduje, abyste měli formuláře se <xref:System.Windows.Forms.ImageList> ovládací prvek již přidán.  
  
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
  
1.  
  
### <a name="to-remove-all-images-programmatically"></a>Chcete-li odebrat všechny Image prostřednictvím kódu programu  
  
-   Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> odebrat jedné image – metoda  
  
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
  
### <a name="to-remove-images-by-key"></a>Chcete-li obrazy pomocí klíče  
  
-   Použití <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> metoda odebrat jedinou bitovou kopii pomocí jeho klíče.  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a>Viz také  
 [Komponenta ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 [Přehled komponenty ImageList](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
