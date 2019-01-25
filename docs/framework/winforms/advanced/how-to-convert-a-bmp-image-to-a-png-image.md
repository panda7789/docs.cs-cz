---
title: 'Postupy: Převod obrázku Bpm na obrázek PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: e11e2874853fb924b2da09f9fdc986873941f141
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676442"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="7efab-102">Postupy: Převod obrázku Bpm na obrázek PNG</span><span class="sxs-lookup"><span data-stu-id="7efab-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="7efab-103">Často budete chtít převést z jedné image soubor formátu do jiného.</span><span class="sxs-lookup"><span data-stu-id="7efab-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="7efab-104">Tento převod může snadno provést zavoláním <xref:System.Drawing.Image.Save%2A> metodu <xref:System.Drawing.Image> třídy a zadáte <xref:System.Drawing.Imaging.ImageFormat> pro formát souborů požadovanou image.</span><span class="sxs-lookup"><span data-stu-id="7efab-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7efab-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7efab-105">Example</span></span>  
 <span data-ttu-id="7efab-106">Následující příklad načte obrázku Bpm na obrázek z typu a uloží obrázek ve formátu PNG.</span><span class="sxs-lookup"><span data-stu-id="7efab-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7efab-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7efab-107">Compiling the Code</span></span>  
 <span data-ttu-id="7efab-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7efab-108">This example requires:</span></span>  
  
-   <span data-ttu-id="7efab-109">Aplikace modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7efab-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="7efab-110">Odkaz na `System.Drawing.Imaging` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7efab-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7efab-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7efab-111">See also</span></span>
- [<span data-ttu-id="7efab-112">Postupy: Vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="7efab-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)
- [<span data-ttu-id="7efab-113">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="7efab-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
- [<span data-ttu-id="7efab-114">Typy rastrových obrázků</span><span class="sxs-lookup"><span data-stu-id="7efab-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
