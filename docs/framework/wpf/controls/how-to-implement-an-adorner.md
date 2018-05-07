---
title: 'Postupy: Implementace doplňku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: f5b0ed080a413546a3b985055858e209f9f347eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-an-adorner"></a>Postupy: Implementace doplňku
Tento příklad ukazuje implementaci minimální adorner.  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Je důležité si uvědomit, že ozdobného prvku neobsahují žádné vyplývajících vykreslování chování; zajištění, že adorner vykreslí má na starosti implementátor adorner.   Běžný způsob implementace vykreslování chování je přepsat <xref:System.Windows.UIElement.OnRender%2A> metoda a používat jednu nebo více <xref:System.Windows.Media.DrawingContext> pro vykreslení adorner vizuály podle potřeby (jak je uvedeno v tomto příkladu).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Vlastní adorner je vytvořen pomocí implementace třídy, která dědí z abstraktní <xref:System.Windows.Documents.Adorner> třídy.  Příklad adorner jednoduše adorns rozích <xref:System.Windows.UIElement> s kroužky přepsáním <xref:System.Windows.UIElement.OnRender%2A> metoda.  
  
### <a name="code"></a>Kód  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled doplňků pro úpravy](../../../../docs/framework/wpf/controls/adorners-overview.md)
