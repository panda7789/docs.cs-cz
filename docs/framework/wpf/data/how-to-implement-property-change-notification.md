---
title: 'Postupy: Implementace oznámení změn vlastností'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: d37d468acc94470be8c2afdc495b40168932ec83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204351"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="33e20-102">Postupy: Implementace oznámení změn vlastností</span><span class="sxs-lookup"><span data-stu-id="33e20-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="33e20-103">Pro podporu <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> vazby vazby vlastnosti cílové automaticky odrážejí změny dynamické vazby zdroje (například mít podokno náhledu automaticky aktualizovat, když uživatel upravuje formulář), aby vaše třída je potřeba poskytnout správné změněná vlastnost oznámení.</span><span class="sxs-lookup"><span data-stu-id="33e20-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="33e20-104">Tento příklad ukazuje, jak vytvořit třídu, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="33e20-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33e20-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="33e20-105">Example</span></span>  
 <span data-ttu-id="33e20-106">K implementaci <xref:System.ComponentModel.INotifyPropertyChanged> musíte deklarovat <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události a vytvořit `OnPropertyChanged` metoda.</span><span class="sxs-lookup"><span data-stu-id="33e20-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="33e20-107">Pak pro každou vlastnost je třeba změnit oznámení pro volání `OnPropertyChanged` vždy, když se aktualizuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="33e20-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="33e20-108">Chcete-li zobrazit příklad, jak `Person` třídy lze použít pro podporu <xref:System.Windows.Data.BindingMode.TwoWay> vazby, naleznete v tématu [řídit, kdy k aktualizaci textu TextBox zdroji](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="33e20-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e20-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33e20-109">See also</span></span>

- [<span data-ttu-id="33e20-110">Přehled zdrojů vazby</span><span class="sxs-lookup"><span data-stu-id="33e20-110">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="33e20-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="33e20-111">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="33e20-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="33e20-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
