---
title: 'Postupy: Nastavení oznámení pro aktualizace připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 896ce103361590dceecccf8534fd330aabe18086
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555838"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="2005d-102">Postupy: Nastavení oznámení pro aktualizace připojení</span><span class="sxs-lookup"><span data-stu-id="2005d-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="2005d-103">Tento příklad ukazuje, jak nastavit tak, aby být upozorněni, když byla aktualizována vazby cíle (target) nebo vlastnost vazby zdroj (zdroj) vazby.</span><span class="sxs-lookup"><span data-stu-id="2005d-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2005d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="2005d-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="2005d-105"> pokaždé, když vyvolá událost aktualizace dat, u, aby byla aktualizována vazby zdroje nebo cíle.</span><span class="sxs-lookup"><span data-stu-id="2005d-105"> raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="2005d-106">Tato událost se interně používá k informování [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] který by měl aktualizovat protože vázaných dat došlo ke změně.</span><span class="sxs-lookup"><span data-stu-id="2005d-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="2005d-107">Poznámka: pro tyto události pro práci a také pro jednosměrné, nebo pomocí obousměrné vazby fungovalo správně, budete muset implementovat třídu dat pomocí <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2005d-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="2005d-108">Další informace najdete v tématu [oznámení o změně vlastnost implementace](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="2005d-108">For more information, see [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="2005d-109">Nastavte <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> nebo <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> vlastnost (nebo obě) `true` vazba.</span><span class="sxs-lookup"><span data-stu-id="2005d-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="2005d-110">Obslužná rutina, kterou zadáte pro naslouchání pro tuto událost musí být připojené přímo k elementu, kde chcete být informováni o změny, nebo kontextu dat, pokud chcete vědět, že se změnila nic v kontextu.</span><span class="sxs-lookup"><span data-stu-id="2005d-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="2005d-111">Tady je příklad, který ukazuje, jak nastavit pro oznámení, pokud vlastnost target byla aktualizována.</span><span class="sxs-lookup"><span data-stu-id="2005d-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="2005d-112">Pak můžete přiřadit obslužnou rutinu podle obslužná rutina události\<T > delegovat, *OnTargetUpdated* v tomto příkladu se zpracovat událost:</span><span class="sxs-lookup"><span data-stu-id="2005d-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="2005d-113">Parametry události lze zjistit podrobnosti o vlastnosti, který změnil (například typ nebo konkrétní elementu, pokud obslužná rutina stejné je připojena k více než jeden element), což může být užitečné, pokud nejsou k dispozici více vázané vlastnosti na jeden element.</span><span class="sxs-lookup"><span data-stu-id="2005d-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2005d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2005d-114">See Also</span></span>  
 [<span data-ttu-id="2005d-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="2005d-115">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="2005d-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="2005d-116">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
