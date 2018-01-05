---
title: "Postupy: příjem oznámení při hodiny, které & č. 39; s změny stavu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 396e2c51894ad5ed11f8953bceb1bd36899cfc62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a><span data-ttu-id="81c10-102">Postupy: příjem oznámení při hodiny, které & č. 39; s změny stavu</span><span class="sxs-lookup"><span data-stu-id="81c10-102">How to: Receive Notification When a Clock&#39;s State Changes</span></span>
<span data-ttu-id="81c10-103">Hodiny <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> dojde k události při jeho <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> stává neplatným, například když hodiny spuštění nebo zastavení.</span><span class="sxs-lookup"><span data-stu-id="81c10-103">A clock's <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> event occurs when its <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> becomes invalid, such as when the clock starts or stops.</span></span> <span data-ttu-id="81c10-104">Můžete zaregistrovat pro tuto událost s přímo pomocí <xref:System.Windows.Media.Animation.Clock>, nebo můžete zaregistrovat pomocí <xref:System.Windows.Media.Animation.Timeline>.</span><span class="sxs-lookup"><span data-stu-id="81c10-104">You can register for this event with directly using a <xref:System.Windows.Media.Animation.Clock>, or you can register using a <xref:System.Windows.Media.Animation.Timeline>.</span></span>  
  
 <span data-ttu-id="81c10-105">V následujícím příkladu <xref:System.Windows.Media.Animation.Storyboard> a dvě <xref:System.Windows.Media.Animation.DoubleAnimation> objekty se používají k animace šířku dvou tvaru.</span><span class="sxs-lookup"><span data-stu-id="81c10-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> and two <xref:System.Windows.Media.Animation.DoubleAnimation> objects are used to animate the width of two rectangles.</span></span> <span data-ttu-id="81c10-106"><xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> Událostí se používá k naslouchání hodiny změny stavu.</span><span class="sxs-lookup"><span data-stu-id="81c10-106">The <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event is used to listen for clock state changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81c10-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="81c10-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 <span data-ttu-id="81c10-108">Následující obrázek ukazuje různé stavy animací zadejte jako nadřazené časové osy (*Storyboard*) postupuje.</span><span class="sxs-lookup"><span data-stu-id="81c10-108">The following illustration shows the different states the animations enter as the parent timeline (*Storyboard*) progresses.</span></span>  
  
 <span data-ttu-id="81c10-109">![Clock stavy pro scénář se dvěma animací](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span><span class="sxs-lookup"><span data-stu-id="81c10-109">![Clock states for a Storyboard with two animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span></span>  
  
 <span data-ttu-id="81c10-110">Následující tabulka uvádí dobu, kdy *Animation1*na <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> aktivuje událost:</span><span class="sxs-lookup"><span data-stu-id="81c10-110">The following table shows the times at which *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="81c10-111">Doba (v sekundách)</span><span class="sxs-lookup"><span data-stu-id="81c10-111">Time (Seconds)</span></span>|<span data-ttu-id="81c10-112">1</span><span class="sxs-lookup"><span data-stu-id="81c10-112">1</span></span>|<span data-ttu-id="81c10-113">10</span><span class="sxs-lookup"><span data-stu-id="81c10-113">10</span></span>|<span data-ttu-id="81c10-114">19</span><span class="sxs-lookup"><span data-stu-id="81c10-114">19</span></span>|<span data-ttu-id="81c10-115">21</span><span class="sxs-lookup"><span data-stu-id="81c10-115">21</span></span>|<span data-ttu-id="81c10-116">30</span><span class="sxs-lookup"><span data-stu-id="81c10-116">30</span></span>|<span data-ttu-id="81c10-117">39</span><span class="sxs-lookup"><span data-stu-id="81c10-117">39</span></span>|  
|<span data-ttu-id="81c10-118">Stav</span><span class="sxs-lookup"><span data-stu-id="81c10-118">State</span></span>|<span data-ttu-id="81c10-119">Aktivní</span><span class="sxs-lookup"><span data-stu-id="81c10-119">Active</span></span>|<span data-ttu-id="81c10-120">Aktivní</span><span class="sxs-lookup"><span data-stu-id="81c10-120">Active</span></span>|<span data-ttu-id="81c10-121">Byla zastavena</span><span class="sxs-lookup"><span data-stu-id="81c10-121">Stopped</span></span>|<span data-ttu-id="81c10-122">Aktivní</span><span class="sxs-lookup"><span data-stu-id="81c10-122">Active</span></span>|<span data-ttu-id="81c10-123">Aktivní</span><span class="sxs-lookup"><span data-stu-id="81c10-123">Active</span></span>|<span data-ttu-id="81c10-124">Byla zastavena</span><span class="sxs-lookup"><span data-stu-id="81c10-124">Stopped</span></span>|  
  
 <span data-ttu-id="81c10-125">Následující tabulka uvádí dobu, kdy *Animation2*na <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> aktivuje událost:</span><span class="sxs-lookup"><span data-stu-id="81c10-125">The following table shows the times at which *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="81c10-126">Doba (v sekundách)</span><span class="sxs-lookup"><span data-stu-id="81c10-126">Time (Seconds)</span></span>|<span data-ttu-id="81c10-127">1</span><span class="sxs-lookup"><span data-stu-id="81c10-127">1</span></span>|<span data-ttu-id="81c10-128">9</span><span class="sxs-lookup"><span data-stu-id="81c10-128">9</span></span>|<span data-ttu-id="81c10-129">11</span><span class="sxs-lookup"><span data-stu-id="81c10-129">11</span></span>|<span data-ttu-id="81c10-130">19</span><span class="sxs-lookup"><span data-stu-id="81c10-130">19</span></span>|<span data-ttu-id="81c10-131">21</span><span class="sxs-lookup"><span data-stu-id="81c10-131">21</span></span>|<span data-ttu-id="81c10-132">29</span><span class="sxs-lookup"><span data-stu-id="81c10-132">29</span></span>|<span data-ttu-id="81c10-133">31</span><span class="sxs-lookup"><span data-stu-id="81c10-133">31</span></span>|<span data-ttu-id="81c10-134">39</span><span class="sxs-lookup"><span data-stu-id="81c10-134">39</span></span>|  
|<span data-ttu-id="81c10-135">Stav</span><span class="sxs-lookup"><span data-stu-id="81c10-135">State</span></span>|<span data-ttu-id="81c10-136">Aktivní</span><span class="sxs-lookup"><span data-stu-id="81c10-136">Active</span></span>|<span data-ttu-id="81c10-137">Naplnění</span><span class="sxs-lookup"><span data-stu-id="81c10-137">Filling</span></span>|<span data-ttu-id="81c10-138">Aktivní</span><span class="sxs-lookup"><span data-stu-id="81c10-138">Active</span></span>|<span data-ttu-id="81c10-139">Byla zastavena</span><span class="sxs-lookup"><span data-stu-id="81c10-139">Stopped</span></span>|<span data-ttu-id="81c10-140">Aktivní</span><span class="sxs-lookup"><span data-stu-id="81c10-140">Active</span></span>|<span data-ttu-id="81c10-141">Naplnění</span><span class="sxs-lookup"><span data-stu-id="81c10-141">Filling</span></span>|<span data-ttu-id="81c10-142">Aktivní</span><span class="sxs-lookup"><span data-stu-id="81c10-142">Active</span></span>|<span data-ttu-id="81c10-143">Byla zastavena</span><span class="sxs-lookup"><span data-stu-id="81c10-143">Stopped</span></span>|  
  
 <span data-ttu-id="81c10-144">Všimněte si, že *Animation1*na <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> událost aktivuje na 10 sekund, i když zůstane stav <xref:System.Windows.Media.Animation.ClockState.Active>.</span><span class="sxs-lookup"><span data-stu-id="81c10-144">Notice that *Animation1*'s  <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires at 10 seconds, even though its state remains <xref:System.Windows.Media.Animation.ClockState.Active>.</span></span> <span data-ttu-id="81c10-145">Důvodem je, že došlo ke změně jeho stavu na 10 sekund, ale změnit z <xref:System.Windows.Media.Animation.ClockState.Active> k <xref:System.Windows.Media.Animation.ClockState.Filling> a pak zpátky na <xref:System.Windows.Media.Animation.ClockState.Active> ve stejné značek.</span><span class="sxs-lookup"><span data-stu-id="81c10-145">That's because its state changed at 10 seconds, but it changed from <xref:System.Windows.Media.Animation.ClockState.Active> to <xref:System.Windows.Media.Animation.ClockState.Filling> and then back to <xref:System.Windows.Media.Animation.ClockState.Active> in the same tick.</span></span>
