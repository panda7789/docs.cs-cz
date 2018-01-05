---
title: DatePicker
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], DatePicker
- DatePicker control [WPF]
ms.assetid: 619765c8-8d25-4315-aec2-79aea08fed9f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd2a1755ae076369661b2c9a7a2b744961cdb129
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datepicker"></a><span data-ttu-id="abdc9-102">DatePicker</span><span class="sxs-lookup"><span data-stu-id="abdc9-102">DatePicker</span></span>
<span data-ttu-id="abdc9-103"><xref:System.Windows.Controls.DatePicker> Řízení umožňuje uživateli zadáním buď ho do textového pole, nebo pomocí rozevíracího seznamu vyberte datum <xref:System.Windows.Controls.Calendar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="abdc9-103">The <xref:System.Windows.Controls.DatePicker> control allows the user to select a date by either typing it into a text field or by using a drop-down <xref:System.Windows.Controls.Calendar> control.</span></span>  
  
 <span data-ttu-id="abdc9-104">Následující obrázek znázorňuje <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="abdc9-104">The following illustration shows a <xref:System.Windows.Controls.DatePicker>.</span></span>  
  
 <span data-ttu-id="abdc9-105">![Ovládací prvek DatePicker řízení](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span><span class="sxs-lookup"><span data-stu-id="abdc9-105">![DatePicker control](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span></span>  
<span data-ttu-id="abdc9-106">Ovládací prvek DatePicker ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="abdc9-106">DatePicker Control</span></span>  
  
 <span data-ttu-id="abdc9-107">Řadu <xref:System.Windows.Controls.DatePicker> vlastností ovládacího prvku jsou pro správu jeho vestavěné <xref:System.Windows.Controls.Calendar>a funkce stejně jako na ekvivalentní vlastnost v <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="abdc9-107">Many of a <xref:System.Windows.Controls.DatePicker> control's properties are for managing its built-in <xref:System.Windows.Controls.Calendar>, and function identically to the equivalent property in <xref:System.Windows.Controls.Calendar>.</span></span> <span data-ttu-id="abdc9-108">Konkrétně <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, a <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> vlastnosti fungovat stejně jako na jejich <xref:System.Windows.Controls.Calendar> svými protějšky.</span><span class="sxs-lookup"><span data-stu-id="abdc9-108">In particular, the <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, and <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> properties function identically to their <xref:System.Windows.Controls.Calendar> counterparts.</span></span> <span data-ttu-id="abdc9-109">Další informace naleznete v tématu <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="abdc9-109">For more information, see <xref:System.Windows.Controls.Calendar>.</span></span>  
  
 <span data-ttu-id="abdc9-110">Uživatelé mohou zadat datum přímo do textové pole, která nastaví <xref:System.Windows.Controls.DatePicker.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="abdc9-110">Users can type a date directly into a text field, which sets the <xref:System.Windows.Controls.DatePicker.Text%2A> property.</span></span> <span data-ttu-id="abdc9-111">Pokud <xref:System.Windows.Controls.DatePicker> zadaný řetězec nelze převést na platné datum <xref:System.Windows.Controls.DatePicker.DateValidationError> událostí, bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="abdc9-111">If the <xref:System.Windows.Controls.DatePicker> cannot convert the entered string to a valid date, the <xref:System.Windows.Controls.DatePicker.DateValidationError> event will be raised.</span></span> <span data-ttu-id="abdc9-112">Ve výchozím nastavení, to způsobí výjimku, ale obslužné rutiny události pro <xref:System.Windows.Controls.DatePicker.DateValidationError> můžete nastavit <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> vlastnost `false` a zabránit výjimku vyvolána.</span><span class="sxs-lookup"><span data-stu-id="abdc9-112">By default, this causes an exception, but an event handler for <xref:System.Windows.Controls.DatePicker.DateValidationError> can set the <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> property to `false` and prevent an exception from being raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abdc9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="abdc9-113">See Also</span></span>  
 [<span data-ttu-id="abdc9-114">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="abdc9-114">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="abdc9-115">Styly a šablony</span><span class="sxs-lookup"><span data-stu-id="abdc9-115">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
