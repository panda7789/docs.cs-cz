---
title: Přehled součásti Časovač (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 6e453f6b7718c6c5be3109f51153a3f5e4b5b6f4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227997"
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="ff5a9-102">Přehled součásti Časovač (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ff5a9-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="ff5a9-103">Windows Forms <xref:System.Windows.Forms.Timer> je komponenta, která vyvolává událost v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="ff5a9-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="ff5a9-104">Tato součást je určená pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ff5a9-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="ff5a9-105">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="ff5a9-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="ff5a9-106">Klíčové vlastnosti, metody a události</span><span class="sxs-lookup"><span data-stu-id="ff5a9-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="ff5a9-107">Délka intervalu je definován <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, jejíž hodnota je v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="ff5a9-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="ff5a9-108">Když je povolené komponenty, <xref:System.Windows.Forms.Timer.Tick> událost se vyvolá, každý interval.</span><span class="sxs-lookup"><span data-stu-id="ff5a9-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="ff5a9-109">Je to, kde přidáte kód, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="ff5a9-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="ff5a9-110">Další informace najdete v tématu [postupy: spouštění procedur v nastavení intervalech pomocí komponenty Windows Forms Timer](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="ff5a9-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="ff5a9-111">Klíče metody <xref:System.Windows.Forms.Timer> komponenty jsou <xref:System.Windows.Forms.Timer.Start%2A> a <xref:System.Windows.Forms.Timer.Stop%2A>, časovač zapnutí a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="ff5a9-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="ff5a9-112">Když je časovač vypnout, resetuje; neexistuje žádný způsob, jak pozastavit <xref:System.Windows.Forms.Timer> komponenty.</span><span class="sxs-lookup"><span data-stu-id="ff5a9-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff5a9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff5a9-113">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="ff5a9-114">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="ff5a9-114">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="ff5a9-115">Omezení vlastnosti intervalu komponenty Windows Forms Timer</span><span class="sxs-lookup"><span data-stu-id="ff5a9-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
