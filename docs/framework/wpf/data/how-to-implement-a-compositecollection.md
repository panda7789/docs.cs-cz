---
title: 'Postupy: Implementace CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: f8af8d806b8c889be11533392ee3c831399e9ab7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556114"
---
# <a name="how-to-implement-a-compositecollection"></a><span data-ttu-id="499e0-102">Postupy: Implementace CompositeCollection</span><span class="sxs-lookup"><span data-stu-id="499e0-102">How to: Implement a CompositeCollection</span></span>
## <a name="example"></a><span data-ttu-id="499e0-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="499e0-103">Example</span></span>  
 <span data-ttu-id="499e0-104">Následující příklad ukazuje, jak zobrazit více kolekcí a položky jako jeden seznamu pomocí <xref:System.Windows.Data.CompositeCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="499e0-104">The following example shows how to display multiple collections and items as one list using the <xref:System.Windows.Data.CompositeCollection> class.</span></span> <span data-ttu-id="499e0-105">V tomto příkladu `GreekGods` je <xref:System.Collections.ObjectModel.ObservableCollection%601> z `GreekGod` vlastní objekty.</span><span class="sxs-lookup"><span data-stu-id="499e0-105">In this example, `GreekGods` is an <xref:System.Collections.ObjectModel.ObservableCollection%601> of `GreekGod` custom objects.</span></span> <span data-ttu-id="499e0-106">Data šablony jsou definovány tak, aby `GreekGod` objekty a `GreekHero` objekty zobrazí s zlatý a barvu popředí azurové v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="499e0-106">Data templates are defined so that `GreekGod` objects and `GreekHero` objects appear with a gold and a cyan foreground color respectively.</span></span>  
  
 [!code-xaml[CompositeCollections#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="499e0-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="499e0-107">See Also</span></span>  
 <xref:System.Windows.Data.CollectionContainer>  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>  
 <xref:System.Windows.Data.XmlDataProvider>  
 <xref:System.Windows.DataTemplate>  
 [<span data-ttu-id="499e0-108">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="499e0-108">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="499e0-109">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="499e0-109">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
