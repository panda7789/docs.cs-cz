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
ms.openlocfilehash: 6afb59550d774109c62c283905495c76b0834b3d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370368"
---
# <a name="how-to-define-a-name-scope"></a>Postupy: Definování rozsahu názvů
Pro animaci s <xref:System.Windows.Media.Animation.Storyboard> v kódu, musíte vytvořit <xref:System.Windows.NameScope> a názvy cílové objektů zaregistrovat element vlastnící tento obor názvů. V následujícím příkladu <xref:System.Windows.NameScope> se vytvoří pro `myMainPanel`. Dvě tlačítka `button1` a `button2`, jsou přidány do panelu a jejich názvy zaregistrovaný. Animací několik a <xref:System.Windows.Media.Animation.Storyboard> jsou vytvořeny. Do scénáře <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda se používá ke spuštění animací.  
  
 Protože `button1`, `button2`, a `myMainPanel` sdílejí stejný obor názvů, některý z nich je možné s <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda spuštění animací.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/CSharp/ScopeExample.cs#namescopeexample)]
 [!code-vb[StoryboardBeginAnimation_procedural_snip#NameScopeExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StoryboardBeginAnimation_procedural_snip/visualbasic/scopeexample.vb#namescopeexample)]  
  
## <a name="see-also"></a>Viz také:
- [Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)
- [Přehled animace](animation-overview.md)
