---
title: 'Postupy: Svázání vlastností dvou ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: f3355969d0f12f0f3ed9b49bdb7efa6913c5e4c4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372097"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a><span data-ttu-id="ec215-102">Postupy: Svázání vlastností dvou ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="ec215-102">How to: Bind the Properties of Two Controls</span></span>
<span data-ttu-id="ec215-103">Tento příklad ukazuje, jak vytvořit vazbu vlastnosti jedné instance ovládacího prvku, který z jiného pomocí <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ec215-103">This example shows how to bind the property of one instantiated control to that of another using the <xref:System.Windows.Data.Binding.ElementName%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec215-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ec215-104">Example</span></span>  
 <span data-ttu-id="ec215-105">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost <xref:System.Windows.Controls.Canvas> k <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span><span class="sxs-lookup"><span data-stu-id="ec215-105">The following example shows how to bind the <xref:System.Windows.Controls.Panel.Background%2A> property of a <xref:System.Windows.Controls.Canvas> to the <xref:System.Windows.Controls.Primitives.Selector.SelectedItem%2A>.<xref:System.Windows.Controls.ContentControl.Content%2A></span></span> <span data-ttu-id="ec215-106">Vlastnost <xref:System.Windows.Controls.ComboBox>:</span><span class="sxs-lookup"><span data-stu-id="ec215-106">property of a <xref:System.Windows.Controls.ComboBox>:</span></span>  
  
 [!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]  
  
 <span data-ttu-id="ec215-107">Při vykreslení v tomto příkladu bude vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="ec215-107">When this example is rendered it looks like the following:</span></span>  
  
 <span data-ttu-id="ec215-108">![Na plátně se zeleným pozadím](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span><span class="sxs-lookup"><span data-stu-id="ec215-108">![A canvas with a green background](./media/databindingbindingdpssample.PNG "DataBindingBindingDPsSample")</span></span>  
  
 <span data-ttu-id="ec215-109">**Poznámka:** cílovou vlastnost vazby (v tomto příkladu <xref:System.Windows.Controls.Panel.Background%2A> vlastnost) musí být vlastnost závislosti.</span><span class="sxs-lookup"><span data-stu-id="ec215-109">**Note** The binding target property (in this example, the <xref:System.Windows.Controls.Panel.Background%2A> property) must be a dependency property.</span></span> <span data-ttu-id="ec215-110">Další informace najdete v tématu [přehled datových vazeb](data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ec215-110">For more information, see [Data Binding Overview](data-binding-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec215-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec215-111">See also</span></span>
- [<span data-ttu-id="ec215-112">Určení zdroje vazby</span><span class="sxs-lookup"><span data-stu-id="ec215-112">Specify the Binding Source</span></span>](how-to-specify-the-binding-source.md)
- [<span data-ttu-id="ec215-113">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="ec215-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
