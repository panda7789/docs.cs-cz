---
title: 'Postupy: Navigace prostřednictvím objektů v datech CollectionView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CollectionView [WPF], navigating through objects
- data binding [WPF], navigating through objects in data CollectionView
- navigating through objects in data CollectionView [WPF]
ms.assetid: fcd37590-bce1-4ac9-8b74-3b96c7458b8a
ms.openlocfilehash: c7de491a76ba6f8d5164c91f8c20bea4a8fa56d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688399"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="7ecc5-102">Postupy: Navigace prostřednictvím objektů v datech CollectionView</span><span class="sxs-lookup"><span data-stu-id="7ecc5-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="7ecc5-103">Zobrazení umožňují kolekci dat prohlížení různými způsoby v závislosti na řazení, filtrování nebo seskupení.</span><span class="sxs-lookup"><span data-stu-id="7ecc5-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="7ecc5-104">Zobrazení také poskytují aktuální záznam ukazatel koncept a umožňují ukazatele.</span><span class="sxs-lookup"><span data-stu-id="7ecc5-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="7ecc5-105">Tento příklad ukazuje, jak získat aktuální objekt, stejně jako navigace prostřednictvím objektů v kolekci dat pomocí funkce poskytované v <xref:System.Windows.Data.CollectionView> třídy.</span><span class="sxs-lookup"><span data-stu-id="7ecc5-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ecc5-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ecc5-106">Example</span></span>  
 <span data-ttu-id="7ecc5-107">V tomto příkladu `myCollectionView` je <xref:System.Windows.Data.CollectionView> objekt, který je zobrazení nad vázané kolekce.</span><span class="sxs-lookup"><span data-stu-id="7ecc5-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="7ecc5-108">V následujícím příkladu `OnButton` je obslužná rutina události `Previous` a `Next` tlačítka v aplikaci, která jsou tlačítka, která umožní uživateli procházení shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="7ecc5-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="7ecc5-109">Všimněte si, že <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> a <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> vlastnosti sestavy, zda ukazatel na aktuální záznam proto na začátek a konec seznamu v uvedeném pořadí tak, která <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> a <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> lze volat jako odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7ecc5-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="7ecc5-110"><xref:System.Windows.Data.CollectionView.CurrentItem%2A> Vlastnosti zobrazení je typovaná jako `Order` vrátit aktuální pořadí položek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="7ecc5-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="7ecc5-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ecc5-111">See also</span></span>
- [<span data-ttu-id="7ecc5-112">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="7ecc5-112">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [<span data-ttu-id="7ecc5-113">Řazení dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="7ecc5-113">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="7ecc5-114">Filtrování dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="7ecc5-114">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="7ecc5-115">Řazení a seskupení dat pomocí zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="7ecc5-115">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="7ecc5-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="7ecc5-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
