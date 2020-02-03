---
title: Omezení vlastnosti intervalu komponenty časovače
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745229"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="8f3b5-102">Omezení vlastnosti intervalu součásti Windows Forms Timer</span><span class="sxs-lookup"><span data-stu-id="8f3b5-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="8f3b5-103">Komponenta model Windows Forms <xref:System.Windows.Forms.Timer> má vlastnost <xref:System.Windows.Forms.Timer.Interval%2A>, která určuje počet milisekund, které budou uplynout mezi jednou událostí časovače a další.</span><span class="sxs-lookup"><span data-stu-id="8f3b5-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="8f3b5-104">V případě, že není komponenta zakázána, časovač nadále přijímá událost <xref:System.Windows.Forms.Timer.Tick> v zhruba stejném časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="8f3b5-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="8f3b5-105">Tato součást je navržená pro model Windows Forms prostředí.</span><span class="sxs-lookup"><span data-stu-id="8f3b5-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="8f3b5-106">Pokud potřebujete časovač, který je vhodný pro serverové prostředí, přečtěte si téma [Úvod k časovačům založeným na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="8f3b5-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="8f3b5-107">Vlastnost interval</span><span class="sxs-lookup"><span data-stu-id="8f3b5-107">The Interval Property</span></span>  
 <span data-ttu-id="8f3b5-108">Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> má při programování <xref:System.Windows.Forms.Timer> součásti vzít v úvahu několik omezení:</span><span class="sxs-lookup"><span data-stu-id="8f3b5-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
- <span data-ttu-id="8f3b5-109">Pokud vaše aplikace nebo jiná aplikace provádí v systému těžké požadavky – například dlouhé smyčky, náročné výpočty nebo jednotka, síť nebo přístup k portu, vaše aplikace nemusí získat události časovače, jak často vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> určuje.</span><span class="sxs-lookup"><span data-stu-id="8f3b5-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
- <span data-ttu-id="8f3b5-110">Interval není zaručený, aby uplynul přesně včas.</span><span class="sxs-lookup"><span data-stu-id="8f3b5-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="8f3b5-111">Aby se zajistila přesnost, časovač by měl podle potřeby kontrolovat systémové hodiny a nemusí se povést k internímu sledování nahromaděného času.</span><span class="sxs-lookup"><span data-stu-id="8f3b5-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
- <span data-ttu-id="8f3b5-112">Přesnost vlastnosti <xref:System.Windows.Forms.Timer.Interval%2A> je v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="8f3b5-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="8f3b5-113">Některé počítače poskytují čítač s vysokým rozlišením, který má rozlišení vyšší než milisekundy.</span><span class="sxs-lookup"><span data-stu-id="8f3b5-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="8f3b5-114">Dostupnost takového čítače závisí na hardwaru procesoru počítače.</span><span class="sxs-lookup"><span data-stu-id="8f3b5-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8f3b5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f3b5-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="8f3b5-116">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="8f3b5-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="8f3b5-117">Přehled komponenty Timer</span><span class="sxs-lookup"><span data-stu-id="8f3b5-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
