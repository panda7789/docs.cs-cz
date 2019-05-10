---
title: 'Postupy: Převod obrázku BPM na obrázek PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
ms.openlocfilehash: 59200941aa0f872a0bd99510bfaa8a8b878a9061
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648306"
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="0f393-102">Postupy: Převod obrázku BPM na obrázek PNG</span><span class="sxs-lookup"><span data-stu-id="0f393-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="0f393-103">Často budete chtít převést z jedné image soubor formátu do jiného.</span><span class="sxs-lookup"><span data-stu-id="0f393-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="0f393-104">Tento převod může snadno provést zavoláním <xref:System.Drawing.Image.Save%2A> metodu <xref:System.Drawing.Image> třídy a zadáte <xref:System.Drawing.Imaging.ImageFormat> pro formát souborů požadovanou image.</span><span class="sxs-lookup"><span data-stu-id="0f393-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f393-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f393-105">Example</span></span>  
 <span data-ttu-id="0f393-106">Následující příklad načte obrázku Bpm na obrázek z typu a uloží obrázek ve formátu PNG.</span><span class="sxs-lookup"><span data-stu-id="0f393-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f393-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0f393-107">Compiling the Code</span></span>  
 <span data-ttu-id="0f393-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="0f393-108">This example requires:</span></span>  
  
- <span data-ttu-id="0f393-109">Aplikace modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0f393-109">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="0f393-110">Odkaz na `System.Drawing.Imaging` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0f393-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f393-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f393-111">See also</span></span>

- [<span data-ttu-id="0f393-112">Postupy: Vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="0f393-112">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="0f393-113">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="0f393-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
- [<span data-ttu-id="0f393-114">Typy rastrových obrázků</span><span class="sxs-lookup"><span data-stu-id="0f393-114">Types of Bitmaps</span></span>](types-of-bitmaps.md)
