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
ms.openlocfilehash: ce13ba3413c13ced7ff9a967e23d87622309feb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-or-remove-images-with-the-windows-forms-imagelist-component"></a><span data-ttu-id="2b7a2-102">Postupy: Přidání a odebrání obrázků se součástí Windows Forms ImageList</span><span class="sxs-lookup"><span data-stu-id="2b7a2-102">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>
<span data-ttu-id="2b7a2-103">Windows Forms <xref:System.Windows.Forms.ImageList> součásti obvykle naplněný obrázky dříve, než je přidružena k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-103">The Windows Forms <xref:System.Windows.Forms.ImageList> component is typically populated with images before it is associated with a control.</span></span> <span data-ttu-id="2b7a2-104">Můžete však přidat a odebrat bitové kopie po přidružení seznamu obrázků s ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-104">However, you can add and remove images after associating the image list with a control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b7a2-105">Když odeberete bitové kopie, ověřte, zda <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> vlastnosti všech přidružených ovládacích prvků je stále platný.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-105">When you remove images, verify that the <xref:System.Windows.Forms.ButtonBase.ImageIndex%2A> property of any associated controls is still valid.</span></span>  
  
### <a name="to-add-images-programmatically"></a><span data-ttu-id="2b7a2-106">Přidání bitové kopie prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="2b7a2-106">To add images programmatically</span></span>  
  
-   <span data-ttu-id="2b7a2-107">Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metoda seznamu obrázků <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-107">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> method of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property.</span></span>  
  
     <span data-ttu-id="2b7a2-108">V následujícím příkladu kódu cesta pro umístění image je nastavena **dokumenty** složky.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-108">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="2b7a2-109">Toto umístění se používá, protože můžete předpokládat, že většina počítačů, které je spuštěn operační systém Windows bude obsahovat této složky.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-109">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="2b7a2-110">Výběr toto umístění také umožňuje uživatelům, kteří mají minimální systém úrovně přístupu další aplikaci bezpečně spustit.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-110">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="2b7a2-111">Následující příklad kódu vyžaduje, abyste měli formuláře se <xref:System.Windows.Forms.ImageList> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-111">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-add-images-with-a-key-value"></a><span data-ttu-id="2b7a2-112">Přidání bitové kopie s hodnotou klíče.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-112">To add images with a key value.</span></span>  
  
-   <span data-ttu-id="2b7a2-113">Použijte jednu z <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> metody seznamu obrázků <xref:System.Windows.Forms.ImageList.Images%2A> vlastnost, která přebírá hodnotu klíče.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-113">Use one of the <xref:System.Windows.Forms.ImageList.ImageCollection.Add%2A> methods of the image list's <xref:System.Windows.Forms.ImageList.Images%2A> property that takes a key value.</span></span>  
  
     <span data-ttu-id="2b7a2-114">V následujícím příkladu kódu cesta pro umístění image je nastavena **dokumenty** složky.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-114">In the following code example, the path set for the location of the image is the **My Documents** folder.</span></span> <span data-ttu-id="2b7a2-115">Toto umístění se používá, protože můžete předpokládat, že většina počítačů, které je spuštěn operační systém Windows bude obsahovat této složky.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-115">This location is used because you can assume that most computers that are running the Windows operating system will include this folder.</span></span> <span data-ttu-id="2b7a2-116">Výběr toto umístění také umožňuje uživatelům, kteří mají minimální systém úrovně přístupu další aplikaci bezpečně spustit.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-116">Choosing this location also lets users who have minimal system access levels more safely run the application.</span></span> <span data-ttu-id="2b7a2-117">Následující příklad kódu vyžaduje, abyste měli formuláře se <xref:System.Windows.Forms.ImageList> ovládací prvek již přidán.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-117">The following code example requires that you have a form with an <xref:System.Windows.Forms.ImageList> control already added.</span></span>  
  
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
  
### <a name="to-remove-all-images-programmatically"></a><span data-ttu-id="2b7a2-118">Chcete-li odebrat všechny Image prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="2b7a2-118">To remove all images programmatically</span></span>  
  
-   <span data-ttu-id="2b7a2-119">Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> odebrat jedné image – metoda</span><span class="sxs-lookup"><span data-stu-id="2b7a2-119">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Remove%2A> method to remove a single image</span></span>  
  
     <span data-ttu-id="2b7a2-120">, - nebo -</span><span class="sxs-lookup"><span data-stu-id="2b7a2-120">,-or-</span></span>  
  
     <span data-ttu-id="2b7a2-121">Použití <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> metoda zrušte všechny Image v seznamu obrázků.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-121">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Clear%2A> method to clear all images in the image list.</span></span>  
  
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
  
### <a name="to-remove-images-by-key"></a><span data-ttu-id="2b7a2-122">Chcete-li obrazy pomocí klíče</span><span class="sxs-lookup"><span data-stu-id="2b7a2-122">To remove images by key</span></span>  
  
-   <span data-ttu-id="2b7a2-123">Použití <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> metoda odebrat jedinou bitovou kopii pomocí jeho klíče.</span><span class="sxs-lookup"><span data-stu-id="2b7a2-123">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.RemoveByKey%2A> method to remove a single image by its key.</span></span>  
  
    ```vb  
    ' Removes the image named "myPhoto" from the list.  
    ImageList1.Images.RemoveByKey("myPhoto")  
    ```  
  
```csharp  
// Removes the image named "myPhoto" from the list.  
imageList1.Images.RemoveByKey("myPhoto");  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b7a2-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b7a2-124">See Also</span></span>  
 [<span data-ttu-id="2b7a2-125">ImageList – komponenta</span><span class="sxs-lookup"><span data-stu-id="2b7a2-125">ImageList Component</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)  
 [<span data-ttu-id="2b7a2-126">ImageList – přehled komponenty</span><span class="sxs-lookup"><span data-stu-id="2b7a2-126">ImageList Component Overview</span></span>](../../../../docs/framework/winforms/controls/imagelist-component-overview-windows-forms.md)  
 [<span data-ttu-id="2b7a2-127">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="2b7a2-127">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
