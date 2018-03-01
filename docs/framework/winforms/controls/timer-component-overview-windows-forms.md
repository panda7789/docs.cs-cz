---
title: "Přehled součásti Časovač (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 90296d2741a96e8788bf7a9b18bf3ea303ad2bae
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="timer-component-overview-windows-forms"></a><span data-ttu-id="feeec-102">Přehled součásti Časovač (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="feeec-102">Timer Component Overview (Windows Forms)</span></span>
<span data-ttu-id="feeec-103">Windows Forms <xref:System.Windows.Forms.Timer> je komponenta, která se vyvolá událost v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="feeec-103">The Windows Forms <xref:System.Windows.Forms.Timer> is a component that raises an event at regular intervals.</span></span> <span data-ttu-id="feeec-104">Tato součást je určená pro prostředí Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="feeec-104">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="feeec-105">Pokud potřebujete časovač, který je vhodný pro prostředí serveru, najdete v části [Úvod do serverové časovače](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span><span class="sxs-lookup"><span data-stu-id="feeec-105">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).</span></span>  
  
## <a name="key-properties-methods-and-events"></a><span data-ttu-id="feeec-106">Klíčové vlastnosti, metod a události</span><span class="sxs-lookup"><span data-stu-id="feeec-106">Key Properties, Methods, and Events</span></span>  
 <span data-ttu-id="feeec-107">Délka intervalů je definována <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, jehož hodnota je uvedena v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="feeec-107">The length of the intervals is defined by the <xref:System.Windows.Forms.Timer.Interval%2A> property, whose value is in milliseconds.</span></span> <span data-ttu-id="feeec-108">Pokud je povoleno komponentu, <xref:System.Windows.Forms.Timer.Tick> událost se vyvolá, každý intervalu.</span><span class="sxs-lookup"><span data-stu-id="feeec-108">When the component is enabled, the <xref:System.Windows.Forms.Timer.Tick> event is raised every interval.</span></span> <span data-ttu-id="feeec-109">Toto je, kde můžete přidat být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="feeec-109">This is where you would add code to be executed.</span></span> <span data-ttu-id="feeec-110">Další informace najdete v tématu [postupy: spuštění procedury v nastavení intervalech pomocí součásti Windows Forms Timer](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span><span class="sxs-lookup"><span data-stu-id="feeec-110">For more information, see [How to: Run Procedures at Set Intervals with the Windows Forms Timer Component](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).</span></span> <span data-ttu-id="feeec-111">Klíče metody <xref:System.Windows.Forms.Timer> jsou součástí <xref:System.Windows.Forms.Timer.Start%2A> a <xref:System.Windows.Forms.Timer.Stop%2A>, časovač zapnutí a vypnutí.</span><span class="sxs-lookup"><span data-stu-id="feeec-111">The key methods of the <xref:System.Windows.Forms.Timer> component are <xref:System.Windows.Forms.Timer.Start%2A> and <xref:System.Windows.Forms.Timer.Stop%2A>, which turn the timer on and off.</span></span> <span data-ttu-id="feeec-112">Když časovač je vypnuté, obnoví; neexistuje žádný způsob, jak pozastavit <xref:System.Windows.Forms.Timer> součásti.</span><span class="sxs-lookup"><span data-stu-id="feeec-112">When the timer is switched off, it resets; there is no way to pause a <xref:System.Windows.Forms.Timer> component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feeec-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="feeec-113">See Also</span></span>  
 <xref:System.Windows.Forms.Timer>  
 [<span data-ttu-id="feeec-114">Komponenta Timer</span><span class="sxs-lookup"><span data-stu-id="feeec-114">Timer Component</span></span>](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [<span data-ttu-id="feeec-115">Omezení vlastnosti intervalu komponenty Windows Forms Timer</span><span class="sxs-lookup"><span data-stu-id="feeec-115">Limitations of the Windows Forms Timer Component's Interval Property</span></span>](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
