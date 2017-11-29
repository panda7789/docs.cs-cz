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
ms.openlocfilehash: cd5c7c796ee9d51a216368de3f3b04c10a5a3acd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="datepicker"></a><span data-ttu-id="2535a-102">DatePicker</span><span class="sxs-lookup"><span data-stu-id="2535a-102">DatePicker</span></span>
<span data-ttu-id="2535a-103"><xref:System.Windows.Controls.DatePicker> Řízení umožňuje uživateli zadáním buď ho do textového pole, nebo pomocí rozevíracího seznamu vyberte datum <xref:System.Windows.Controls.Calendar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2535a-103">The <xref:System.Windows.Controls.DatePicker> control allows the user to select a date by either typing it into a text field or by using a drop-down <xref:System.Windows.Controls.Calendar> control.</span></span>  
  
 <span data-ttu-id="2535a-104">Následující obrázek znázorňuje <xref:System.Windows.Controls.DatePicker>.</span><span class="sxs-lookup"><span data-stu-id="2535a-104">The following illustration shows a <xref:System.Windows.Controls.DatePicker>.</span></span>  
  
 <span data-ttu-id="2535a-105">![Ovládací prvek DatePicker řízení](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span><span class="sxs-lookup"><span data-stu-id="2535a-105">![DatePicker control](../../../../docs/framework/wpf/controls/media/ndp-datepicker.png "NDP_DatePicker")</span></span>  
<span data-ttu-id="2535a-106">Ovládací prvek DatePicker ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2535a-106">DatePicker Control</span></span>  
  
 <span data-ttu-id="2535a-107">Řadu <xref:System.Windows.Controls.DatePicker> vlastností ovládacího prvku jsou pro správu jeho vestavěné <xref:System.Windows.Controls.Calendar>a funkce stejně jako na ekvivalentní vlastnost v <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="2535a-107">Many of a <xref:System.Windows.Controls.DatePicker> control's properties are for managing its built-in <xref:System.Windows.Controls.Calendar>, and function identically to the equivalent property in <xref:System.Windows.Controls.Calendar>.</span></span> <span data-ttu-id="2535a-108">Konkrétně <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, a <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> vlastnosti fungovat stejně jako na jejich <xref:System.Windows.Controls.Calendar> svými protějšky.</span><span class="sxs-lookup"><span data-stu-id="2535a-108">In particular, the <xref:System.Windows.Controls.DatePicker.IsTodayHighlighted%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.FirstDayOfWeek%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.BlackoutDates%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateStart%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDateEnd%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.DatePicker.DisplayDate%2A?displayProperty=nameWithType>, and <xref:System.Windows.Controls.DatePicker.SelectedDate%2A?displayProperty=nameWithType> properties function identically to their <xref:System.Windows.Controls.Calendar> counterparts.</span></span> <span data-ttu-id="2535a-109">Další informace naleznete v tématu <xref:System.Windows.Controls.Calendar>.</span><span class="sxs-lookup"><span data-stu-id="2535a-109">For more information, see <xref:System.Windows.Controls.Calendar>.</span></span>  
  
 <span data-ttu-id="2535a-110">Uživatelé mohou zadat datum přímo do textové pole, která nastaví <xref:System.Windows.Controls.DatePicker.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2535a-110">Users can type a date directly into a text field, which sets the <xref:System.Windows.Controls.DatePicker.Text%2A> property.</span></span> <span data-ttu-id="2535a-111">Pokud <xref:System.Windows.Controls.DatePicker> zadaný řetězec nelze převést na platné datum <xref:System.Windows.Controls.DatePicker.DateValidationError> událostí, bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="2535a-111">If the <xref:System.Windows.Controls.DatePicker> cannot convert the entered string to a valid date, the <xref:System.Windows.Controls.DatePicker.DateValidationError> event will be raised.</span></span> <span data-ttu-id="2535a-112">Ve výchozím nastavení, to způsobí výjimku, ale obslužné rutiny události pro <xref:System.Windows.Controls.DatePicker.DateValidationError> můžete nastavit <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> vlastnost `false` a zabránit výjimku vyvolána.</span><span class="sxs-lookup"><span data-stu-id="2535a-112">By default, this causes an exception, but an event handler for <xref:System.Windows.Controls.DatePicker.DateValidationError> can set the <xref:System.Windows.Controls.DatePickerDateValidationErrorEventArgs.ThrowException%2A> property to `false` and prevent an exception from being raised.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2535a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="2535a-113">See Also</span></span>  
 [<span data-ttu-id="2535a-114">Ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="2535a-114">Controls</span></span>](../../../../docs/framework/wpf/controls/index.md)  
 [<span data-ttu-id="2535a-115">Stylů a ukázka</span><span class="sxs-lookup"><span data-stu-id="2535a-115">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
