---
title: 'Postupy: Implementace oznámení změn vlastností'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: 7a8ab232019f1266095091cd4e1ce6e7fec63207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587804"
---
# <a name="how-to-implement-property-change-notification"></a>Postupy: Implementace oznámení změn vlastností
Pro podporu <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> vazby vazby vlastnosti cílové automaticky odrážejí změny dynamické vazby zdroje (například mít podokno náhledu automaticky aktualizovat, když uživatel upravuje formulář), aby vaše třída je potřeba poskytnout správné změněná vlastnost oznámení. Tento příklad ukazuje, jak vytvořit třídu, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Příklad  
 K implementaci <xref:System.ComponentModel.INotifyPropertyChanged> musíte deklarovat <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> události a vytvořit `OnPropertyChanged` metoda. Pak pro každou vlastnost je třeba změnit oznámení pro volání `OnPropertyChanged` vždy, když se aktualizuje vlastnost.  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Chcete-li zobrazit příklad, jak `Person` třídy lze použít pro podporu <xref:System.Windows.Data.BindingMode.TwoWay> vazby, naleznete v tématu [řídit, kdy k aktualizaci textu TextBox zdroji](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Viz také:
- [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md)
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
