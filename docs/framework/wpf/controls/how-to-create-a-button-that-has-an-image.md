---
title: 'Postupy: Vytvoření tlačítka s obrázkem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: fe9f35a6f83c5a839823d94c4d3c55e01b192fb1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352032"
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="1eb36-102">Postupy: Vytvoření tlačítka s obrázkem</span><span class="sxs-lookup"><span data-stu-id="1eb36-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="1eb36-103">Tento příklad ukazuje, jak pro zahrnutí obrázku na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="1eb36-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eb36-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1eb36-104">Example</span></span>  
 <span data-ttu-id="1eb36-105">Následující příklad vytvoří dva <xref:System.Windows.Controls.Button> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="1eb36-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="1eb36-106">Jeden <xref:System.Windows.Controls.Button> obsahuje text a druhý obsahuje bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="1eb36-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="1eb36-107">Na obrázku je do složky s názvem data, která je podsložkou složky projektu v příkladu.</span><span class="sxs-lookup"><span data-stu-id="1eb36-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="1eb36-108">Když uživatel klikne <xref:System.Windows.Controls.Button> , která má bitovou kopii, pozadí a textu druhé <xref:System.Windows.Controls.Button> změnit.</span><span class="sxs-lookup"><span data-stu-id="1eb36-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="1eb36-109">Tento příklad vytvoří <xref:System.Windows.Controls.Button> ovládací prvky s použitím značky, ale kód používá k zápisu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="1eb36-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="1eb36-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1eb36-110">See also</span></span>
- [<span data-ttu-id="1eb36-111">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="1eb36-111">Controls</span></span>](index.md)
- [<span data-ttu-id="1eb36-112">Knihovna ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="1eb36-112">Control Library</span></span>](control-library.md)
