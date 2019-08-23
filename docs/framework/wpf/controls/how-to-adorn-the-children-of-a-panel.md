---
title: 'Postupy: Doplnění podřízených položek panelu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], binding to children of Panels
- Panel control [WPF], binding adorners to children
ms.assetid: 4cc9b972-b472-4e5c-bdf3-3702d7fbb1f5
ms.openlocfilehash: 739ccaa0273e66c4650c35217a1156d64336dbbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923516"
---
# <a name="how-to-adorn-the-children-of-a-panel"></a><span data-ttu-id="b799e-102">Postupy: Doplnění podřízených položek panelu</span><span class="sxs-lookup"><span data-stu-id="b799e-102">How to: Adorn the Children of a Panel</span></span>
<span data-ttu-id="b799e-103">Tento příklad ukazuje, jak programově vytvořit vazby doplňku k podřízeným položkám určeného <xref:System.Windows.Controls.Panel>.</span><span class="sxs-lookup"><span data-stu-id="b799e-103">This example shows how to programmatically bind an adorner to the children of a specified <xref:System.Windows.Controls.Panel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b799e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b799e-104">Example</span></span>  
 <span data-ttu-id="b799e-105">Chcete-li vytvořit navázání doplňku k <xref:System.Windows.Controls.Panel>podřízeným položkám, postupujte následovně:</span><span class="sxs-lookup"><span data-stu-id="b799e-105">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>  
  
1. <span data-ttu-id="b799e-106">Deklarujte nový <xref:System.Windows.Documents.AdornerLayer> objekt a `static` <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> zavolejte metodu pro nalezení příplatku pro element, jehož podřízené prvky mají být nakryté.</span><span class="sxs-lookup"><span data-stu-id="b799e-106">Declare a new <xref:System.Windows.Documents.AdornerLayer> object and call the `static`<xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> method to find an adorner layer for the element whose children are to be adorned.</span></span>  
  
2. <span data-ttu-id="b799e-107">Zobrazte výčet prostřednictvím podřízených objektů nadřazeného prvku a zavolejte <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu pro svázání doplňku s každým podřízeným elementem.</span><span class="sxs-lookup"><span data-stu-id="b799e-107">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>  
  
 <span data-ttu-id="b799e-108">Následující příklad váže SimpleCircleAdorner (zobrazený výše) na podřízené objekty <xref:System.Windows.Controls.StackPanel> pojmenovaného *myStackPanel*.</span><span class="sxs-lookup"><span data-stu-id="b799e-108">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*.</span></span>  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
> [!NOTE]
> <span data-ttu-id="b799e-109">Použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro svázání doplňku s jiným prvkem není aktuálně podporováno.</span><span class="sxs-lookup"><span data-stu-id="b799e-109">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b799e-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b799e-110">See also</span></span>

- [<span data-ttu-id="b799e-111">Přehled doplňků pro úpravy</span><span class="sxs-lookup"><span data-stu-id="b799e-111">Adorners Overview</span></span>](adorners-overview.md)
