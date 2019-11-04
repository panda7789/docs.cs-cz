---
title: 'Postupy: Vymazání připojení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bindings [WPF], clearing
- clearing bindings [WPF]
- data binding [WPF], clearing bindings
ms.assetid: 73962a93-32a9-4bcd-9240-bcfbb239093a
ms.openlocfilehash: 66f7eb0209d23660b9c7351ca793f509b2f4bb8d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458874"
---
# <a name="how-to-clear-bindings"></a>Postupy: Vymazání připojení
Tento příklad ukazuje, jak vymazat vazby z objektu.  
  
## <a name="example"></a>Příklad  
 Chcete-li vymazat vazbu z jednotlivé vlastnosti objektu, zavolejte <xref:System.Windows.Data.BindingOperations.ClearBinding%2A>, jak je znázorněno v následujícím příkladu. Následující příklad odebere vazbu z <xref:System.Windows.Controls.TextBlock.TextProperty> *MyText*, objekt <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[CodeOnlyBinding#ClearBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CodeOnlyBinding/CSharp/binding.cs#clearbinding)]
 [!code-vb[CodeOnlyBinding#ClearBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CodeOnlyBinding/VisualBasic/App.vb#clearbinding)]  
  
 Zrušením vazby se odstraní vazba, aby se hodnota vlastnosti závislosti změnila na cokoliv, co by bylo bez vazby. Tato hodnota může být výchozí hodnota, zděděná hodnota nebo hodnota z vazby šablony dat.  
  
 Chcete-li vymazat vazby ze všech možných vlastností objektu, použijte <xref:System.Windows.Data.BindingOperations.ClearAllBindings%2A>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Data.BindingOperations>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
