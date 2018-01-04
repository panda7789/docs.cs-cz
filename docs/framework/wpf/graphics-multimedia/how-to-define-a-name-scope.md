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
ms.workload: dotnet
ms.openlocfilehash: 3007088f849f40e4e9b4f1846c19c98c33e95c17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-name-scope"></a>Postupy: Definování rozsahu názvů
Pro animaci s <xref:System.Windows.Media.Animation.Storyboard> v kódu, je nutné vytvořit <xref:System.Windows.NameScope> a zaregistrovat element vlastnící tento název oboru názvů cílové objekty. V následujícím příkladu <xref:System.Windows.NameScope> se vytvoří pro `myMainPanel`. Dvě tlačítka `button1` a `button2`, jsou přidány do panelu a jejich názvy zaregistrován. Několik animace a <xref:System.Windows.Media.Animation.Storyboard> se vytvářejí. Do scénáře <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda se používá ke spuštění animace.  
  
 Protože `button1`, `button2`, a `myMainPanel` všechny sdílet stejný obor názvů, kterékoli z nich lze použít s <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda spuštění animace.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a>Viz také  
 [Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
