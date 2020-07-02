---
title: 'Postupy: Implementace oznámení změn vlastností'
description: Povolit vlastnosti pro automatické upozorňování zdroje vazby při změně hodnoty vlastnosti v Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 6c298930b7b1f812e94ea6add8f53c67d3453530
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620778"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="ccc3f-103">Postupy: Implementace oznámení změn vlastností</span><span class="sxs-lookup"><span data-stu-id="ccc3f-103">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="ccc3f-104">Aby bylo možné podporovat <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> svázat vlastnosti cílové vazby, aby automaticky odrážely dynamické změny zdroje vazby (například pokud chcete, aby se podokno náhledu automaticky aktualizovalo při úpravách formuláře), vaše třída musí poskytovat správnou vlastnost změněných oznámení.</span><span class="sxs-lookup"><span data-stu-id="ccc3f-104">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="ccc3f-105">Tento příklad ukazuje, jak vytvořit třídu, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged> .</span><span class="sxs-lookup"><span data-stu-id="ccc3f-105">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccc3f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccc3f-106">Example</span></span>  
 <span data-ttu-id="ccc3f-107">K implementaci musíte <xref:System.ComponentModel.INotifyPropertyChanged> deklarovat <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> událost a vytvořit `OnPropertyChanged` metodu.</span><span class="sxs-lookup"><span data-stu-id="ccc3f-107">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="ccc3f-108">Potom můžete pro každou vlastnost, pro kterou chcete změnit oznámení, zavolat `OnPropertyChanged` vždy, když je vlastnost aktualizována.</span><span class="sxs-lookup"><span data-stu-id="ccc3f-108">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="ccc3f-109">Příklad toho `Person` , jak lze třídu použít pro podporu <xref:System.Windows.Data.BindingMode.TwoWay> vazby, naleznete v tématu [Control when text TextBox Update source](how-to-control-when-the-textbox-text-updates-the-source.md).</span><span class="sxs-lookup"><span data-stu-id="ccc3f-109">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc3f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccc3f-110">See also</span></span>

- [<span data-ttu-id="ccc3f-111">Přehled zdrojů vazby</span><span class="sxs-lookup"><span data-stu-id="ccc3f-111">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="ccc3f-112">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="ccc3f-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="ccc3f-113">– postupy</span><span class="sxs-lookup"><span data-stu-id="ccc3f-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
