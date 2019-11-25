---
title: 'Postupy: Svázání vlastností dvou ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: d38c473b8c4d3f71f1e3decd4f66be248665c57b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974806"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="59fdd-102">Postupy: Svázání vlastností dvou ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="59fdd-102">How to: Bind the Properties of Two Controls</span></span>

<span data-ttu-id="59fdd-103">Tento příklad ukazuje, jak vytvořit navázání vlastnosti jednoho ovládacího prvku s vytvořeným instancemi na jiný pomocí vlastnosti <xref:System.Windows.Data.Binding.ElementName%2A>.</span><span class="sxs-lookup"><span data-stu-id="59fdd-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="59fdd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="59fdd-104">Example</span></span>

<span data-ttu-id="59fdd-105">Následující příklad ukazuje, jak vytvořit navázání vlastnosti <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Canvas> na vlastnost [SelectedItem. Content](xref:System.Windows.Controls.ContentControl.Content%2A) <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="59fdd-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the [SelectedItem.Content](xref:System.Windows.Controls.ContentControl.Content%2A) property of a <xref:System.Windows.Controls.ComboBox>:</span></span>

[!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]

<span data-ttu-id="59fdd-106">Když je tento příklad vykreslený, vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="59fdd-106">When this example is rendered it looks like the following:</span></span>

![Snímek obrazovky s polem se seznamem s hodnotou zelenou vybranou a zeleným čtvercem](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> <span data-ttu-id="59fdd-108">Vlastnost target vazby (v tomto příkladu vlastnost <xref:System.Windows.Controls.Panel.Background%2A>) musí být vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="59fdd-108">The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="59fdd-109">Další informace najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="59fdd-109">For more information, see [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="59fdd-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59fdd-110">See also</span></span>

- [<span data-ttu-id="59fdd-111">Určení zdroje vazby</span><span class="sxs-lookup"><span data-stu-id="59fdd-111">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="59fdd-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="59fdd-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
