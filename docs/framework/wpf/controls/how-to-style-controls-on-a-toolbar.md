---
title: 'Postupy: Ovládací prvky stylu na prvku ToolBar'
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: 580b56ebb47aa7bd50da0a966ccf60f7ea9fb2a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217780"
---
# <a name="how-to-style-controls-on-a-toolbar"></a><span data-ttu-id="1adf1-102">Postupy: Ovládací prvky stylu na prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="1adf1-102">How to: Style Controls on a ToolBar</span></span>
<span data-ttu-id="1adf1-103"><xref:System.Windows.Controls.ToolBar> Definuje <xref:System.Windows.ResourceKey> objekty k určení stylu ovládacích prvků v rámci <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="1adf1-103">The <xref:System.Windows.Controls.ToolBar> defines <xref:System.Windows.ResourceKey> objects to specify the style of controls within the <xref:System.Windows.Controls.ToolBar>.</span></span>  <span data-ttu-id="1adf1-104">K úpravě stylu ovládacího prvku v <xref:System.Windows.Controls.ToolBar>, nastavte `x:key` atribut styl, který má <xref:System.Windows.ResourceKey> definované v <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="1adf1-104">To style a control in a <xref:System.Windows.Controls.ToolBar>, set the `x:key` attribute of the style to a <xref:System.Windows.ResourceKey> defined in <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 <span data-ttu-id="1adf1-105"><xref:System.Windows.Controls.ToolBar> Definuje následující <xref:System.Windows.ResourceKey> objekty:</span><span class="sxs-lookup"><span data-stu-id="1adf1-105">The <xref:System.Windows.Controls.ToolBar> defines the following <xref:System.Windows.ResourceKey> objects:</span></span>  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a><span data-ttu-id="1adf1-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1adf1-106">Example</span></span>  
 <span data-ttu-id="1adf1-107">Následující příklad definuje styly pro ovládací prvky v rámci <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="1adf1-107">The following example defines styles for the controls within a <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a><span data-ttu-id="1adf1-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1adf1-108">See also</span></span>

- [<span data-ttu-id="1adf1-109">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="1adf1-109">Styling and Templating</span></span>](styling-and-templating.md)
