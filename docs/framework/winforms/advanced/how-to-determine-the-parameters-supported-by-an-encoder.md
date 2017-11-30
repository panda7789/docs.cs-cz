---
title: "Postupy: Určení parametrů podporovaných kodérem"
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
helpviewer_keywords: encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e041434e9ace24618dbdc45341a0e8468721c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a><span data-ttu-id="62921-102">Postupy: Určení parametrů podporovaných kodérem</span><span class="sxs-lookup"><span data-stu-id="62921-102">How to: Determine the Parameters Supported by an Encoder</span></span>
<span data-ttu-id="62921-103">Můžete upravit parametry bitové kopie, například úrovně kvality a komprese, ale musíte vědět, jaké parametry jsou podporovány kodér danou bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="62921-103">You can adjust image parameters, such as quality and compression level, but you must know which parameters are supported by a given image encoder.</span></span> <span data-ttu-id="62921-104"><xref:System.Drawing.Image> Třída poskytuje <xref:System.Drawing.Image.GetEncoderParameterList%2A> metoda, aby mohla určit, které parametry bitové kopie jsou podporovány pro konkrétní kodér.</span><span class="sxs-lookup"><span data-stu-id="62921-104">The <xref:System.Drawing.Image> class provides the <xref:System.Drawing.Image.GetEncoderParameterList%2A> method so that you can determine which image parameters are supported for a particular encoder.</span></span> <span data-ttu-id="62921-105">Kodér zadáte s identifikátorem GUID.</span><span class="sxs-lookup"><span data-stu-id="62921-105">You specify the encoder with a GUID.</span></span> <span data-ttu-id="62921-106"><xref:System.Drawing.Image.GetEncoderParameterList%2A> Metoda vrátí pole <xref:System.Drawing.Imaging.EncoderParameter> objekty.</span><span class="sxs-lookup"><span data-stu-id="62921-106">The <xref:System.Drawing.Image.GetEncoderParameterList%2A> method returns an array of <xref:System.Drawing.Imaging.EncoderParameter> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62921-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="62921-107">Example</span></span>  
 <span data-ttu-id="62921-108">Následující příklad kódu výstupy podporované parametry pro kodér JPEG.</span><span class="sxs-lookup"><span data-stu-id="62921-108">The following example code outputs the supported parameters for the JPEG encoder.</span></span> <span data-ttu-id="62921-109">Použijte seznam kategorií parametr a přidružené identifikátory GUID v <xref:System.Drawing.Imaging.Encoder> přehledu třídy k určení kategorie pro jednotlivé parametry.</span><span class="sxs-lookup"><span data-stu-id="62921-109">Use the list of parameter categories and associated GUIDs in the <xref:System.Drawing.Imaging.Encoder> class overview to determine the category for each parameter.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62921-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="62921-110">Compiling the Code</span></span>  
 <span data-ttu-id="62921-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="62921-111">This example requires:</span></span>  
  
-   <span data-ttu-id="62921-112">Aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="62921-112">A Windows Forms application.</span></span>  
  
-   <span data-ttu-id="62921-113">A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="62921-113">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62921-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="62921-114">See Also</span></span>  
 [<span data-ttu-id="62921-115">Postupy: vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="62921-115">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 [<span data-ttu-id="62921-116">Typy rastrových obrázků</span><span class="sxs-lookup"><span data-stu-id="62921-116">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 [<span data-ttu-id="62921-117">Použití kodérů a dekodérů ve spravovaném GDI +</span><span class="sxs-lookup"><span data-stu-id="62921-117">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)
