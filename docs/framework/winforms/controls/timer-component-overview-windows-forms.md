---
title: Přehled komponenty Timer
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 83b52d395cdc3e3357bcf83517eab258a5c8ae08
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742783"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="0f430-102">Přehled součásti Časovač (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0f430-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="0f430-103"><xref:System.Windows.Forms.Timer> model Windows Forms je komponenta, která vyvolává událost v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="0f430-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="0f430-104">Tato součást je navržená pro model Windows Forms prostředí.</span><span class="sxs-lookup"><span data-stu-id="0f430-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="0f430-105">Pokud potřebujete časovač, který je vhodný pro serverové prostředí, přečtěte si téma [Úvod k časovačům založeným na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="0f430-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="0f430-106">Klíčové vlastnosti, metody a události</span><span class="sxs-lookup"><span data-stu-id="0f430-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="0f430-107">Délka intervalu je definována vlastností <xref:System.Windows.Forms.Timer.Interval%2A>, jejíž hodnota je v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="0f430-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="0f430-108">Je-li povolena komponenta, událost <xref:System.Windows.Forms.Timer.Tick> je vyvolána každý interval.</span><span class="sxs-lookup"><span data-stu-id="0f430-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="0f430-109">Tady byste měli přidat kód, který se má spustit.</span><span class="sxs-lookup"><span data-stu-id="0f430-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="0f430-110">Další informace najdete v tématu Postupy [: spouštění procedur v nastavených intervalech pomocí komponenty časovače model Windows Forms](run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="0f430-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="0f430-111">Klíčové metody součásti <xref:System.Windows.Forms.Timer> jsou <xref:System.Windows.Forms.Timer.Start%2A> a <xref:System.Windows.Forms.Timer.Stop%2A>, které zapínají a vypínají časovač.</span><span class="sxs-lookup"><span data-stu-id="0f430-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="0f430-112">Při vypnutí časovače je obnovena; neexistuje žádný způsob, jak pozastavit komponentu <xref:System.Windows.Forms.Timer>.</span><span class="sxs-lookup"><span data-stu-id="0f430-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f430-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f430-113">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="0f430-114">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="0f430-114">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="0f430-115">Omezení vlastnosti intervalu komponenty Windows Forms Timer</span><span class="sxs-lookup"><span data-stu-id="0f430-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](limitations-of-the-timer-component-interval-property.md)
