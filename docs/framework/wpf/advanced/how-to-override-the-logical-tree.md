---
title: "Postupy: Přetížení logického stromu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- overriding the logical tree [WPF]
- logical tree [WPF], overriding
ms.assetid: 0ae4d074-8113-4b06-b4fa-e0f39d4967a6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4cc6045d3505981d93f07347ebd49d57cd759774
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-override-the-logical-tree"></a>Postupy: Přetížení logického stromu
Ačkoli to není nezbytné ve většině případů, ovládacího prvku rozšířené autorům mít možnost přepsání logickém stromu.  
  
## <a name="example"></a>Příklad  
 Tento příklad popisuje postup podtřídami <xref:System.Windows.Controls.StackPanel> k přepsání logickém stromu. v takovém případě vynutit chování, že panelu může mít pouze a učiní pouze jeden podřízený element. To není nezbytně prakticky žádoucí chování, ale zobrazí se zde jako prostředek ilustrující tento scénář pro přepsání elementu normální logickém stromu.  
  
 [!code-csharp[LogicalOverride#SingletonPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LogicalOverride/CSharp/SDKSampleLibrary/class1.cs#singletonpanel)]  
  
 Další informace o logickém stromu najdete v tématu [stromy v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).
