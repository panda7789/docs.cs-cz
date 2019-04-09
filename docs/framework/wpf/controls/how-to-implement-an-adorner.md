---
title: 'Postupy: Implementace doplňku pro úpravy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: da318fee42b4628351217774de2a2225cfb21ee1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120806"
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="556ba-102">Postupy: Implementace doplňku pro úpravy</span><span class="sxs-lookup"><span data-stu-id="556ba-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="556ba-103">Tento příklad ukazuje implementaci minimální doplněk pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="556ba-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="556ba-104">Poznámky pro implementátory</span><span class="sxs-lookup"><span data-stu-id="556ba-104">Notes for Implementers</span></span>  
 <span data-ttu-id="556ba-105">Je důležité si uvědomit, že doplňky pro úpravy neobsahují žádné vlastní vykreslování chování; zajištění, že pro úpravy vykreslí zodpovídá za implementátora doplněk pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="556ba-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="556ba-106">Běžný způsob implementace chování vykreslování je k přepsání <xref:System.Windows.UIElement.OnRender%2A> metoda a používat jednu nebo více <xref:System.Windows.Media.DrawingContext> objekty k vykreslení doplněk pro úpravy vizuály podle potřeby (jak je znázorněno v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="556ba-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="556ba-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="556ba-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="556ba-108">Popis</span><span class="sxs-lookup"><span data-stu-id="556ba-108">Description</span></span>  
 <span data-ttu-id="556ba-109">Vlastní doplněk pro úpravy je vytvořen pomocí implementace, která dědí z abstraktní třídy <xref:System.Windows.Documents.Adorner> třídy.</span><span class="sxs-lookup"><span data-stu-id="556ba-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="556ba-110">Doplněk pro úpravy příklad jednoduše adorns rohů <xref:System.Windows.UIElement> s kruhy tak, že přepíšete <xref:System.Windows.UIElement.OnRender%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="556ba-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="556ba-111">Kód</span><span class="sxs-lookup"><span data-stu-id="556ba-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="556ba-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="556ba-112">See also</span></span>

- [<span data-ttu-id="556ba-113">Přehled doplňků</span><span class="sxs-lookup"><span data-stu-id="556ba-113">Adorners Overview</span></span>](adorners-overview.md)
