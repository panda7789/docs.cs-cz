---
title: 'Postupy: Odebrání doplňku z elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: a3e1b08a9ec5e2cd60c063ced5e5f0d5874f8184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>Postupy: Odebrání doplňku z elementu
Tento příklad ukazuje, jak programově odebrat konkrétní adorner ze zadané <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Příklad  
 Tento příklad kódu podrobné Odebere první adorner v poli ozdobného prvku vrácený <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  V tomto příkladu se stane, načíst ozdobného prvku na <xref:System.Windows.UIElement> s názvem *hodnotu myTextBox*.  Pokud element zadané ve volání <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> nemá žádné ozdobného prvku `null` je vrácen.  Tento kód explicitně kontroluje pro pole hodnotu null a je nejvhodnější pro aplikace, kde je očekávána null pole relativně běžně k dispozici.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>Příklad  
 Tento příklad kódu zhuštěné je funkčně srovnatelný podrobné výše uvedený příklad. Tento kód nekontroluje explicitně pro pole hodnotu null, takže je možné, <xref:System.NullReferenceException> může být vyvolána výjimka.  Tento kód je nejvhodnější pro aplikace, kde null pole musí být výjimečných.  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled doplňků pro úpravy](../../../../docs/framework/wpf/controls/adorners-overview.md)
