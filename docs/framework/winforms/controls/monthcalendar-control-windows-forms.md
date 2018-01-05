---
title: "MonthCalendar – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calendar controls
- MonthCalendar control [Windows Forms]
- dates [Windows Forms], controls
- calendars
ms.assetid: 051c6518-e0ca-426b-855c-f9bf70972970
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2ed5ccd46a6563ced2cf5946304a36d0c204a00a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="monthcalendar-control-windows-forms"></a><span data-ttu-id="00eff-102">MonthCalendar – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="00eff-102">MonthCalendar Control (Windows Forms)</span></span>
<span data-ttu-id="00eff-103">Windows Forms `MonthCalendar` řízení uvede intuitivní grafické rozhraní pro uživatele k zobrazení a nastavit informace o datu.</span><span class="sxs-lookup"><span data-stu-id="00eff-103">The Windows Forms `MonthCalendar` control presents an intuitive graphical interface for users to view and set date information.</span></span> <span data-ttu-id="00eff-104">Ovládací prvek zobrazí mřížku obsahující číslem dny v měsíci, uspořádané ve sloupcích pod dny v týdnu.</span><span class="sxs-lookup"><span data-stu-id="00eff-104">The control displays a grid containing the numbered days of the month, arranged in columns underneath the days of the week.</span></span> <span data-ttu-id="00eff-105">Kliknutím na tlačítko se šipkou na obou stranách titulek měsíc můžete vybrat jiný měsíc.</span><span class="sxs-lookup"><span data-stu-id="00eff-105">You can select a different month by clicking the arrow buttons on either side of the month caption.</span></span> <span data-ttu-id="00eff-106">Na rozdíl od podobné <xref:System.Windows.Forms.DateTimePicker> ovládací prvek, můžete vybrat rozsah kalendářních dat pro tento ovládací prvek; však <xref:System.Windows.Forms.DateTimePicker> řízení umožňuje nastavit čas, a také data.</span><span class="sxs-lookup"><span data-stu-id="00eff-106">Unlike the similar <xref:System.Windows.Forms.DateTimePicker> control, you can select a range of dates with this control; however, the <xref:System.Windows.Forms.DateTimePicker> control allows you to set times as well as dates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="00eff-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="00eff-107">In This Section</span></span>  
 [<span data-ttu-id="00eff-108">Přehled ovládacího prvku MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="00eff-108">MonthCalendar Control Overview</span></span>](../../../../docs/framework/winforms/controls/monthcalendar-control-overview-windows-forms.md)  
 <span data-ttu-id="00eff-109">Představuje obecné koncepty `MonthCalendar` řízení, které umožňuje uživatelům zobrazit a nastavit informace o datu pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="00eff-109">Introduces the general concepts of the `MonthCalendar` control, which allows users to view and set date information for an application.</span></span>  
  
 [<span data-ttu-id="00eff-110">Postupy: Změna vzhledu ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="00eff-110">How to: Change the Windows Forms MonthCalendar Control's Appearance</span></span>](../../../../docs/framework/winforms/controls/how-to-change-monthcalendar-control-appearance.md)  
 <span data-ttu-id="00eff-111">Popisuje, jak přizpůsobit vzhled `MonthCalendar` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="00eff-111">Describes how to customize the appearance of the `MonthCalendar` control.</span></span>  
  
 [<span data-ttu-id="00eff-112">Postupy: Zobrazení více než jednoho měsíce v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="00eff-112">How to: Display More than One Month in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-more-than-one-month-wf-monthcalendar-control.md)  
 <span data-ttu-id="00eff-113">Popisuje postup konfigurace `MonthCalendar` ovládací prvek zobrazí několik měsíců současně.</span><span class="sxs-lookup"><span data-stu-id="00eff-113">Describes how to configure the `MonthCalendar` control to display several months simultaneously.</span></span>  
  
 [<span data-ttu-id="00eff-114">Postupy: Tučné zobrazení konkrétních dnů pomocí ovládacího prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="00eff-114">How to: Display Specific Days in Bold with the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/display-specific-days-in-bold-with-wf-monthcalendar-control.md)  
 <span data-ttu-id="00eff-115">Vysvětluje, jak nastavit určitá data, která se zobrazí tučně.</span><span class="sxs-lookup"><span data-stu-id="00eff-115">Explains how to set certain dates to appear bold.</span></span>  
  
 [<span data-ttu-id="00eff-116">Postupy: Výběr rozsahu kalendářních dat v ovládacím prvku Windows Forms MonthCalendar</span><span class="sxs-lookup"><span data-stu-id="00eff-116">How to: Select a Range of Dates in the Windows Forms MonthCalendar Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-a-range-of-dates-in-the-windows-forms-monthcalendar-control.md)  
 <span data-ttu-id="00eff-117">Vysvětluje, jak programově vybrat rozsah kalendářních dat z `MonthCalendar` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="00eff-117">Explains how to programmatically select a range of dates from the `MonthCalendar` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="00eff-118">Odkaz</span><span class="sxs-lookup"><span data-stu-id="00eff-118">Reference</span></span>  
 <xref:System.Windows.Forms.MonthCalendar>  
 <span data-ttu-id="00eff-119">Poskytuje referenční informace o třídě a její členy.</span><span class="sxs-lookup"><span data-stu-id="00eff-119">Provides reference information on the class and its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="00eff-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="00eff-120">Related Sections</span></span>  
 [<span data-ttu-id="00eff-121">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="00eff-121">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="00eff-122">Poskytuje úplný seznam Windows Forms – ovládací prvky, odkazy na informace o jejich používání.</span><span class="sxs-lookup"><span data-stu-id="00eff-122">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>  
  
 [<span data-ttu-id="00eff-123">Ovládací prvek DateTimePicker</span><span class="sxs-lookup"><span data-stu-id="00eff-123">DateTimePicker Control</span></span>](../../../../docs/framework/winforms/controls/datetimepicker-control-windows-forms.md)  
 <span data-ttu-id="00eff-124">Popisuje ovládacího prvku podobná <xref:System.Windows.Forms.MonthCalendar>, i když <xref:System.Windows.Forms.DateTimePicker> řízení také můžete vybrat čas a neumožňuje vybrat rozsah kalendářních dat.</span><span class="sxs-lookup"><span data-stu-id="00eff-124">Describes a control similar to <xref:System.Windows.Forms.MonthCalendar>, although the <xref:System.Windows.Forms.DateTimePicker> control also allows you to select a time and does not allow you to select a range of dates.</span></span>
