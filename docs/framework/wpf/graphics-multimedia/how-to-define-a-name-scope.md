---
title: 'Postupy: Definování rozsahu názvů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
ms.openlocfilehash: 656c1e9af11697cd4a1253bdab673887765976a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674463"
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="af68d-102">Postupy: Definování rozsahu názvů</span><span class="sxs-lookup"><span data-stu-id="af68d-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="af68d-103">Pro animaci s <xref:System.Windows.Media.Animation.Storyboard> v kódu, musíte vytvořit <xref:System.Windows.NameScope> a názvy cílové objektů zaregistrovat element vlastnící tento obor názvů.</span><span class="sxs-lookup"><span data-stu-id="af68d-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="af68d-104">V následujícím příkladu <xref:System.Windows.NameScope> se vytvoří pro `myMainPanel`.</span><span class="sxs-lookup"><span data-stu-id="af68d-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="af68d-105">Dvě tlačítka `button1` a `button2`, jsou přidány do panelu a jejich názvy zaregistrovaný.</span><span class="sxs-lookup"><span data-stu-id="af68d-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="af68d-106">Animací několik a <xref:System.Windows.Media.Animation.Storyboard> jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="af68d-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="af68d-107">Do scénáře <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda se používá ke spuštění animací.</span><span class="sxs-lookup"><span data-stu-id="af68d-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="af68d-108">Protože `button1`, `button2`, a `myMainPanel` sdílejí stejný obor názvů, některý z nich je možné s <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda spuštění animací.</span><span class="sxs-lookup"><span data-stu-id="af68d-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af68d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="af68d-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="af68d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af68d-110">See also</span></span>
- [<span data-ttu-id="af68d-111">Animace vlastnosti pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="af68d-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="af68d-112">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="af68d-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
