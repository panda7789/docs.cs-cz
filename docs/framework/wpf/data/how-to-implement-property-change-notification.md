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
ms.openlocfilehash: 4f9ff49a443577e119b0c1079abbe23bd7ede4c4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459742"
---
# <a name="how-to-implement-property-change-notification"></a>Postupy: Implementace oznámení změn vlastností
Pro podporu <xref:System.Windows.Data.BindingMode.OneWay> nebo <xref:System.Windows.Data.BindingMode.TwoWay> vazby, která umožňuje vlastnostem cíle vazby automaticky odrážet dynamické změny zdroje vazby (například pokud chcete, aby se podokno náhledu automaticky aktualizovalo, když uživatel upravuje formulář), vaše třída potřebuje Zadejte správné oznámení o změněných vlastnostech. Tento příklad ukazuje, jak vytvořit třídu, která implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Příklad  
 Chcete-li implementovat <xref:System.ComponentModel.INotifyPropertyChanged> je třeba deklarovat událost <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> a vytvořit metodu `OnPropertyChanged`. Potom pro každou vlastnost, pro kterou chcete změnit oznámení, zavoláte `OnPropertyChanged` vždy, když je vlastnost aktualizována.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Chcete-li zobrazit příklad, jak lze třídu `Person` použít pro podporu vazby <xref:System.Windows.Data.BindingMode.TwoWay>, přečtěte si téma [řízení při aktualizaci textu TextBox ve zdroji](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled zdrojů vazby](binding-sources-overview.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
