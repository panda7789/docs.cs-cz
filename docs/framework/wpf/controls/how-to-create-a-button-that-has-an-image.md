---
title: "Postupy: Vytvoření tlačítka s obrázkem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa3aa5454629d53fd8864df6a4f204e22028208f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-button-that-has-an-image"></a><span data-ttu-id="13c0f-102">Postupy: Vytvoření tlačítka s obrázkem</span><span class="sxs-lookup"><span data-stu-id="13c0f-102">How to: Create a Button That Has an Image</span></span>
<span data-ttu-id="13c0f-103">Tento příklad ukazuje, jak zahrnout obrázek na <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="13c0f-103">This example shows how to include an image on a <xref:System.Windows.Controls.Button>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13c0f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="13c0f-104">Example</span></span>  
 <span data-ttu-id="13c0f-105">Následující příklad vytvoří dvě <xref:System.Windows.Controls.Button> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="13c0f-105">The following example creates two <xref:System.Windows.Controls.Button> controls.</span></span> <span data-ttu-id="13c0f-106">Jeden <xref:System.Windows.Controls.Button> obsahuje text a dalších obsahuje bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="13c0f-106">One <xref:System.Windows.Controls.Button> contains text and the other contains an image.</span></span> <span data-ttu-id="13c0f-107">Obrázek je ve složce s názvem data, která je podsložkou složky projektu v příkladu.</span><span class="sxs-lookup"><span data-stu-id="13c0f-107">The image is in a folder called data, which is a subfolder of the example’s project folder.</span></span> <span data-ttu-id="13c0f-108">Když uživatel klikne <xref:System.Windows.Controls.Button> obsahujícím bitovou kopii, na pozadí a text dalších <xref:System.Windows.Controls.Button> změnit.</span><span class="sxs-lookup"><span data-stu-id="13c0f-108">When a user clicks the <xref:System.Windows.Controls.Button> that has the image, the background and the text of the other <xref:System.Windows.Controls.Button> change.</span></span>  
  
 <span data-ttu-id="13c0f-109">Tento příklad vytvoří <xref:System.Windows.Controls.Button> řídí pomocí značek, ale kód používá k zápisu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="13c0f-109">This example creates <xref:System.Windows.Controls.Button> controls by using markup but uses code to write the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handlers.</span></span>  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="13c0f-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="13c0f-110">See Also</span></span>  
 [<span data-ttu-id="13c0f-111">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="13c0f-111">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="13c0f-112">Knihovna ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="13c0f-112">Control Library</span></span>](../../../../docs/framework/wpf/controls/control-library.md)
