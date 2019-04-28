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
ms.openlocfilehash: c92b8010def2f77f859ee0bd9cdb1ed51dd15f27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723040"
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="d38c9-102">Postupy: Vypsání seznamu instalovaných dekodérů</span><span class="sxs-lookup"><span data-stu-id="d38c9-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="d38c9-103">Můžete chtít seznamu dekodérů bitové kopie k dispozici v počítači, chcete-li zjistit, jestli vaše aplikace může číst formátu souboru konkrétní image.</span><span class="sxs-lookup"><span data-stu-id="d38c9-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="d38c9-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statické metody tak, aby bylo možné určit, která image dekodérů jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d38c9-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="d38c9-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="d38c9-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d38c9-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d38c9-106">Example</span></span>  
 <span data-ttu-id="d38c9-107">Následující příklad kódu Vypíše seznam nainstalovaných dekodérů a jejich hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="d38c9-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d38c9-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d38c9-108">Compiling the Code</span></span>  
 <span data-ttu-id="d38c9-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d38c9-109">This example requires:</span></span>  
  
- <span data-ttu-id="d38c9-110">Aplikace modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d38c9-110">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="d38c9-111">A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="d38c9-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d38c9-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d38c9-112">See also</span></span>

- [<span data-ttu-id="d38c9-113">Postupy: Vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="d38c9-113">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="d38c9-114">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="d38c9-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
