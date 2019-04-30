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
ms.openlocfilehash: c4539847368c1a5789e99ec92106d17077ed5943
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770835"
---
# <a name="how-to-override-the-panel-onrender-method"></a>Postupy: Přepsání metody panelu OnRender
Tento příklad ukazuje, jak přepsat <xref:System.Windows.Controls.Panel.OnRender%2A> metoda <xref:System.Windows.Controls.Panel> Chcete-li přidat vlastní grafické efekty na prvek rozložení.  
  
## <a name="example"></a>Příklad  
 Použití <xref:System.Windows.Controls.Panel.OnRender%2A> metody, chcete-li přidat grafické efekty na prvek vykreslené panelu. Například můžete použít tuto metodu Chcete-li přidat vlastní ohraničení nebo účinky na pozadí. A <xref:System.Windows.Media.DrawingContext> objekt je předán jako argument, který poskytuje metody pro kreslení tvarů, textu, obrázků nebo videa. V důsledku toho tato metoda je užitečná pro přizpůsobení panelu.  
  
 [!code-csharp[LightWeightCustomPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LightWeightCustomPanel/CSharp/OffsetPanel.cs#1)]
 [!code-vb[LightWeightCustomPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LightWeightCustomPanel/visualbasic/offsetpanel.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Panel>
- [Přehled panelu](panels-overview.md)
- [Ukázka vlastních kruhové panelu](https://go.microsoft.com/fwlink/?LinkID=159982)
- [Témata s postupy](panel-how-to-topics.md)
