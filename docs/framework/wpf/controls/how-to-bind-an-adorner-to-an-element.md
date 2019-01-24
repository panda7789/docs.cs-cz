---
title: 'Postupy: Připojení doplňku k elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
ms.openlocfilehash: 91dd047e65af8791f8e558a9a3b622ef05e2cb77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606319"
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Postupy: Připojení doplňku k elementu
Tento příklad ukazuje, jak prostřednictvím kódu programu připojení doplňku k zadané <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Příklad  
 K připojení doplňku k konkrétní <xref:System.Windows.UIElement>, postupujte podle těchto kroků:  
  
1.  Volání `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> získat <xref:System.Windows.Documents.AdornerLayer> objekt pro <xref:System.Windows.UIElement> chcete být opatřený. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> provede se vizuální strom začínající v zadaném **UIElement**a vrátí první vrstvu doplněk pro úpravy, které nalezne. (Pokud se nenajdou žádné vrstvy doplněk pro úpravy, metoda vrátí hodnotu null.)  
  
2.  Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metodu pro vytvoření vazby doplněk pro úpravy k cíli **UIElement**.  
  
 Následující příklad vytvoří vazbu SimpleCircleAdorner (popsaný výš) k <xref:System.Windows.Controls.TextBox> s názvem *hodnotu myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pro vazbu na jiný prvek pro úpravy v tuto chvíli nepodporuje.  
  
## <a name="see-also"></a>Viz také:
- [Přehled doplňků pro úpravy](../../../../docs/framework/wpf/controls/adorners-overview.md)
