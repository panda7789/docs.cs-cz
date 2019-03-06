---
title: 'Postupy: Nastavení zablokovatelného režimu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 874724584b44c17ff6c01331295cfa1a60978d54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360346"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="2a2c5-102">Postupy: Nastavení zablokovatelného režimu jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2a2c5-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="2a2c5-103">Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Freezable> voláním jen pro čtení jeho <xref:System.Windows.Freezable.Freeze%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2a2c5-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="2a2c5-104">Nelze zmrazit <xref:System.Windows.Freezable> objektu, pokud je některý z následujících podmínek `true` o objektu:</span><span class="sxs-lookup"><span data-stu-id="2a2c5-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="2a2c5-105">Má animovat nebo data vázané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2a2c5-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="2a2c5-106">Obsahuje vlastnosti, které určil institut NIST dynamický prostředek.</span><span class="sxs-lookup"><span data-stu-id="2a2c5-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="2a2c5-107">Další informace o dynamické prostředky, najdete v článku [prostředky XAML](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="2a2c5-107">For more information about dynamic resources, see the [XAML Resources](xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="2a2c5-108">Obsahuje <xref:System.Windows.Freezable> podřízených objektů, které nelze zmrazit.</span><span class="sxs-lookup"><span data-stu-id="2a2c5-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="2a2c5-109">Pokud jsou tyto podmínky `false` pro vaše <xref:System.Windows.Freezable> objektů a vy nemáte v úmyslu upravit, vezměte v úvahu zmrazení to zlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="2a2c5-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a2c5-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a2c5-110">Example</span></span>  
 <span data-ttu-id="2a2c5-111">V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush>, což je typ <xref:System.Windows.Freezable> objektu.</span><span class="sxs-lookup"><span data-stu-id="2a2c5-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="2a2c5-112">Další informace o <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2a2c5-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a2c5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a2c5-113">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="2a2c5-114">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="2a2c5-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="2a2c5-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="2a2c5-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
