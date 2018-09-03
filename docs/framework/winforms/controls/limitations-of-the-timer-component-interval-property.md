---
title: Omezení součásti Windows Forms Timer&#39;vlastnosti Interval s
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: e5b9e7e43369913f0cdc9c7f2111bd4fe58675e6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465652"
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a><span data-ttu-id="8d23e-102">Omezení součásti Windows Forms Timer&#39;vlastnosti Interval s</span><span class="sxs-lookup"><span data-stu-id="8d23e-102">Limitations of the Windows Forms Timer Component&#39;s Interval Property</span></span>
<span data-ttu-id="8d23e-103">Windows Forms <xref:System.Windows.Forms.Timer> komponenta má <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, která určuje počet milisekund, které prochází mezi jeden časovače událostí a dalších.</span><span class="sxs-lookup"><span data-stu-id="8d23e-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="8d23e-104">Pokud součást je zakázáno, časovač bude dál přijímat <xref:System.Windows.Forms.Timer.Tick> událost v intervalech přibližně stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="8d23e-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="8d23e-105">Tato součást je určená pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="8d23e-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="8d23e-106">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="8d23e-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="8d23e-107">Vlastnost Interval</span><span class="sxs-lookup"><span data-stu-id="8d23e-107">The Interval Property</span></span>  
 <span data-ttu-id="8d23e-108"><xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost má několik omezení ke zvážení, když programujete <xref:System.Windows.Forms.Timer> komponenty:</span><span class="sxs-lookup"><span data-stu-id="8d23e-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
-   <span data-ttu-id="8d23e-109">Pokud vaše aplikace nebo jiná aplikace provádí kladou velké požadavky na systém – například dlouho smyčky, náročné na výpočty, nebo jednotku, sítě nebo přístup k – aplikace nelze získat události časovače tak často, jako <xref:System.Windows.Forms.Timer.Interval%2A> určuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8d23e-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
-   <span data-ttu-id="8d23e-110">Není zaručeno, že interval uplyne přesně včas.</span><span class="sxs-lookup"><span data-stu-id="8d23e-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="8d23e-111">Aby se zajistila přesnost, časovač by měl zkontrolovat systémové hodiny podle potřeby, spíše než zkuste udržovat přehled o celkové čas interně.</span><span class="sxs-lookup"><span data-stu-id="8d23e-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
-   <span data-ttu-id="8d23e-112">Přesnost <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost je v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="8d23e-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="8d23e-113">Některé počítače zadejte ve vysokém rozlišení čítač, který má vyšší než milisekund rozlišení.</span><span class="sxs-lookup"><span data-stu-id="8d23e-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="8d23e-114">Dostupnost tyto čítače závisí na hardwaru procesoru vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="8d23e-114">The availability of such a counter depends on the processor hardware of your computer.</span></span> <span data-ttu-id="8d23e-115">Další informace najdete v článku 172338, "Jak na použití QueryPerformanceCounter do kódu v době," znalostní báze Microsoft Knowledge Base na http://support.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="8d23e-115">For more information, see article 172338, "How To Use QueryPerformanceCounter to Time Code," in the Microsoft Knowledge Base at http://support.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d23e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d23e-116">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="8d23e-117">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="8d23e-117">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="8d23e-118">Přehled komponenty Timer</span><span class="sxs-lookup"><span data-stu-id="8d23e-118">Timer Component Overview</span></span>](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
