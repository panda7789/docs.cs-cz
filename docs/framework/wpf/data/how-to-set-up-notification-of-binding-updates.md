---
title: 'Postupy: Nastavení oznámení pro aktualizace vazeb'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 4185198312ed98f9aaa1388626600d9f21abae55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213959"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="a470a-102">Postupy: Nastavení oznámení pro aktualizace vazeb</span><span class="sxs-lookup"><span data-stu-id="a470a-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="a470a-103">Tento příklad ukazuje, jak nastavit upozornění, až se aktualizovala cíl vazby (cíl) nebo vlastnost source (zdroj) vazby vazby.</span><span class="sxs-lookup"><span data-stu-id="a470a-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a470a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a470a-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="a470a-105">pokaždé, když vyvolává událost aktualizace dat, u, vazba zdroj nebo cíl je aktualizovaná.</span><span class="sxs-lookup"><span data-stu-id="a470a-105">raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="a470a-106">Tato událost se interně používá k informování [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , který by měl aktualizovat protože vázaných dat se změnila.</span><span class="sxs-lookup"><span data-stu-id="a470a-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="a470a-107">Všimněte si, že pro tyto události pro práci a také pro jednosměrné nebo obousměrné vazby fungovalo správně, je nutné implementovat třídy dat pomocí <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a470a-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="a470a-108">Další informace najdete v tématu [implementace oznámení změn vlastností](how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="a470a-108">For more information, see [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="a470a-109">Nastavte <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> nebo <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> vlastnost (nebo obojí) `true` ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="a470a-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="a470a-110">Obslužná rutina, kterou zadáte pro naslouchání pro tuto událost musí být připojené přímo na prvek, ve které chcete být informováni o změny, nebo kontextu dat, pokud budete chtít mějte na paměti, že něco v kontextu změnilo.</span><span class="sxs-lookup"><span data-stu-id="a470a-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="a470a-111">Tady je příklad, který ukazuje, jak nastavit pro oznámení, pokud vlastnost target byla aktualizována.</span><span class="sxs-lookup"><span data-stu-id="a470a-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="a470a-112">Pak můžete přiřadit obslužnou rutinu podle EventHandler\<T > delegovat, *OnTargetUpdated* v tomto příkladu, pro zpracování události:</span><span class="sxs-lookup"><span data-stu-id="a470a-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="a470a-113">Parametry události je možné zjistit podrobné informace o vlastnosti, která se změnila (jako je například typ nebo konkrétní elementu, jestliže stejnou obslužnou rutinu je připojen k více než jeden prvek), což může být užitečné, pokud více vázané vlastnosti na jeden element.</span><span class="sxs-lookup"><span data-stu-id="a470a-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a470a-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a470a-114">See also</span></span>

- [<span data-ttu-id="a470a-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="a470a-115">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="a470a-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="a470a-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
