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
# <a name="timer-component-overview-windows-forms"></a>Přehled součásti Časovač (Windows Forms)
<xref:System.Windows.Forms.Timer> model Windows Forms je komponenta, která vyvolává událost v pravidelných intervalech. Tato součást je navržená pro model Windows Forms prostředí. Pokud potřebujete časovač, který je vhodný pro serverové prostředí, přečtěte si téma [Úvod k časovačům založeným na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="key-properties-methods-and-events"></a>Klíčové vlastnosti, metody a události  
 Délka intervalu je definována vlastností <xref:System.Windows.Forms.Timer.Interval%2A>, jejíž hodnota je v milisekundách. Je-li povolena komponenta, událost <xref:System.Windows.Forms.Timer.Tick> je vyvolána každý interval. Tady byste měli přidat kód, který se má spustit. Další informace najdete v tématu Postupy [: spouštění procedur v nastavených intervalech pomocí komponenty časovače model Windows Forms](run-procedures-at-set-intervals-with-wf-timer-component.md). Klíčové metody součásti <xref:System.Windows.Forms.Timer> jsou <xref:System.Windows.Forms.Timer.Start%2A> a <xref:System.Windows.Forms.Timer.Stop%2A>, které zapínají a vypínají časovač. Při vypnutí časovače je obnovena; neexistuje žádný způsob, jak pozastavit komponentu <xref:System.Windows.Forms.Timer>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.Timer>
- [Komponenta Timer](timer-component-windows-forms.md)
- [Omezení vlastnosti intervalu komponenty Windows Forms Timer](limitations-of-the-timer-component-interval-property.md)
