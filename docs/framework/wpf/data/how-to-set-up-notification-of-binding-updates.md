---
title: 'Postupy: Nastavení oznámení pro aktualizace připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: dfa0f9264247f7585c1743e40fd980906556efd0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454950"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Postupy: Nastavení oznámení pro aktualizace připojení
Tento příklad ukazuje, jak nastavit, aby byly oznamovány při aktualizaci cíle vazby (cíle) nebo vlastnosti zdroje vazby (zdroj) vazby.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vyvolá událost aktualizace dat pokaždé, když se aktualizuje zdroj nebo cíl vazby. Interně se tato událost používá k informování [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], že by se měla aktualizovat, protože se změnila vázaná data. Všimněte si, že aby tyto události fungovaly, a také způsob, jak správně pracovat, je nutné implementovat svou datovou třídu pomocí rozhraní <xref:System.ComponentModel.INotifyPropertyChanged>. Další informace najdete v tématu [implementace oznámení změny vlastností](how-to-implement-property-change-notification.md).  
  
 Nastavte vlastnost <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> nebo <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> (nebo oboje) na `true` ve vazbě. Obslužná rutina, kterou zadáte k naslouchání této události, musí být připojena přímo k prvku, kde chcete mít informace o změnách, nebo k celkovému kontextu dat, pokud chcete mít na paměti, že se něco v kontextu změnilo.  
  
 Tady je příklad, který ukazuje, jak nastavit pro oznámení v případě, že byla aktualizována cílová vlastnost.  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Pak můžete přiřadit obslužnou rutinu na základě delegáta > EventHandler\<T, který je v tomto příkladu *OnTargetUpdated* pro zpracování události:  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Parametry události lze použít k určení podrobností o vlastnosti, která se změnila (například typ nebo konkrétní element, pokud je stejná obslužná rutina připojena k více než jednomu prvku), což může být užitečné, pokud existuje více vlastností vázaných prvků na jednom prvku.  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
