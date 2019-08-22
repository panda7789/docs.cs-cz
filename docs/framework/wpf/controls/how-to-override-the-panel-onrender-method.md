---
title: 'Postupy: Přepsání metody panelu OnRender'
ms.date: 03/30/2017
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
ms.openlocfilehash: 23c3353e130585ed83726816a467ca73f6aa9152
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666706"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Postupy: Přepsání metody panelu OnRender
Tento příklad ukazuje, jak přepsat <xref:System.Windows.Controls.Panel.OnRender%2A> <xref:System.Windows.Controls.Panel> metodu pro přidání vlastních grafických efektů do prvku rozložení.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.Panel.OnRender%2A> Použijte metodu pro přidání grafických efektů do vykresleného panelu elementu. Můžete například použít tuto metodu k přidání vlastních efektů ohraničení nebo pozadí. <xref:System.Windows.Media.DrawingContext> Objekt je předán jako argument, který poskytuje metody pro kreslení tvarů, textu, obrázků a videí. V důsledku toho je tato metoda užitečná pro přizpůsobení objektu panelu.  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Panel>
- [Přehled panelu](panels-overview.md)
- [Témata s postupy](panel-how-to-topics.md)
