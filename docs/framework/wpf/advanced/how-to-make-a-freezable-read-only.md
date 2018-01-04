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
ms.workload: dotnet
ms.openlocfilehash: aa6d3f7109e8258dff0a07556bc8572f6071c961
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="cb696-102">Postupy: Nastavení zablokovatelného režimu jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cb696-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="cb696-103">Tento příklad ukazuje, jak provádět <xref:System.Windows.Freezable> jen pro čtení voláním jeho <xref:System.Windows.Freezable.Freeze%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="cb696-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="cb696-104">Nelze ukotvit <xref:System.Windows.Freezable> objektu, pokud je některého z následujících podmínek `true` o objektu:</span><span class="sxs-lookup"><span data-stu-id="cb696-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="cb696-105">Má animovaný nebo data vázané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cb696-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="cb696-106">Obsahuje vlastnosti, které jsou nastaveny dynamické prostředek.</span><span class="sxs-lookup"><span data-stu-id="cb696-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="cb696-107">Další informace o dynamické prostředky, najdete v článku [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="cb696-107">For more information about dynamic resources, see the [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="cb696-108">Obsahuje <xref:System.Windows.Freezable> dílčí objekty, které nelze ukotvit.</span><span class="sxs-lookup"><span data-stu-id="cb696-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="cb696-109">Pokud tyto podmínky se `false` pro vaše <xref:System.Windows.Freezable> objektu a vy nemáte v úmyslu upravit, zvažte zmrazení mohla získat výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="cb696-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb696-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="cb696-110">Example</span></span>  
 <span data-ttu-id="cb696-111">V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush>, který je typem <xref:System.Windows.Freezable> objektu.</span><span class="sxs-lookup"><span data-stu-id="cb696-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="cb696-112">Další informace o <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cb696-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb696-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb696-113">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="cb696-114">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="cb696-114">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="cb696-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="cb696-115">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
