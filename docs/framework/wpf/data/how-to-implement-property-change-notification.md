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
ms.openlocfilehash: 4f9ff49a443577e119b0c1079abbe23bd7ede4c4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459742"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="afeab-102">Postupy: Implementace oznámení změn vlastností</span><span class="sxs-lookup"><span data-stu-id="afeab-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="afeab-103">Pro podporu <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> vazby, která umožňuje vlastnostem cíle vazby automaticky odrážet dynamické změny zdroje vazby (například pokud chcete, aby se podokno náhledu automaticky aktualizovalo, když uživatel upravuje formulář), vaše třída potřebuje Zadejte správné oznámení o změněných vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="afeab-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="afeab-104">Tento příklad ukazuje, jak vytvořit třídu, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="afeab-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afeab-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="afeab-105">Example</span></span>  
 <span data-ttu-id="afeab-106">Chcete-li implementovat <xref:System.ComponentModel.INotifyPropertyChanged> je třeba deklarovat událost <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> a vytvořit metodu `OnPropertyChanged`.</span><span class="sxs-lookup"><span data-stu-id="afeab-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="afeab-107">Potom pro každou vlastnost, pro kterou chcete změnit oznámení, zavoláte `OnPropertyChanged` vždy, když je vlastnost aktualizována.</span><span class="sxs-lookup"><span data-stu-id="afeab-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="afeab-108">Chcete-li zobrazit příklad, jak lze třídu `Person` použít pro podporu vazby <xref:System.Windows.Data.BindingMode.TwoWay>, přečtěte si téma [řízení při aktualizaci textu TextBox ve zdroji](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="afeab-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afeab-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afeab-109">See also</span></span>

- [<span data-ttu-id="afeab-110">Přehled zdrojů vazby</span><span class="sxs-lookup"><span data-stu-id="afeab-110">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="afeab-111">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="afeab-111">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="afeab-112">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="afeab-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
