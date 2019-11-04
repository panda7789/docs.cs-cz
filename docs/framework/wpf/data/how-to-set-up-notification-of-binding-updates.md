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
# <a name="how-to-set-up-notification-of-binding-updates"></a><span data-ttu-id="f1e0c-102">Postupy: Nastavení oznámení pro aktualizace připojení</span><span class="sxs-lookup"><span data-stu-id="f1e0c-102">How to: Set Up Notification of Binding Updates</span></span>
<span data-ttu-id="f1e0c-103">Tento příklad ukazuje, jak nastavit, aby byly oznamovány při aktualizaci cíle vazby (cíle) nebo vlastnosti zdroje vazby (zdroj) vazby.</span><span class="sxs-lookup"><span data-stu-id="f1e0c-103">This example shows how to set up to be notified when the binding target (target) or the binding source (source) property of a binding has been updated.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1e0c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1e0c-104">Example</span></span>  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="f1e0c-105">vyvolá událost aktualizace dat pokaždé, když se aktualizuje zdroj nebo cíl vazby.</span><span class="sxs-lookup"><span data-stu-id="f1e0c-105">raises a data update event each time that the binding source or target has been updated.</span></span> <span data-ttu-id="f1e0c-106">Interně se tato událost používá k informování [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], že by se měla aktualizovat, protože se změnila vázaná data.</span><span class="sxs-lookup"><span data-stu-id="f1e0c-106">Internally, this event is used to inform the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] that it should update, because the bound data has changed.</span></span> <span data-ttu-id="f1e0c-107">Všimněte si, že aby tyto události fungovaly, a také způsob, jak správně pracovat, je nutné implementovat svou datovou třídu pomocí rozhraní <xref:System.ComponentModel.INotifyPropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="f1e0c-107">Note that for these events to work, and also for one-way or two-way binding to work properly, you need to implement your data class using the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="f1e0c-108">Další informace najdete v tématu [implementace oznámení změny vlastností](how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="f1e0c-108">For more information, see [Implement Property Change Notification](how-to-implement-property-change-notification.md).</span></span>  
  
 <span data-ttu-id="f1e0c-109">Nastavte vlastnost <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> nebo <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> (nebo oboje) na `true` ve vazbě.</span><span class="sxs-lookup"><span data-stu-id="f1e0c-109">Set the <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> or <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> property (or both) to `true` in the binding.</span></span> <span data-ttu-id="f1e0c-110">Obslužná rutina, kterou zadáte k naslouchání této události, musí být připojena přímo k prvku, kde chcete mít informace o změnách, nebo k celkovému kontextu dat, pokud chcete mít na paměti, že se něco v kontextu změnilo.</span><span class="sxs-lookup"><span data-stu-id="f1e0c-110">The handler you provide to listen for this event must be attached directly to the element where you want to be informed of changes, or to the overall data context if you want to be aware that anything in the context has changed.</span></span>  
  
 <span data-ttu-id="f1e0c-111">Tady je příklad, který ukazuje, jak nastavit pro oznámení v případě, že byla aktualizována cílová vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f1e0c-111">Here is an example that shows how to set up for notification when a target property has been updated.</span></span>  
  
 [!code-xaml[DirectionalBinding#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="f1e0c-112">Pak můžete přiřadit obslužnou rutinu na základě delegáta > EventHandler\<T, který je v tomto příkladu *OnTargetUpdated* pro zpracování události:</span><span class="sxs-lookup"><span data-stu-id="f1e0c-112">You can then assign a handler based on the EventHandler\<T> delegate, *OnTargetUpdated* in this example, to handle the event:</span></span>  
  
 [!code-csharp[DirectionalBinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](~/samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 <span data-ttu-id="f1e0c-113">Parametry události lze použít k určení podrobností o vlastnosti, která se změnila (například typ nebo konkrétní element, pokud je stejná obslužná rutina připojena k více než jednomu prvku), což může být užitečné, pokud existuje více vlastností vázaných prvků na jednom prvku.</span><span class="sxs-lookup"><span data-stu-id="f1e0c-113">Parameters of the event can be used to determine details about the property that changed (such as the type or the specific element if the same handler is attached to more than one element), which can be useful if there are multiple bound properties on a single element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e0c-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1e0c-114">See also</span></span>

- [<span data-ttu-id="f1e0c-115">Přehled datových vazeb</span><span class="sxs-lookup"><span data-stu-id="f1e0c-115">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="f1e0c-116">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="f1e0c-116">How-to Topics</span></span>](data-binding-how-to-topics.md)
