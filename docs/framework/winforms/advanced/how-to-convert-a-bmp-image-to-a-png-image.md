---
title: "Postupy: Převod obrázku BPM na obrázek PNG"
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
- BMP images [Windows Forms], converting to PNG
- image formats [Windows Forms], converting between
ms.assetid: 9d4a692d-73ac-4ce3-9e05-9ec321e8fbd6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 542dd132ece543b6a53a9e6d867b49fce4d15a58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-bmp-image-to-a-png-image"></a><span data-ttu-id="b729b-102">Postupy: Převod obrázku BPM na obrázek PNG</span><span class="sxs-lookup"><span data-stu-id="b729b-102">How to: Convert a BMP image to a PNG image</span></span>
<span data-ttu-id="b729b-103">Často budete chtít převést z jedné bitové kopie souboru formátu do druhého.</span><span class="sxs-lookup"><span data-stu-id="b729b-103">Oftentimes, you will want to convert from one image file format to another.</span></span> <span data-ttu-id="b729b-104">Můžete provést tento převod snadno voláním <xref:System.Drawing.Image.Save%2A> metodu <xref:System.Drawing.Image> třídy a určení <xref:System.Drawing.Imaging.ImageFormat> pro formát souboru požadovanou image.</span><span class="sxs-lookup"><span data-stu-id="b729b-104">You can do this conversion easily by calling the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class and specifying the <xref:System.Drawing.Imaging.ImageFormat> for the desired image file format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b729b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b729b-105">Example</span></span>  
 <span data-ttu-id="b729b-106">Následující příklad načte obrázku Bpm na obrázek z typu a uloží obrázek ve formátu PNG.</span><span class="sxs-lookup"><span data-stu-id="b729b-106">The following example loads a BMP image from a type, and saves the image in the PNG format.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#4)]
 [!code-vb[UsingImageEncodersDecoders#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b729b-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b729b-107">Compiling the Code</span></span>  
 <span data-ttu-id="b729b-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b729b-108">This example requires:</span></span>  
  
-   <span data-ttu-id="b729b-109">Aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b729b-109">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="b729b-110">Odkaz na `System.Drawing.Imaging` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b729b-110">A reference to the `System.Drawing.Imaging` namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b729b-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b729b-111">See Also</span></span>  
 [<span data-ttu-id="b729b-112">Postupy: vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="b729b-112">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="b729b-113">Použití kodérů a dekodérů ve spravovaném GDI +</span><span class="sxs-lookup"><span data-stu-id="b729b-113">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 [<span data-ttu-id="b729b-114">Typy rastrových obrázků</span><span class="sxs-lookup"><span data-stu-id="b729b-114">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)
