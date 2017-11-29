---
title: "Postupy: Vypsání seznamu instalovaných dekodérů"
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
- image codecs [Windows Forms], listing
- image decoders [Windows Forms], listing
ms.assetid: 11417191-8c95-40ca-8024-779e61706fb6
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17cbdebfa6cbb0cacacd923de4bd22125c812938
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-installed-decoders"></a><span data-ttu-id="73baa-102">Postupy: Vypsání seznamu instalovaných dekodérů</span><span class="sxs-lookup"><span data-stu-id="73baa-102">How to: List Installed Decoders</span></span>
<span data-ttu-id="73baa-103">Můžete k zobrazení seznamu dekodérů bitové kopie k dispozici v počítačích k určení, jestli vaše aplikace může číst konkrétní TIFF.</span><span class="sxs-lookup"><span data-stu-id="73baa-103">You may want to list the image decoders available on a computer, to determine whether your application can read a particular image file format.</span></span> <span data-ttu-id="73baa-104"><xref:System.Drawing.Imaging.ImageCodecInfo> Třída poskytuje <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> statických metod, aby mohla určit, která image dekódovací moduly jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="73baa-104">The <xref:System.Drawing.Imaging.ImageCodecInfo> class provides the <xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> static methods so that you can determine which image decoders are available.</span></span> <span data-ttu-id="73baa-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A>Vrátí pole <xref:System.Drawing.Imaging.ImageCodecInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="73baa-105"><xref:System.Drawing.Imaging.ImageCodecInfo.GetImageDecoders%2A> returns an array of <xref:System.Drawing.Imaging.ImageCodecInfo> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73baa-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="73baa-106">Example</span></span>  
 <span data-ttu-id="73baa-107">Následující příklad kódu Vypíše seznam nainstalovaných dekodérů a jejich hodnoty vlastností.</span><span class="sxs-lookup"><span data-stu-id="73baa-107">The following code example outputs the list of installed decoders and their property values.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#2)]
 [!code-vb[UsingImageEncodersDecoders#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73baa-108">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="73baa-108">Compiling the Code</span></span>  
 <span data-ttu-id="73baa-109">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="73baa-109">This example requires:</span></span>  
  
-   <span data-ttu-id="73baa-110">Aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="73baa-110">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="73baa-111">A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="73baa-111">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73baa-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="73baa-112">See Also</span></span>  
 [<span data-ttu-id="73baa-113">Postupy: vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="73baa-113">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="73baa-114">Použití kodérů a dekodérů ve spravovaném GDI +</span><span class="sxs-lookup"><span data-stu-id="73baa-114">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
