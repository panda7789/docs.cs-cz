---
title: "Postupy: Nastavení oznámení pro aktualizace připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a07337e99e985bfbc0a5dbc5f2d231ee36cf1422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Postupy: Nastavení oznámení pro aktualizace připojení
Tento příklad ukazuje, jak nastavit tak, aby být upozorněni, když byla aktualizována vazby cíle (target) nebo vlastnost vazby zdroj (zdroj) vazby.  
  
## <a name="example"></a>Příklad  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]pokaždé, když vyvolá událost aktualizace dat, u, aby byla aktualizována vazby zdroje nebo cíle. Tato událost se interně používá k informování [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] který by měl aktualizovat protože vázaných dat došlo ke změně. Poznámka: pro tyto události pro práci a také pro jednosměrné, nebo pomocí obousměrné vazby fungovalo správně, budete muset implementovat třídu dat pomocí <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [oznámení o změně vlastnost implementace](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 Nastavte <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> nebo <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> vlastnost (nebo obě) `true` vazba. Obslužná rutina, kterou zadáte pro naslouchání pro tuto událost musí být připojené přímo k elementu, kde chcete být informováni o změny, nebo kontextu dat, pokud chcete vědět, že se změnila nic v kontextu.  
  
 Tady je příklad, který ukazuje, jak nastavit pro oznámení, pokud vlastnost target byla aktualizována.  
  
 [!code-xaml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Pak můžete přiřadit obslužnou rutinu podle obslužná rutina události\<T > delegovat, *OnTargetUpdated* v tomto příkladu se zpracovat událost:  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Parametry události lze zjistit podrobnosti o vlastnosti, který změnil (například typ nebo konkrétní elementu, pokud obslužná rutina stejné je připojena k více než jeden element), což může být užitečné, pokud nejsou k dispozici více vázané vlastnosti na jeden element.  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
