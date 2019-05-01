---
title: 'Postupy: Vytvoření vazby vlastností dvou ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: 332e8e0dfa30ff7aff27c95652f07446baf6511a
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63809535"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="52228-102">Postupy: Vytvoření vazby vlastností dvou ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="52228-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="52228-103">Tento příklad ukazuje, jak vytvořit vazbu vlastnosti jedné instance ovládacího prvku, který z jiného pomocí <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="52228-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52228-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="52228-104">Example</span></span>  
 <span data-ttu-id="52228-105">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Canvas> k <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="52228-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="52228-106">Vlastnost <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="52228-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="52228-107">Při vykreslení v tomto příkladu bude vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="52228-107">When this example is rendered it looks like the following:</span></span>  
  
![Snímek obrazovky zobrazující pole se seznamem zaškrtnutým políčkem hodnotou zelené a zelený čtvereček.](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="52228-109">Vlastnost target vazby (v tomto příkladu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost) musí být vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="52228-109">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="52228-110">Další informace najdete v tématu [přehled datových vazeb](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="52228-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52228-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52228-111">See also</span></span>

- [<span data-ttu-id="52228-112">Určení zdroje vazby</span><span class="sxs-lookup"><span data-stu-id="52228-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="52228-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="52228-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
