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
ms.openlocfilehash: b9afbac85dee90938e2bd55ebe19d3b02c0d66d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341488"
---
# <a name="how-to-create-thumbnail-images"></a><span data-ttu-id="fcc71-102">Postupy: Vytváření miniatur</span><span class="sxs-lookup"><span data-stu-id="fcc71-102">How to: Create Thumbnail Images</span></span>
<span data-ttu-id="fcc71-103">Obrázek miniatury je malá verze Image.</span><span class="sxs-lookup"><span data-stu-id="fcc71-103">A thumbnail image is a small version of an image.</span></span> <span data-ttu-id="fcc71-104">Obrázek miniatury můžete vytvořit pomocí volání <xref:System.Drawing.Image.GetThumbnailImage%2A> metodu <xref:System.Drawing.Image> objektu.</span><span class="sxs-lookup"><span data-stu-id="fcc71-104">You can create a thumbnail image by calling the <xref:System.Drawing.Image.GetThumbnailImage%2A> method of an <xref:System.Drawing.Image> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcc71-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="fcc71-105">Example</span></span>  
 <span data-ttu-id="fcc71-106">Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru JPG.</span><span class="sxs-lookup"><span data-stu-id="fcc71-106">The following example constructs an <xref:System.Drawing.Image> object from a JPG file.</span></span> <span data-ttu-id="fcc71-107">Původní bitové kopie je 640 pixelů šířku a výšku 479 pixelů.</span><span class="sxs-lookup"><span data-stu-id="fcc71-107">The original image has a width of 640 pixels and a height of 479 pixels.</span></span> <span data-ttu-id="fcc71-108">Kód vytvoří miniaturu, která má šířku 100 pixelů a výška 100 pixelů.</span><span class="sxs-lookup"><span data-stu-id="fcc71-108">The code creates a thumbnail image that has a width of 100 pixels and a height of 100 pixels.</span></span>  
  
 <span data-ttu-id="fcc71-109">Následující obrázek znázorňuje obrázek miniatury.</span><span class="sxs-lookup"><span data-stu-id="fcc71-109">The following illustration shows the thumbnail image.</span></span>  
  
 <span data-ttu-id="fcc71-110">![Obrázek miniatury](./media/thumbnail1.png "Thumbnail1")</span><span class="sxs-lookup"><span data-stu-id="fcc71-110">![Thumbnail Image](./media/thumbnail1.png "Thumbnail1")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcc71-111">V tomto příkladu je metoda zpětného volání deklarovány, ale nikdy použít.</span><span class="sxs-lookup"><span data-stu-id="fcc71-111">In this example, a callback method is declared, but never used.</span></span> <span data-ttu-id="fcc71-112">Tento atribut podporuje všechny verze rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="fcc71-112">This supports all versions of GDI+.</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#71](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#71)]
 [!code-vb[System.Drawing.WorkingWithImages#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#71)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fcc71-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fcc71-113">Compiling the Code</span></span>  
 <span data-ttu-id="fcc71-114">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="fcc71-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="fcc71-115">Chcete-li spustit příklad, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="fcc71-115">To run the example, follow these steps:</span></span>  
  
1. <span data-ttu-id="fcc71-116">Vytvoření nové aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fcc71-116">Create a new Windows Forms application.</span></span>  
  
2. <span data-ttu-id="fcc71-117">Přidejte ukázkový kód do formuláře.</span><span class="sxs-lookup"><span data-stu-id="fcc71-117">Add the example code to the form.</span></span>  
  
3. <span data-ttu-id="fcc71-118">Vytvořte obslužnou rutinu pro daný formulář <xref:System.Windows.Forms.Control.Paint> událostí</span><span class="sxs-lookup"><span data-stu-id="fcc71-118">Create a handler for the form's <xref:System.Windows.Forms.Control.Paint> event</span></span>  
  
4. <span data-ttu-id="fcc71-119">V <xref:System.Windows.Forms.Control.Paint> obslužné rutiny, volání `GetThumbnail` a předáte `e` pro <xref:System.Windows.Forms.PaintEventArgs>.</span><span class="sxs-lookup"><span data-stu-id="fcc71-119">In the <xref:System.Windows.Forms.Control.Paint> handler, call the `GetThumbnail` method and pass `e` for <xref:System.Windows.Forms.PaintEventArgs>.</span></span>  
  
5. <span data-ttu-id="fcc71-120">Najdete soubor obrázku, který chcete vytvořit miniatury.</span><span class="sxs-lookup"><span data-stu-id="fcc71-120">Find an image file that you want to make a thumbnail of.</span></span>  
  
6. <span data-ttu-id="fcc71-121">V `GetThumbnail` metoda, zadejte cestu a název do bitové kopie souboru.</span><span class="sxs-lookup"><span data-stu-id="fcc71-121">In the `GetThumbnail` method, specify the path and file name to your image.</span></span>  
  
7. <span data-ttu-id="fcc71-122">Stiskněte klávesu F5 ke spuštění v příkladu.</span><span class="sxs-lookup"><span data-stu-id="fcc71-122">Press F5 to run the example.</span></span>  
  
     <span data-ttu-id="fcc71-123">Ve formuláři se zobrazí obrázek miniatury 100 x 100.</span><span class="sxs-lookup"><span data-stu-id="fcc71-123">A 100 by 100 thumbnail image appears on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcc71-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcc71-124">See also</span></span>

- [<span data-ttu-id="fcc71-125">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="fcc71-125">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="fcc71-126">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="fcc71-126">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
