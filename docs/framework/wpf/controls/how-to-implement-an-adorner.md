---
title: "Postupy: Implementace doplňku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3f69fee64ea65e8d49cce523c85669993cc6bce
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="dfff0-102">Postupy: Implementace doplňku</span><span class="sxs-lookup"><span data-stu-id="dfff0-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="dfff0-103">Tento příklad ukazuje implementaci minimální adorner.</span><span class="sxs-lookup"><span data-stu-id="dfff0-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="dfff0-104">Poznámky pro implementátory</span><span class="sxs-lookup"><span data-stu-id="dfff0-104">Notes for Implementers</span></span>  
 <span data-ttu-id="dfff0-105">Je důležité si uvědomit, že ozdobného prvku neobsahují žádné vyplývajících vykreslování chování; zajištění, že adorner vykreslí má na starosti implementátor adorner.</span><span class="sxs-lookup"><span data-stu-id="dfff0-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="dfff0-106">Běžný způsob implementace vykreslování chování je přepsat <xref:System.Windows.UIElement.OnRender%2A> metoda a používat jednu nebo více <xref:System.Windows.Media.DrawingContext> pro vykreslení adorner vizuály podle potřeby (jak je uvedeno v tomto příkladu).</span><span class="sxs-lookup"><span data-stu-id="dfff0-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfff0-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="dfff0-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="dfff0-108">Popis</span><span class="sxs-lookup"><span data-stu-id="dfff0-108">Description</span></span>  
 <span data-ttu-id="dfff0-109">Vlastní adorner je vytvořen pomocí implementace třídy, která dědí z abstraktní <xref:System.Windows.Documents.Adorner> třídy.</span><span class="sxs-lookup"><span data-stu-id="dfff0-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="dfff0-110">Příklad adorner jednoduše adorns rozích <xref:System.Windows.UIElement> s kroužky přepsáním <xref:System.Windows.UIElement.OnRender%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="dfff0-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="dfff0-111">Kód</span><span class="sxs-lookup"><span data-stu-id="dfff0-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="dfff0-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="dfff0-112">See Also</span></span>  
 [<span data-ttu-id="dfff0-113">Přehled ozdobného prvku</span><span class="sxs-lookup"><span data-stu-id="dfff0-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)
