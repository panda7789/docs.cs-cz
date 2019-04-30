---
title: 'Postupy: Vymazání vazeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 8140928d44555e399ddf4ebd73407a251ad3cffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931466"
---
# <a name="how-to-clear-bindings"></a>Postupy: Vymazání vazeb
Tento příklad ukazuje, jak vymazání připojení z objektu.  
  
## <a name="example"></a>Příklad  
 Chcete-li zrušit vazbu z jednotlivých vlastností pro objekt, zavolejte <xref:System.Windows.Data.BindingOperations.ClearBinding%2A> jak je znázorněno v následujícím příkladu. Následující příklad odebere vazbu z <xref:System.Windows.Controls.TextBlock.TextProperty> z *mytext*, <xref:System.Windows.Controls.TextBlock> objektu.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Vymazává se vazba odebere vazbu tak, aby hodnota vlastnosti závislostí se změní na cokoli, co by byl bez vazby. Tato hodnota může být výchozí hodnotu, zděděná hodnota nebo hodnota z datové vazby šablony.  
  
 Chcete-li vymazání připojení ze všech možných vlastností pro objekt, použijte <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.BindingOperations>
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
