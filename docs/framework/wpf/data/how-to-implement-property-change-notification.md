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
ms.openlocfilehash: a9c0fb433e2fa65e28db3b793e038b49f9d6353b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555987"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="c0141-102">Postupy: Implementace oznámení změn vlastností</span><span class="sxs-lookup"><span data-stu-id="c0141-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="c0141-103">Pro podporu <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> vazby k povolení vlastnosti cíle vaší vazba automaticky podle dynamické změn vazby zdroje (například tak, aby měl v podokně náhledu aktualizují automaticky, když uživatel upravuje formuláře), vaše – třída musí zajistit řádné změněné vlastnosti oznámení.</span><span class="sxs-lookup"><span data-stu-id="c0141-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="c0141-104">Tento příklad ukazuje, jak vytvořit třídu, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="c0141-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0141-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0141-105">Example</span></span>  
 <span data-ttu-id="c0141-106">K implementaci <xref:System.ComponentModel.INotifyPropertyChanged> musíte deklarovat <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události a vytvořit `OnPropertyChanged` metoda.</span><span class="sxs-lookup"><span data-stu-id="c0141-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="c0141-107">Potom pro každou vlastnost chcete upozornění na změnu pro volání `OnPropertyChanged` vždy, když je vlastnost aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="c0141-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="c0141-108">Chcete-li zobrazit příklad, jak `Person` třídu lze použít pro podporu <xref:System.Windows.Data.BindingMode.TwoWay> vazby, najdete v části [řízení, když TextBox Text aktualizuje zdroj](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="c0141-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0141-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0141-109">See Also</span></span>  
 [<span data-ttu-id="c0141-110">Přehled zdrojů vazby</span><span class="sxs-lookup"><span data-stu-id="c0141-110">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="c0141-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="c0141-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="c0141-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="c0141-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
