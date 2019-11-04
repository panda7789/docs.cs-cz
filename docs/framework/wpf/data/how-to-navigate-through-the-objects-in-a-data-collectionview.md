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
ms.openlocfilehash: 5ca386db89dcaa66d364d2ed7169c67393cebead
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459704"
---
# <a name="how-to-navigate-through-the-objects-in-a-data-collectionview"></a><span data-ttu-id="6e277-102">Postupy: Navigace prostřednictvím objektů v datech CollectionView</span><span class="sxs-lookup"><span data-stu-id="6e277-102">How to: Navigate Through the Objects in a Data CollectionView</span></span>
<span data-ttu-id="6e277-103">Zobrazení umožňují, aby se stejná kolekce dat zobrazila různými způsoby v závislosti na řazení, filtrování nebo seskupování.</span><span class="sxs-lookup"><span data-stu-id="6e277-103">Views allow the same data collection to be viewed in different ways, depending on sorting, filtering, or grouping.</span></span> <span data-ttu-id="6e277-104">Zobrazení také poskytují aktuální koncept ukazatele záznamu a umožňují přesunutí ukazatele.</span><span class="sxs-lookup"><span data-stu-id="6e277-104">Views also provide a current record pointer concept and enable moving the pointer.</span></span> <span data-ttu-id="6e277-105">Tento příklad ukazuje, jak získat aktuální objekt a také procházet objekty v kolekci dat pomocí funkcí poskytovaných ve třídě <xref:System.Windows.Data.CollectionView>.</span><span class="sxs-lookup"><span data-stu-id="6e277-105">This example shows how to get the current object as well as navigate through the objects in a data collection using the functionality provided in the <xref:System.Windows.Data.CollectionView> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e277-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e277-106">Example</span></span>  
 <span data-ttu-id="6e277-107">V tomto příkladu je `myCollectionView` objekt <xref:System.Windows.Data.CollectionView>, který je zobrazením v vázané kolekci.</span><span class="sxs-lookup"><span data-stu-id="6e277-107">In this example, `myCollectionView` is a <xref:System.Windows.Data.CollectionView> object that is a view over a bound collection.</span></span>  
  
 <span data-ttu-id="6e277-108">V následujícím příkladu je `OnButton` obslužná rutina události pro tlačítka `Previous` a `Next` v aplikaci, což jsou tlačítka, která umožňují uživateli přejít na shromažďování dat.</span><span class="sxs-lookup"><span data-stu-id="6e277-108">In the following example, `OnButton` is an event handler for the `Previous` and `Next` buttons in an application, which are buttons that allow the user to navigate the data collection.</span></span> <span data-ttu-id="6e277-109">Všimněte si, že vlastnosti <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> a <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> vykazují, zda ukazatel aktuálního záznamu přichází na začátek a konec seznamu, aby bylo možné <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> a <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> volat jako odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="6e277-109">Note that the <xref:System.Windows.Data.CollectionView.IsCurrentBeforeFirst%2A> and <xref:System.Windows.Data.CollectionView.IsCurrentAfterLast%2A> properties report whether the current record pointer has come to the beginning and the end of the list respectively so that <xref:System.Windows.Data.CollectionView.MoveCurrentToFirst%2A> and <xref:System.Windows.Data.CollectionView.MoveCurrentToLast%2A> can be called as appropriately.</span></span>  
  
 <span data-ttu-id="6e277-110">Vlastnost <xref:System.Windows.Data.CollectionView.CurrentItem%2A> zobrazení je převedena jako `Order`, která vrátí aktuální položku objednávky v kolekci.</span><span class="sxs-lookup"><span data-stu-id="6e277-110">The <xref:System.Windows.Data.CollectionView.CurrentItem%2A> property of the view is cast as an `Order` to return the current order item in the collection.</span></span>  
  
 [!code-csharp[CollectionView#OnButton](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionView/CSharp/Page1.xaml.cs#onbutton)]
 [!code-vb[CollectionView#OnButton](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionView/VisualBasic/Page1.xaml.vb#onbutton)]  
  
## <a name="see-also"></a><span data-ttu-id="6e277-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e277-111">See also</span></span>

- [<span data-ttu-id="6e277-112">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="6e277-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="6e277-113">Řazení dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="6e277-113">Sort Data in a View</span></span>](how-to-sort-data-in-a-view.md)
- [<span data-ttu-id="6e277-114">Filtrování dat v zobrazení</span><span class="sxs-lookup"><span data-stu-id="6e277-114">Filter Data in a View</span></span>](how-to-filter-data-in-a-view.md)
- [<span data-ttu-id="6e277-115">Řazení a seskupení dat pomocí zobrazení XAML</span><span class="sxs-lookup"><span data-stu-id="6e277-115">Sort and Group Data Using a View in XAML</span></span>](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [<span data-ttu-id="6e277-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="6e277-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
