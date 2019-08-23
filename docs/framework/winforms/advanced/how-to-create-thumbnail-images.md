---
title: 'Postupy: Vytváření miniatur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thumbnail images [Windows Forms], creating
- images [Windows Forms], creating thumbnails
ms.assetid: e956242a-1e5b-4217-a3cf-5f3fb45d00ba
ms.openlocfilehash: 786a92d99f5e7a0c27f502efa9a5fe617ac4d4d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923759"
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="580c6-102">Postupy: Vytváření miniatur</span><span class="sxs-lookup"><span data-stu-id="580c6-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="580c6-103">Obrázek miniatury je malá verze obrázku.</span><span class="sxs-lookup"><span data-stu-id="580c6-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="580c6-104">Můžete vytvořit miniaturu obrázku voláním <xref:System.Drawing.Image.GetThumbnailImage%2A> metody <xref:System.Drawing.Image> objektu.</span><span class="sxs-lookup"><span data-stu-id="580c6-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="580c6-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="580c6-105">Example</span></span>  
 <span data-ttu-id="580c6-106">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru jpg.</span><span class="sxs-lookup"><span data-stu-id="580c6-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="580c6-107">Původní obrázek má šířku 640 pixelů a výšku 479 pixelů.</span><span class="sxs-lookup"><span data-stu-id="580c6-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="580c6-108">Kód Vytvoří miniaturu obrázku s šířkou 100 pixelů a výškou 100 pixelů.</span><span class="sxs-lookup"><span data-stu-id="580c6-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="580c6-109">Miniatura obrázku je znázorněna na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="580c6-109">The following illustration shows the thumbnail image:</span></span>  
  
 ![Snímek obrazovky zobrazující výstupní miniaturu](./media/how-to-create-thumbnail-images/construct-thumbnail-image.png)  
  
> [!NOTE]
> <span data-ttu-id="580c6-111">V tomto příkladu je metoda zpětného volání deklarovaná, ale nikdy se nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="580c6-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="580c6-112">Tato podpora podporuje všechny verze rozhraní GDI+.</span><span class="sxs-lookup"><span data-stu-id="580c6-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="580c6-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="580c6-113">Compiling the Code</span></span>  
 <span data-ttu-id="580c6-114">Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což <xref:System.Windows.Forms.Control.Paint> je parametr obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="580c6-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="580c6-115">Chcete-li spustit příklad, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="580c6-115">To run the example, follow these steps:</span></span>  
  
1. <span data-ttu-id="580c6-116">Vytvořte novou model Windows Forms aplikaci.</span><span class="sxs-lookup"><span data-stu-id="580c6-116">Create a new Windows Forms application.</span></span>  
  
2. <span data-ttu-id="580c6-117">Přidejte vzorový kód do formuláře.</span><span class="sxs-lookup"><span data-stu-id="580c6-117">Add the example code to the form.</span></span>  
  
3. <span data-ttu-id="580c6-118">Vytvoření obslužné rutiny pro <xref:System.Windows.Forms.Control.Paint> událost formuláře</span><span class="sxs-lookup"><span data-stu-id="580c6-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4. <span data-ttu-id="580c6-119">V obslužné rutině volejte metodu `GetThumbnail` a předejte `e` <xref:System.Windows.Forms.PaintEventArgs>ji. <xref:System.Windows.Forms.Control.Paint></span><span class="sxs-lookup"><span data-stu-id="580c6-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5. <span data-ttu-id="580c6-120">Vyhledejte soubor obrázku, který chcete vytvořit jako miniaturu.</span><span class="sxs-lookup"><span data-stu-id="580c6-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6. <span data-ttu-id="580c6-121">`GetThumbnail` V metodě zadejte cestu a název souboru k imagi.</span><span class="sxs-lookup"><span data-stu-id="580c6-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7. <span data-ttu-id="580c6-122">Stisknutím klávesy F5 spusťte příklad.</span><span class="sxs-lookup"><span data-stu-id="580c6-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="580c6-123">Ve formuláři se zobrazí obrázek miniatury 100 až 100.</span><span class="sxs-lookup"><span data-stu-id="580c6-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="580c6-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="580c6-124">See also</span></span>

- [<span data-ttu-id="580c6-125">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="580c6-125">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="580c6-126">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="580c6-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
