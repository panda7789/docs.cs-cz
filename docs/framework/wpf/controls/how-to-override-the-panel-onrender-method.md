---
title: "Postupy: Přetížení metody panelu OnRender"
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
f1_keywords:
- overriding OnRender method
- Panel control, overriding OnRender method
- OnRender method
- controls, Panel, overriding OnRender method
helpviewer_keywords:
- overriding OnRender method of Panel control [WPF]
- OnRender method [WPF], overriding
- Panel control [WPF], overriding OnRender method
ms.assetid: 57397834-a085-4e36-90ab-416fad98f341
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 958595cdfa521b372270d6283c7134ef0ba0ef79
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-override-the-panel-onrender-method"></a>Postupy: Přetížení metody panelu OnRender
Tento příklad ukazuje, jak lze přepsat <xref:System.Windows.Controls.Panel.OnRender%2A> metodu <xref:System.Windows.Controls.Panel> Chcete-li přidat vlastní grafické efekty do elementu rozložení.  
  
## <a name="example"></a>Příklad  
 Použití <xref:System.Windows.Controls.Panel.OnRender%2A> metoda-li přidat grafické efekty vykreslené panel prvek. Například můžete použít tuto metodu můžete přidat vlastní ohraničení nebo pozadí účinky. A <xref:System.Windows.Media.DrawingContext> objektu je předat jako argument, který poskytuje metody pro kreslení tvarů, text, obrázky nebo videa. V důsledku toho tato metoda je užitečná pro přizpůsobení panelů objektu.  
  
 [!code-csharp[LightWeightCustomPanel#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Panel>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Vlastní paprskového panelu ukázkové](http://go.microsoft.com/fwlink/?LinkID=159982)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/panel-how-to-topics.md)
