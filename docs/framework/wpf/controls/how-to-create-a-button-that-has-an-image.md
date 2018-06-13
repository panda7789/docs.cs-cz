---
title: 'Postupy: Vytvoření tlačítka s obrázkem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: 9fb871aa39461329654c0289f00bd3080a633913
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550937"
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="e49bc-102">Postupy: Vytvoření tlačítka s obrázkem</span><span class="sxs-lookup"><span data-stu-id="e49bc-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="e49bc-103">Tento příklad ukazuje, jak zahrnout obrázek na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="e49bc-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e49bc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e49bc-104">Example</span></span>  
 <span data-ttu-id="e49bc-105">Následující příklad vytvoří dvě <xref:System.Windows.Controls.Button> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="e49bc-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="e49bc-106">Jeden <xref:System.Windows.Controls.Button> obsahuje text a dalších obsahuje bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="e49bc-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="e49bc-107">Obrázek je ve složce s názvem data, která je podsložkou složky projektu v příkladu.</span><span class="sxs-lookup"><span data-stu-id="e49bc-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="e49bc-108">Když uživatel klikne <xref:System.Windows.Controls.Button> obsahujícím bitovou kopii, na pozadí a text dalších <xref:System.Windows.Controls.Button> změnit.</span><span class="sxs-lookup"><span data-stu-id="e49bc-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="e49bc-109">Tento příklad vytvoří <xref:System.Windows.Controls.Button> řídí pomocí značek, ale kód používá k zápisu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="e49bc-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="e49bc-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e49bc-110">See Also</span></span>  
 [<span data-ttu-id="e49bc-111">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="e49bc-111">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="e49bc-112">Knihovna ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e49bc-112">Control Library</span></span>](../../../../docs/framework/wpf/controls/control-library.md)
