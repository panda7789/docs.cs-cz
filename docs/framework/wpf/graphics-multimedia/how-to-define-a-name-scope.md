---
title: "Postupy: Definování rozsahu názvů"
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
helpviewer_keywords:
- name scope [WPF], defining
- Storyboards [WPF], animating in procedural code
- animation [WPF], Storyboards [WPF], in procedural code
ms.assetid: 4f361925-6a08-40dc-8231-a61111c6b28b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8d3199de53f93f07e36e7a6e0a02ed9e80b4d591
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-name-scope"></a><span data-ttu-id="619a5-102">Postupy: Definování rozsahu názvů</span><span class="sxs-lookup"><span data-stu-id="619a5-102">How to: Define a Name Scope</span></span>
<span data-ttu-id="619a5-103">Pro animaci s <xref:System.Windows.Media.Animation.Storyboard> v kódu, je nutné vytvořit <xref:System.Windows.NameScope> a zaregistrovat element vlastnící tento název oboru názvů cílové objekty.</span><span class="sxs-lookup"><span data-stu-id="619a5-103">To animate with <xref:System.Windows.Media.Animation.Storyboard> in code, you must create a <xref:System.Windows.NameScope> and register the target objects' names with the element that owns that name scope.</span></span> <span data-ttu-id="619a5-104">V následujícím příkladu <xref:System.Windows.NameScope> se vytvoří pro `myMainPanel`.</span><span class="sxs-lookup"><span data-stu-id="619a5-104">In the following example, a <xref:System.Windows.NameScope> is created for `myMainPanel`.</span></span> <span data-ttu-id="619a5-105">Dvě tlačítka `button1` a `button2`, jsou přidány do panelu a jejich názvy zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="619a5-105">Two buttons, `button1` and `button2`, are added to the panel, and their names registered.</span></span> <span data-ttu-id="619a5-106">Několik animace a <xref:System.Windows.Media.Animation.Storyboard> se vytvářejí.</span><span class="sxs-lookup"><span data-stu-id="619a5-106">Several animations and a <xref:System.Windows.Media.Animation.Storyboard> are created.</span></span> <span data-ttu-id="619a5-107">Do scénáře <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda se používá ke spuštění animace.</span><span class="sxs-lookup"><span data-stu-id="619a5-107">The storyboard's <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method is used to start the animations.</span></span>  
  
 <span data-ttu-id="619a5-108">Protože `button1`, `button2`, a `myMainPanel` všechny sdílet stejný obor názvů, kterékoli z nich lze použít s <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda spuštění animace.</span><span class="sxs-lookup"><span data-stu-id="619a5-108">Because `button1`, `button2`, and `myMainPanel` all share the same name scope, any one of them can be used with the <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method to start the animations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="619a5-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="619a5-109">Example</span></span>  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a><span data-ttu-id="619a5-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="619a5-110">See Also</span></span>  
 [<span data-ttu-id="619a5-111">Animace vlastnost pomocí scénáře</span><span class="sxs-lookup"><span data-stu-id="619a5-111">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="619a5-112">Animace – přehled</span><span class="sxs-lookup"><span data-stu-id="619a5-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
