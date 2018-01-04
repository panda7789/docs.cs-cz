---
title: "Postupy: Vytváření miniatur obrázků"
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
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8eeb856fabd895e171c0ad8739ae6a63b5c7065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="745d0-102">Postupy: Vytváření miniatur obrázků</span><span class="sxs-lookup"><span data-stu-id="745d0-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="745d0-103">Miniatury je malá verze bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="745d0-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="745d0-104">Miniatury můžete vytvořit voláním <xref:System.Drawing.Image.GetThumbnailImage%2A> metodu <xref:System.Drawing.Image> objektu.</span><span class="sxs-lookup"><span data-stu-id="745d0-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="745d0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="745d0-105">Example</span></span>  
 <span data-ttu-id="745d0-106">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru JPG.</span><span class="sxs-lookup"><span data-stu-id="745d0-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="745d0-107">Původní bitové kopie má 640 pixelů šířka a výška 479 pixelů.</span><span class="sxs-lookup"><span data-stu-id="745d0-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="745d0-108">Kód vytvoří miniaturu, který má 100 pixelů šířka a výška 100 pixelů.</span><span class="sxs-lookup"><span data-stu-id="745d0-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="745d0-109">Následující obrázek ukazuje na miniaturu.</span><span class="sxs-lookup"><span data-stu-id="745d0-109">The following illustration shows the thumbnail image.</span></span>  
  
 <span data-ttu-id="745d0-110">![Miniaturu](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span><span class="sxs-lookup"><span data-stu-id="745d0-110">![Thumbnail Image](../../../../docs/framework/winforms/advanced/media/thumbnail1.png "Thumbnail1")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="745d0-111">V tomto příkladu je metoda zpětného volání deklarovat, ale nikdy použity.</span><span class="sxs-lookup"><span data-stu-id="745d0-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="745d0-112">To podporuje všechny verze rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="745d0-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="745d0-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="745d0-113">Compiling the Code</span></span>  
 <span data-ttu-id="745d0-114">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="745d0-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="745d0-115">Pokud chcete spustit v příkladu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="745d0-115">To run the example, follow these steps:</span></span>  
  
1.  <span data-ttu-id="745d0-116">Vytvořte novou aplikaci Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="745d0-116">Create a new Windows Forms application.</span></span>  
  
2.  <span data-ttu-id="745d0-117">Přidejte ukázkový kód pro formulář.</span><span class="sxs-lookup"><span data-stu-id="745d0-117">Add the example code to the form.</span></span>  
  
3.  <span data-ttu-id="745d0-118">Vytvořte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Control.Paint> událostí</span><span class="sxs-lookup"><span data-stu-id="745d0-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4.  <span data-ttu-id="745d0-119">V <xref:System.Windows.Forms.Control.Paint> obslužná rutina, volání `GetThumbnail` metoda a předejte jí `e` pro <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="745d0-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5.  <span data-ttu-id="745d0-120">Najít soubor obrázku, který má být miniaturu.</span><span class="sxs-lookup"><span data-stu-id="745d0-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6.  <span data-ttu-id="745d0-121">V `GetThumbnail` metoda, zadejte cestu a název do bitové kopie souboru.</span><span class="sxs-lookup"><span data-stu-id="745d0-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7.  <span data-ttu-id="745d0-122">Stisknutím klávesy F5 spusťte v příkladu.</span><span class="sxs-lookup"><span data-stu-id="745d0-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="745d0-123">100 podle 100 miniaturu se zobrazí na formuláři.</span><span class="sxs-lookup"><span data-stu-id="745d0-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="745d0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="745d0-124">See Also</span></span>  
 [<span data-ttu-id="745d0-125">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="745d0-125">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="745d0-126">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="745d0-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
