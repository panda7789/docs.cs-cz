---
title: Omezení vlastnosti intervalu součásti Windows Forms Timer
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: f564a4ce7fa2d9b8ea5446f2cf6bd016db054dd9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724385"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="50d7c-102">Omezení vlastnosti intervalu součásti Windows Forms Timer</span><span class="sxs-lookup"><span data-stu-id="50d7c-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="50d7c-103">Windows Forms <xref:System.Windows.Forms.Timer> komponenta má <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, která určuje počet milisekund, které prochází mezi jeden časovače událostí a dalších.</span><span class="sxs-lookup"><span data-stu-id="50d7c-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="50d7c-104">Pokud součást je zakázáno, časovač bude dál přijímat <xref:System.Windows.Forms.Timer.Tick> událost v intervalech přibližně stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="50d7c-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="50d7c-105">Tato součást je určená pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="50d7c-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="50d7c-106">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="50d7c-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="50d7c-107">Vlastnost Interval</span><span class="sxs-lookup"><span data-stu-id="50d7c-107">The Interval Property</span></span>  
 <span data-ttu-id="50d7c-108"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost má několik omezení ke zvážení, když programujete <xref:System.Windows.Forms.Timer> komponenty:</span><span class="sxs-lookup"><span data-stu-id="50d7c-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="50d7c-109">Pokud vaše aplikace nebo jiná aplikace provádí kladou velké požadavky na systém – například dlouho smyčky, náročné na výpočty, nebo jednotku, sítě nebo přístup k – aplikace nelze získat události časovače tak často, jako <xref:System.Windows.Forms.Timer.Interval%2A> určuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="50d7c-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="50d7c-110">Není zaručeno, že interval uplyne přesně včas.</span><span class="sxs-lookup"><span data-stu-id="50d7c-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="50d7c-111">Aby se zajistila přesnost, časovač by měl zkontrolovat systémové hodiny podle potřeby, spíše než zkuste udržovat přehled o celkové čas interně.</span><span class="sxs-lookup"><span data-stu-id="50d7c-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="50d7c-112">Přesnost <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost je v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="50d7c-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="50d7c-113">Některé počítače zadejte ve vysokém rozlišení čítač, který má vyšší než milisekund rozlišení.</span><span class="sxs-lookup"><span data-stu-id="50d7c-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="50d7c-114">Dostupnost tyto čítače závisí na hardwaru procesoru vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="50d7c-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="50d7c-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50d7c-115">See also</span></span>
- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="50d7c-116">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="50d7c-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="50d7c-117">Přehled komponenty Timer</span><span class="sxs-lookup"><span data-stu-id="50d7c-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
