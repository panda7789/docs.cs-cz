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
ms.openlocfilehash: 492930b7d8a47db478c8fa0f282cb5f491e144ac
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708454"
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="98517-102">Postupy: Vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="98517-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="98517-103">Můžete chtít seznamu kodérů image dostupných na počítači, k určení, jestli vaše aplikace můžete uložit do formátu souboru konkrétní image.</span><span class="sxs-lookup"><span data-stu-id="98517-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="98517-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statické metody tak, aby bylo možné určit, která image kodérů jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="98517-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="98517-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="98517-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98517-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="98517-106">Example</span></span>  
 <span data-ttu-id="98517-107">Následující příklad kódu Vypíše seznam nainstalovaných kodérů a jejich hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="98517-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="98517-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="98517-108">Compiling the Code</span></span>  
 <span data-ttu-id="98517-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="98517-109">This example requires:</span></span>  
  
-   <span data-ttu-id="98517-110">Aplikace modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="98517-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="98517-111">A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="98517-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98517-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98517-112">See also</span></span>
- [<span data-ttu-id="98517-113">Postupy: Vypsání seznamu instalovaných dekodérů</span><span class="sxs-lookup"><span data-stu-id="98517-113">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)
- [<span data-ttu-id="98517-114">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="98517-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
