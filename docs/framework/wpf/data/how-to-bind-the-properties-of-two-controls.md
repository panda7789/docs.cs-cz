---
title: 'Postupy: Svázání vlastností dvou ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 66c759c28747de5b0288c906f5d51e4253fb7d52
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459178"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="9f0eb-102">Postupy: Svázání vlastností dvou ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="9f0eb-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="9f0eb-103">Tento příklad ukazuje, jak vytvořit navázání vlastnosti jednoho ovládacího prvku s vytvořeným instancemi na jiný pomocí vlastnosti <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f0eb-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f0eb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f0eb-104">Example</span></span>  
 <span data-ttu-id="9f0eb-105">Následující příklad ukazuje, jak vytvořit navázání vlastnosti <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Canvas> na <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="9f0eb-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="9f0eb-106">vlastnost <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="9f0eb-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="9f0eb-107">Když je tento příklad vykreslený, vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="9f0eb-107">When this example is rendered it looks like the following:</span></span>  
  
![Snímek obrazovky s polem se seznamem s hodnotou zelenou vybranou a zeleným čtvercem](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="9f0eb-109">Vlastnost target vazby (v tomto příkladu vlastnost <xref:System.Windows.Controls.Panel.Background%2A>) musí být vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="9f0eb-109">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="9f0eb-110">Další informace najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9f0eb-110">For more information, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f0eb-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f0eb-111">See also</span></span>

- [<span data-ttu-id="9f0eb-112">Určení zdroje vazby</span><span class="sxs-lookup"><span data-stu-id="9f0eb-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="9f0eb-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="9f0eb-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
