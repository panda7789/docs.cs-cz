---
title: Přehled součásti Časovač (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: a13afba026f1f9eed095817c65637bb6a091c7f0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725282"
---
# <a name="timer-component-overview-windows-forms"></a>Přehled součásti Časovač (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Timer> je komponenta, která vyvolává událost v pravidelných intervalech. Tato součást je určená pro prostředí Windows Forms. Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="key-properties-methods-and-events"></a>Klíčové vlastnosti, metody a události  
 Délka intervalu je definován <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, jejíž hodnota je v milisekundách. Když je povolené komponenty, <xref:System.Windows.Forms.Timer.Tick> událost se vyvolá, každý interval. Je to, kde přidáte kód, který se spustí. Další informace najdete v tématu [jak: Spouštění procedur v nastavených intervalech pomocí komponenty Windows Forms Timer](run-procedures-at-set-intervals-with-wf-timer-component.md). Klíče metody <xref:System.Windows.Forms.Timer> komponenty jsou <xref:System.Windows.Forms.Timer.Start%2A> a <xref:System.Windows.Forms.Timer.Stop%2A>, časovač zapnutí a vypnutí. Když je časovač vypnout, resetuje; neexistuje žádný způsob, jak pozastavit <xref:System.Windows.Forms.Timer> komponenty.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Timer>
- [Komponenta Timer](timer-component-windows-forms.md)
- [Omezení vlastnosti intervalu komponenty Windows Forms Timer](limitations-of-the-timer-component-interval-property.md)
