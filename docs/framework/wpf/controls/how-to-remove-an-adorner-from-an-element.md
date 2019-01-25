---
title: 'Postupy: Odebrání doplňku z elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: eeefa83703ef9a4ffa7653042745d9acd58536f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695751"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>Postupy: Odebrání doplňku z elementu
Tento příklad ukazuje, jak programově odebrat konkrétní doplněk pro úpravy ze zadaného <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Příklad  
 Tento podrobný příklad odstraní první doplněk pro úpravy v poli doplňků pro úpravy vrácený <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  V tomto příkladu dojde k načtení ozdobného prvku na <xref:System.Windows.UIElement> s názvem *hodnotu myTextBox*.  Pokud element zadána ve volání <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> doplňky nemá `null` je vrácena.  Tento kód explicitně kontroluje pole s hodnotou null a je nejvhodnější pro aplikace, kde se očekává se poměrně běžnou pole s hodnotou null.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>Příklad  
 Tento příklad zhuštěnému kód je funkčně srovnatelný s komentářem výše uvedený příklad. Tento kód explicitně nekontroluje pro pole s hodnotou null, takže je možné, který <xref:System.NullReferenceException> může být vyvolána výjimka.  Tento kód je nejvhodnější pro aplikace, kde se očekává pole null docházet zřídka.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled doplňků pro úpravy](../../../../docs/framework/wpf/controls/adorners-overview.md)
