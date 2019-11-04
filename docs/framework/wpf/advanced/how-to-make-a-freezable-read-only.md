---
title: 'Postupy: Nastavení zablokovatelného režimu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460067"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="1ed8a-102">Postupy: Nastavení zablokovatelného režimu jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1ed8a-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="1ed8a-103">Tento příklad ukazuje, jak nastavit <xref:System.Windows.Freezable> jen pro čtení, voláním jeho metody <xref:System.Windows.Freezable.Freeze%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ed8a-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="1ed8a-104">Objekt <xref:System.Windows.Freezable> nelze ukotvit, je-li některá z následujících podmínek `true` o objektu:</span><span class="sxs-lookup"><span data-stu-id="1ed8a-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
- <span data-ttu-id="1ed8a-105">Obsahuje animované nebo vlastnosti vázaného na data.</span><span class="sxs-lookup"><span data-stu-id="1ed8a-105">It has animated or data bound properties.</span></span>  
  
- <span data-ttu-id="1ed8a-106">Obsahuje vlastnosti, které jsou nastaveny dynamickým prostředkem.</span><span class="sxs-lookup"><span data-stu-id="1ed8a-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="1ed8a-107">Další informace o dynamických prostředcích najdete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="1ed8a-107">For more information about dynamic resources, see the [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
- <span data-ttu-id="1ed8a-108">Obsahuje <xref:System.Windows.Freezable> dílčích objektů, které nelze zmrazit.</span><span class="sxs-lookup"><span data-stu-id="1ed8a-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="1ed8a-109">Pokud jsou tyto podmínky `false` pro váš objekt <xref:System.Windows.Freezable> a nechcete ho upravovat, zvažte jeho zmrazení, abyste získali výhody výkonu.</span><span class="sxs-lookup"><span data-stu-id="1ed8a-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ed8a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ed8a-110">Example</span></span>  
 <span data-ttu-id="1ed8a-111">Následující příklad zablokuje <xref:System.Windows.Media.SolidColorBrush>, což je typ objektu <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="1ed8a-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="1ed8a-112">Další informace o <xref:System.Windows.Freezable> objektů naleznete v tématu [Přehled objektů Freezable](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1ed8a-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed8a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ed8a-113">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="1ed8a-114">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="1ed8a-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="1ed8a-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="1ed8a-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
