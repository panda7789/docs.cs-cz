---
title: 'Postupy: Získání položky ListBoxItem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox controls [WPF], getting a ListBoxItem
- ListBoxItem [WPF]
ms.assetid: da877c6f-5fd8-40cb-8909-225cbfd99aa5
ms.openlocfilehash: 27a435feb4a941c77af221ab25bd63ea98b16e92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910322"
---
# <a name="how-to-get-a-listboxitem"></a>Postupy: Získání položky ListBoxItem
Pokud potřebujete získat konkrétní <xref:System.Windows.Controls.ListBoxItem> konkrétního indexu ve <xref:System.Windows.Controls.ListBox>, můžete použít <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje <xref:System.Windows.Controls.ListBox> a jejích položek.  
  
 [!code-xaml[ListBoxItems#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml#1)]  
  
 Následující příklad ukazuje, jak k získání položky určením index položky v <xref:System.Windows.Controls.ItemContainerGenerator.ContainerFromIndex%2A> vlastnost <xref:System.Windows.Controls.ItemContainerGenerator>.  
  
 [!code-csharp[ListBoxItems#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ListBoxItems#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#2)]  
  
 Po načtení položky seznamu můžete zobrazit obsah položky, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[ListBoxItems#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxItems/CSharp/Window1.xaml.cs#3)]
 [!code-vb[ListBoxItems#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListBoxItems/VisualBasic/Window1.xaml.vb#3)]
