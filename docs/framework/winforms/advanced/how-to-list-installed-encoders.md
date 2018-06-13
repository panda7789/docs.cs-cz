---
title: 'Postupy: Vypsání seznamu instalovaných kodérů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image encoders [Windows Forms], listing
ms.assetid: 49e8e4e9-7a67-42d9-86bf-08821cdc282e
ms.openlocfilehash: 1882ce9a140fb325c29411173ba7bde717bd3f98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524752"
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="f8a94-102">Postupy: Vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="f8a94-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="f8a94-103">Můžete zobrazit seznam kodérů dostupné v počítači, chcete-li zjistit, jestli vaše aplikace můžete uložit do formátu souboru z bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="f8a94-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="f8a94-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statických metod, aby mohla určit, která image kodéry jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="f8a94-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="f8a94-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="f8a94-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8a94-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8a94-106">Example</span></span>  
 <span data-ttu-id="f8a94-107">Následující příklad kódu Vypíše seznam nainstalovaných kodéry a jejich hodnoty vlastností.</span><span class="sxs-lookup"><span data-stu-id="f8a94-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8a94-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f8a94-108">Compiling the Code</span></span>  
 <span data-ttu-id="f8a94-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f8a94-109">This example requires:</span></span>  
  
-   <span data-ttu-id="f8a94-110">Aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f8a94-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="f8a94-111">A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="f8a94-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a94-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8a94-112">See Also</span></span>  
 [<span data-ttu-id="f8a94-113">Postupy: Vypsání seznamu instalovaných dekodérů</span><span class="sxs-lookup"><span data-stu-id="f8a94-113">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 [<span data-ttu-id="f8a94-114">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="f8a94-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
