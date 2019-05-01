---
title: 'Postupy: Určení parametrů podporovaných kodérem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encoder parameters [Windows Forms], determining supported
ms.assetid: f47ae459-e3ce-4d41-a140-2f6c6aea3f44
ms.openlocfilehash: 2626eee239d9876125340dd133c5a9b3e45c3d7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004325"
---
# <a name="how-to-determine-the-parameters-supported-by-an-encoder"></a><span data-ttu-id="e8b6f-102">Postupy: Určení parametrů podporovaných kodérem</span><span class="sxs-lookup"><span data-stu-id="e8b6f-102">How to: Determine the Parameters Supported by an Encoder</span></span>
<span data-ttu-id="e8b6f-103">Můžete upravit parametry image, například úroveň kvality a provádí kompresi, ale musíte vědět, jaké parametry jsou podporovány kodér danou image.</span><span class="sxs-lookup"><span data-stu-id="e8b6f-103">You can adjust image parameters, such as quality and compression level, but you must know which parameters are supported by a given image encoder.</span></span> <span data-ttu-id="e8b6f-104"><xref:System.Drawing.Image> Třída poskytuje <xref:System.Drawing.Image.GetEncoderParameterList%2A> metodu tak, aby bylo možné určit, které image parametry jsou podporovány pro konkrétní kodér.</span><span class="sxs-lookup"><span data-stu-id="e8b6f-104">The <xref:System.Drawing.Image> class provides the <xref:System.Drawing.Image.GetEncoderParameterList%2A> method so that you can determine which image parameters are supported for a particular encoder.</span></span> <span data-ttu-id="e8b6f-105">Zadejte kodér s identifikátorem GUID.</span><span class="sxs-lookup"><span data-stu-id="e8b6f-105">You specify the encoder with a GUID.</span></span> <span data-ttu-id="e8b6f-106"><xref:System.Drawing.Image.GetEncoderParameterList%2A> Metoda vrátí pole <xref:System.Drawing.Imaging.EncoderParameter> objekty.</span><span class="sxs-lookup"><span data-stu-id="e8b6f-106">The <xref:System.Drawing.Image.GetEncoderParameterList%2A> method returns an array of <xref:System.Drawing.Imaging.EncoderParameter> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8b6f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8b6f-107">Example</span></span>  
 <span data-ttu-id="e8b6f-108">Následující příklad kódu vypíše podporovaných parametrů pro kodér JPEG.</span><span class="sxs-lookup"><span data-stu-id="e8b6f-108">The following example code outputs the supported parameters for the JPEG encoder.</span></span> <span data-ttu-id="e8b6f-109">Pomocí seznamu kategorií parametr a přidružené identifikátory GUID <xref:System.Drawing.Imaging.Encoder> přehledu třídy k určení kategorie každého parametru.</span><span class="sxs-lookup"><span data-stu-id="e8b6f-109">Use the list of parameter categories and associated GUIDs in the <xref:System.Drawing.Imaging.Encoder> class overview to determine the category for each parameter.</span></span>  
  
 [!code-csharp[UsingImageEncodersDecoders#3](~/samples/snippets/csharp/VS_Snippets_Winforms/UsingImageEncodersDecoders/CS/Form1.cs#3)]
 [!code-vb[UsingImageEncodersDecoders#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/UsingImageEncodersDecoders/VB/Form1.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8b6f-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e8b6f-110">Compiling the Code</span></span>  
 <span data-ttu-id="e8b6f-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e8b6f-111">This example requires:</span></span>  
  
- <span data-ttu-id="e8b6f-112">Aplikace modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e8b6f-112">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="e8b6f-113">A <xref:System.Windows.Forms.PaintEventArgs>, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="e8b6f-113">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b6f-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8b6f-114">See also</span></span>

- [<span data-ttu-id="e8b6f-115">Postupy: Vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="e8b6f-115">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)
- [<span data-ttu-id="e8b6f-116">Typy rastrových obrázků</span><span class="sxs-lookup"><span data-stu-id="e8b6f-116">Types of Bitmaps</span></span>](types-of-bitmaps.md)
- [<span data-ttu-id="e8b6f-117">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="e8b6f-117">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
