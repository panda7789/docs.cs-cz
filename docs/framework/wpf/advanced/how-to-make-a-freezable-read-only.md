---
title: "Postupy: Nastavení zablokovatelného režimu jen pro čtení"
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
helpviewer_keywords: Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c407a2fcccfbda29ba23f63ba6ae71302c734d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="c3588-102">Postupy: Nastavení zablokovatelného režimu jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c3588-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="c3588-103">Tento příklad ukazuje, jak provádět <xref:System.Windows.Freezable> jen pro čtení voláním jeho <xref:System.Windows.Freezable.Freeze%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="c3588-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="c3588-104">Nelze ukotvit <xref:System.Windows.Freezable> objektu, pokud je některého z následujících podmínek `true` o objektu:</span><span class="sxs-lookup"><span data-stu-id="c3588-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="c3588-105">Má animovaný nebo data vázané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c3588-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="c3588-106">Obsahuje vlastnosti, které jsou nastaveny dynamické prostředek.</span><span class="sxs-lookup"><span data-stu-id="c3588-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="c3588-107">Další informace o dynamické prostředky, najdete v článku [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="c3588-107">For more information about dynamic resources, see the [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="c3588-108">Obsahuje <xref:System.Windows.Freezable> dílčí objekty, které nelze ukotvit.</span><span class="sxs-lookup"><span data-stu-id="c3588-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="c3588-109">Pokud tyto podmínky se `false` pro vaše <xref:System.Windows.Freezable> objektu a vy nemáte v úmyslu upravit, zvažte zmrazení mohla získat výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="c3588-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3588-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c3588-110">Example</span></span>  
 <span data-ttu-id="c3588-111">V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush>, který je typem <xref:System.Windows.Freezable> objektu.</span><span class="sxs-lookup"><span data-stu-id="c3588-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="c3588-112">Další informace o <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c3588-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3588-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c3588-113">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="c3588-114">Zmrazitelné objekty – přehled</span><span class="sxs-lookup"><span data-stu-id="c3588-114">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="c3588-115">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="c3588-115">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
