---
title: 'Postupy: Nastavení zablokovatelného objektu jen pro čtení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 5748b7929db18578bbe00e3217b1578ac5fbc0f4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614594"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="17e5a-102">Postupy: Nastavení zablokovatelného objektu jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17e5a-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="17e5a-103">Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Freezable> voláním jen pro čtení jeho <xref:System.Windows.Freezable.Freeze%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="17e5a-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="17e5a-104">Nelze zmrazit <xref:System.Windows.Freezable> objektu, pokud je některý z následujících podmínek `true` o objektu:</span><span class="sxs-lookup"><span data-stu-id="17e5a-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
- <span data-ttu-id="17e5a-105">Má animovat nebo data vázané vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="17e5a-105">It has animated or data bound properties.</span></span>  
  
- <span data-ttu-id="17e5a-106">Obsahuje vlastnosti, které určil institut NIST dynamický prostředek.</span><span class="sxs-lookup"><span data-stu-id="17e5a-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="17e5a-107">Další informace o dynamické prostředky, najdete v článku [prostředky XAML](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="17e5a-107">For more information about dynamic resources, see the [XAML Resources](xaml-resources.md).</span></span>  
  
- <span data-ttu-id="17e5a-108">Obsahuje <xref:System.Windows.Freezable> podřízených objektů, které nelze zmrazit.</span><span class="sxs-lookup"><span data-stu-id="17e5a-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="17e5a-109">Pokud jsou tyto podmínky `false` pro vaše <xref:System.Windows.Freezable> objektů a vy nemáte v úmyslu upravit, vezměte v úvahu zmrazení to zlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="17e5a-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17e5a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="17e5a-110">Example</span></span>  
 <span data-ttu-id="17e5a-111">V následujícím příkladu se zablokuje <xref:System.Windows.Media.SolidColorBrush>, což je typ <xref:System.Windows.Freezable> objektu.</span><span class="sxs-lookup"><span data-stu-id="17e5a-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="17e5a-112">Další informace o <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="17e5a-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e5a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17e5a-113">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="17e5a-114">Přehled zablokovatelných objektů</span><span class="sxs-lookup"><span data-stu-id="17e5a-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="17e5a-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="17e5a-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
