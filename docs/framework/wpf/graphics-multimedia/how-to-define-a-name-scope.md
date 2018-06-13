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
ms.openlocfilehash: 689c8187fcf17ef48a73bc5a6fc4928f3be1a078
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559712"
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="b0893-102">Postupy: Definování rozsahu názvů</span><span class="sxs-lookup"><span data-stu-id="b0893-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="b0893-103">Pro animaci s <xref:System.Windows.Media.Animation.Storyboard> v kódu, je nutné vytvořit <xref:System.Windows.NameScope> a zaregistrovat element vlastnící tento název oboru názvů cílové objekty.</span><span class="sxs-lookup"><span data-stu-id="b0893-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="b0893-104">V následujícím příkladu <xref:System.Windows.NameScope> se vytvoří pro `myMainPanel`.</span><span class="sxs-lookup"><span data-stu-id="b0893-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="b0893-105">Dvě tlačítka `button1` a `button2`, jsou přidány do panelu a jejich názvy zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="b0893-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="b0893-106">Několik animace a <xref:System.Windows.Media.Animation.Storyboard> se vytvářejí.</span><span class="sxs-lookup"><span data-stu-id="b0893-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="b0893-107">Do scénáře <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda se používá ke spuštění animace.</span><span class="sxs-lookup"><span data-stu-id="b0893-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="b0893-108">Protože `button1`, `button2`, a `myMainPanel` všechny sdílet stejný obor názvů, kterékoli z nich lze použít s <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda spuštění animace.</span><span class="sxs-lookup"><span data-stu-id="b0893-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0893-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0893-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="b0893-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0893-110">See Also</span></span>  
 [<span data-ttu-id="b0893-111">Animace vlastnosti pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="b0893-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="b0893-112">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="b0893-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
