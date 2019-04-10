---
title: 'Postupy: Nastavení oznámení pro aktualizace vazeb'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 4185198312ed98f9aaa1388626600d9f21abae55
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213959"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Postupy: Nastavení oznámení pro aktualizace vazeb
Tento příklad ukazuje, jak nastavit upozornění, až se aktualizovala cíl vazby (cíl) nebo vlastnost source (zdroj) vazby vazby.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pokaždé, když vyvolává událost aktualizace dat, u, vazba zdroj nebo cíl je aktualizovaná. Tato událost se interně používá k informování [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , který by měl aktualizovat protože vázaných dat se změnila. Všimněte si, že pro tyto události pro práci a také pro jednosměrné nebo obousměrné vazby fungovalo správně, je nutné implementovat třídy dat pomocí <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [implementace oznámení změn vlastností](how-to-implement-property-change-notification.md).  
  
 Nastavte <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> nebo <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> vlastnost (nebo obojí) `true` ve vazbě. Obslužná rutina, kterou zadáte pro naslouchání pro tuto událost musí být připojené přímo na prvek, ve které chcete být informováni o změny, nebo kontextu dat, pokud budete chtít mějte na paměti, že něco v kontextu změnilo.  
  
 Tady je příklad, který ukazuje, jak nastavit pro oznámení, pokud vlastnost target byla aktualizována.  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Pak můžete přiřadit obslužnou rutinu podle EventHandler\<T > delegovat, *OnTargetUpdated* v tomto příkladu, pro zpracování události:  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Parametry události je možné zjistit podrobné informace o vlastnosti, která se změnila (jako je například typ nebo konkrétní elementu, jestliže stejnou obslužnou rutinu je připojen k více než jeden prvek), což může být užitečné, pokud více vázané vlastnosti na jeden element.  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](data-binding-overview.md)
- [– postupy](data-binding-how-to-topics.md)
