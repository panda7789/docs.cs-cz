---
title: "Omezení součásti Windows Forms Timer & č. 39; s vlastnost intervalu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 72af16b7dcb7709dd132a3748a454eda57acc168
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a><span data-ttu-id="4adb2-102">Omezení součásti Windows Forms Timer & č. 39; s vlastnost intervalu</span><span class="sxs-lookup"><span data-stu-id="4adb2-102">Limitations of the Windows Forms Timer Component&#39;s Interval Property</span></span>
<span data-ttu-id="4adb2-103">Windows Forms <xref:System.Windows.Forms.Timer> součást obsahuje <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, která určuje počet milisekund, po které se předají mezi jeden časovače událostí a další.</span><span class="sxs-lookup"><span data-stu-id="4adb2-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="4adb2-104">Pokud je zakázána, časovač nadále přijímat <xref:System.Windows.Forms.Timer.Tick> událost v přibližně stejné časové intervaly.</span><span class="sxs-lookup"><span data-stu-id="4adb2-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="4adb2-105">Tato součást je určená pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="4adb2-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="4adb2-106">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, najdete v části [Úvod do serverové časovače](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="4adb2-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/en-us/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="4adb2-107">Vlastnost intervalu</span><span class="sxs-lookup"><span data-stu-id="4adb2-107">The Interval Property</span></span>  
 <span data-ttu-id="4adb2-108"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost má několik omezení ke zvážení, když jsou programování <xref:System.Windows.Forms.Timer> součásti:</span><span class="sxs-lookup"><span data-stu-id="4adb2-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="4adb2-109">Aplikace nebo jiné aplikace upravuje velkou požadavky na systém – například dlouho smyčky, náročné výpočty, nebo jednotku, sítě nebo přístup k portu – aplikace nelze získat události časovače tak často, jako <xref:System.Windows.Forms.Timer.Interval%2A> určuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4adb2-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="4adb2-110">Interval není zaručena uplynout přesně na čas.</span><span class="sxs-lookup"><span data-stu-id="4adb2-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="4adb2-111">Aby byla zajištěna přesnost, časovač by měl Zkontrolujte systémové hodiny podle potřeby, nikoli zkuste ke sledování Akumulovaná čas interně.</span><span class="sxs-lookup"><span data-stu-id="4adb2-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="4adb2-112">Přesnost <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost je v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="4adb2-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="4adb2-113">Některé počítače zadejte ve vysokém rozlišení čítač, který má vyšší než počet milisekund rozlišení.</span><span class="sxs-lookup"><span data-stu-id="4adb2-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="4adb2-114">Dostupnost tyto čítače závisí na procesoru hardware počítače.</span><span class="sxs-lookup"><span data-stu-id="4adb2-114">The availability of such a counter depends on the processor hardware of your computer.</span></span> <span data-ttu-id="4adb2-115">Další informace najdete v článku 172338, "Jak k použití QueryPerformanceCounter do kódu v době," v databázi Microsoft Knowledge Base na http://support.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="4adb2-115">For more information, see article 172338, "How To Use QueryPerformanceCounter to Time Code," in the Microsoft Knowledge Base at http://support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adb2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4adb2-116">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="4adb2-117">Komponenta časovač</span><span class="sxs-lookup"><span data-stu-id="4adb2-117">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="4adb2-118">Přehled součásti časovač</span><span class="sxs-lookup"><span data-stu-id="4adb2-118">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
