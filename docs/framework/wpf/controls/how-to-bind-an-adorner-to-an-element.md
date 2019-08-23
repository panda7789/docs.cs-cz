---
title: 'Postupy: Svázání doplňku pro úpravy s elementem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: e8c7eb929042bfe1455bfc9bf459fc466de5c397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923498"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Postupy: Svázání doplňku pro úpravy s elementem
Tento příklad ukazuje, jak programově navazovat Doplňky na určenou <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Příklad  
 Chcete-li navazovat Doplňky na konkrétní <xref:System.Windows.UIElement>, postupujte takto:  
  
1. `static` Zavolejte metodu <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pro získání<xref:System.Windows.Documents.AdornerLayer> objektu ,<xref:System.Windows.UIElement> který má být podrobnější. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>provede sestavování vizuálního stromu, počínaje zadaným prvekem **UIElement**a vrátí první nalezenou vrstvu doplňku. (Pokud se nenaleznou žádné vrstvy doplňků, vrátí metoda hodnotu null.)  
  
2. Zavolejte metodu pro svázání doplňku k cílovému prvku **UIElement.** <xref:System.Windows.Documents.AdornerLayer.Add%2A>  
  
 Následující příklad váže SimpleCircleAdorner (zobrazený výše) k <xref:System.Windows.Controls.TextBox> pojmenovanému *MyTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
> Použití [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro svázání doplňku s jiným prvkem není aktuálně podporováno.  
  
## <a name="see-also"></a>Viz také:

- [Přehled doplňků pro úpravy](adorners-overview.md)
