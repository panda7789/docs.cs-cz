---
title: 'Postupy: Vypsání seznamu instalovaných dekodérů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
ms.openlocfilehash: c40bb79dde4a9baf8b84f3cda5fdabc6e30ad0b5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717528"
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="94669-102">Postupy: Vypsání seznamu instalovaných dekodérů</span><span class="sxs-lookup"><span data-stu-id="94669-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="94669-103">Můžete chtít seznamu dekodérů bitové kopie k dispozici v počítači, chcete-li zjistit, jestli vaše aplikace může číst formátu souboru konkrétní image.</span><span class="sxs-lookup"><span data-stu-id="94669-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="94669-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statické metody tak, aby bylo možné určit, která image dekodérů jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="94669-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="94669-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="94669-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94669-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="94669-106">Example</span></span>  
 <span data-ttu-id="94669-107">Následující příklad kódu Vypíše seznam nainstalovaných dekodérů a jejich hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="94669-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94669-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="94669-108">Compiling the Code</span></span>  
 <span data-ttu-id="94669-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="94669-109">This example requires:</span></span>  
  
-   <span data-ttu-id="94669-110">Aplikace modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="94669-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="94669-111">A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="94669-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94669-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94669-112">See also</span></span>
- [<span data-ttu-id="94669-113">Postupy: Vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="94669-113">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="94669-114">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="94669-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
