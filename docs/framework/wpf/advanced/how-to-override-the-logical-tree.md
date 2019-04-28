---
title: 'Postupy: Přepsání logického stromu'
ms.date: 03/30/2017
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
ms.openlocfilehash: bf3459fff1a90326794d6713dd39c73596b0e960
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768443"
---
# <a name="how-to-override-the-logical-tree"></a>Postupy: Přepsání logického stromu
I když není nutné ve většině případů, pokročilé ovládací prvek Autoři mají možnost přetížení logického stromu.  
  
## <a name="example"></a>Příklad  
 Tento příklad popisuje, jak podtřídy <xref:System.Windows.Controls.StackPanel> přepsání logického stromu, v tomto případě k vynucení chování, že na panelu může mít jenom a budou vykreslovat pouze jeden podřízený prvek. To není nezbytně prakticky žádoucí chování, ale je znázorněna zde jako způsob ilustrující scénář pro přepsání elementu normální Logická stromová struktura.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Další informace o logickém stromu, naleznete v tématu [stromy v subsystému WPF](trees-in-wpf.md).
