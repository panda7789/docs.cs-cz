---
title: 'Postupy: Implementace doplňku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
ms.openlocfilehash: 53a25396ba5d8a5c78e850e636b7c882c03d5152
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362640"
---
# <a name="how-to-implement-an-adorner"></a>Postupy: Implementace doplňku
Tento příklad ukazuje implementaci minimální doplněk pro úpravy.  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Je důležité si uvědomit, že doplňky pro úpravy neobsahují žádné vlastní vykreslování chování; zajištění, že pro úpravy vykreslí zodpovídá za implementátora doplněk pro úpravy.   Běžný způsob implementace chování vykreslování je k přepsání <xref:System.Windows.UIElement.OnRender%2A> metoda a používat jednu nebo více <xref:System.Windows.Media.DrawingContext> objekty k vykreslení doplněk pro úpravy vizuály podle potřeby (jak je znázorněno v tomto příkladu).  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Vlastní doplněk pro úpravy je vytvořen pomocí implementace, která dědí z abstraktní třídy <xref:System.Windows.Documents.Adorner> třídy.  Doplněk pro úpravy příklad jednoduše adorns rohů <xref:System.Windows.UIElement> s kruhy tak, že přepíšete <xref:System.Windows.UIElement.OnRender%2A> metody.  
  
### <a name="code"></a>Kód  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled doplňků pro úpravy](adorners-overview.md)
