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
ms.openlocfilehash: c5019a349b4f3c881190241042cecc6c4c571950
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605653"
---
# <a name="how-to-list-installed-encoders"></a><span data-ttu-id="7c7db-102">Postupy: Vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="7c7db-102">How to: List Installed Encoders</span></span>
<span data-ttu-id="7c7db-103">Můžete chtít seznamu kodérů image dostupných na počítači, k určení, jestli vaše aplikace můžete uložit do formátu souboru konkrétní image.</span><span class="sxs-lookup"><span data-stu-id="7c7db-103">You may want to list the image encoders available on a computer, to determine whether your application can save to a particular image file format.</span></span> <span data-ttu-id="7c7db-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> statické metody tak, aby bylo možné určit, která image kodérů jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="7c7db-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> static methods so that you can determine which image encoders are available.</span></span> <span data-ttu-id="7c7db-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="7c7db-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageEncoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c7db-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c7db-106">Example</span></span>  
 <span data-ttu-id="7c7db-107">Následující příklad kódu Vypíše seznam nainstalovaných kodérů a jejich hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="7c7db-107">The following code example outputs the list of installed encoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#1)]
 [!code-vb[UsingImageEncodersDecoders#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c7db-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7c7db-108">Compiling the Code</span></span>  
 <span data-ttu-id="7c7db-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7c7db-109">This example requires:</span></span>  
  
-   <span data-ttu-id="7c7db-110">Aplikace modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7c7db-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="7c7db-111">A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="7c7db-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7db-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c7db-112">See also</span></span>
- [<span data-ttu-id="7c7db-113">Postupy: Vypsání seznamu instalovaných dekodérů</span><span class="sxs-lookup"><span data-stu-id="7c7db-113">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)
- [<span data-ttu-id="7c7db-114">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="7c7db-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
