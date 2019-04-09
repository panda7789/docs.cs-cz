---
title: 'Postupy: Svázání prvku ListBox s daty'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 4dea53a524247d18628b3e7e7b2c06906dced53d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106431"
---
# <a name="how-to-bind-a-listbox-to-data"></a><span data-ttu-id="75b5a-102">Postupy: Svázání prvku ListBox s daty</span><span class="sxs-lookup"><span data-stu-id="75b5a-102">How to: Bind a ListBox to Data</span></span>
<span data-ttu-id="75b5a-103">Můžete vytvořit vývojář aplikace <xref:System.Windows.Controls.ListBox> ovládací prvky bez zadání obsah jednotlivých <xref:System.Windows.Controls.ListBoxItem> samostatně.</span><span class="sxs-lookup"><span data-stu-id="75b5a-103">An application developer can create <xref:System.Windows.Controls.ListBox> controls without specifying the contents of each <xref:System.Windows.Controls.ListBoxItem> separately.</span></span> <span data-ttu-id="75b5a-104">Vytváření datových vazeb můžete použít k vytvoření vazby dat na jednotlivé položky.</span><span class="sxs-lookup"><span data-stu-id="75b5a-104">You can use data binding to bind data to the individual items.</span></span>  
  
 <span data-ttu-id="75b5a-105">Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.ListBox> , který naplní <xref:System.Windows.Controls.ListBoxItem> prvky pomocí datové vazby ke zdroji dat s názvem *barvy*.</span><span class="sxs-lookup"><span data-stu-id="75b5a-105">The following example shows how to create a <xref:System.Windows.Controls.ListBox> that populates the <xref:System.Windows.Controls.ListBoxItem> elements by data binding to a data source called *Colors*.</span></span> <span data-ttu-id="75b5a-106">V tomto případě není nutné používat <xref:System.Windows.Controls.ListBoxItem> značky k určení obsahu každé položky.</span><span class="sxs-lookup"><span data-stu-id="75b5a-106">In this case it is not necessary to use <xref:System.Windows.Controls.ListBoxItem> tags to specify the content of each item.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75b5a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="75b5a-107">Example</span></span>  
 [!code-xaml[ListBoxEvent#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="75b5a-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75b5a-108">See also</span></span>

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [<span data-ttu-id="75b5a-109">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="75b5a-109">Controls</span></span>](../advanced/optimizing-performance-controls.md)
