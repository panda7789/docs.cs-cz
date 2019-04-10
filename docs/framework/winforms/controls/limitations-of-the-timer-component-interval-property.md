---
title: Omezení vlastnosti intervalu součásti Windows Forms Timer
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 54782c4e0460ba1ba9b8a870b8f60f08a76340b3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125169"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="10f7d-102">Omezení vlastnosti intervalu součásti Windows Forms Timer</span><span class="sxs-lookup"><span data-stu-id="10f7d-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="10f7d-103">Windows Forms <xref:System.Windows.Forms.Timer> komponenta má <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, která určuje počet milisekund, které prochází mezi jeden časovače událostí a dalších.</span><span class="sxs-lookup"><span data-stu-id="10f7d-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="10f7d-104">Pokud součást je zakázáno, časovač bude dál přijímat <xref:System.Windows.Forms.Timer.Tick> událost v intervalech přibližně stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="10f7d-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="10f7d-105">Tato součást je určená pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="10f7d-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="10f7d-106">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="10f7d-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="10f7d-107">Vlastnost Interval</span><span class="sxs-lookup"><span data-stu-id="10f7d-107">The Interval Property</span></span>  
 <span data-ttu-id="10f7d-108"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost má několik omezení ke zvážení, když programujete <xref:System.Windows.Forms.Timer> komponenty:</span><span class="sxs-lookup"><span data-stu-id="10f7d-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="10f7d-109">Pokud vaše aplikace nebo jiná aplikace provádí kladou velké požadavky na systém – například dlouho smyčky, náročné na výpočty, nebo jednotku, sítě nebo přístup k – aplikace nelze získat události časovače tak často, jako <xref:System.Windows.Forms.Timer.Interval%2A> určuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="10f7d-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="10f7d-110">Není zaručeno, že interval uplyne přesně včas.</span><span class="sxs-lookup"><span data-stu-id="10f7d-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="10f7d-111">Aby se zajistila přesnost, časovač by měl zkontrolovat systémové hodiny podle potřeby, spíše než zkuste udržovat přehled o celkové čas interně.</span><span class="sxs-lookup"><span data-stu-id="10f7d-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="10f7d-112">Přesnost <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost je v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="10f7d-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="10f7d-113">Některé počítače zadejte ve vysokém rozlišení čítač, který má vyšší než milisekund rozlišení.</span><span class="sxs-lookup"><span data-stu-id="10f7d-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="10f7d-114">Dostupnost tyto čítače závisí na hardwaru procesoru vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="10f7d-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="10f7d-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10f7d-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="10f7d-116">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="10f7d-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="10f7d-117">Přehled komponenty Timer</span><span class="sxs-lookup"><span data-stu-id="10f7d-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
