---
title: Přehled součásti Časovač (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- Timer
helpviewer_keywords:
- Timer component [Windows Forms], about Timer components
- timers [Windows Forms], about timers
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
ms.openlocfilehash: 39bc3c8cda06a62eb40b042e46cbd070a82cce01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="timer-component-overview-windows-forms"></a>Přehled součásti Časovač (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Timer> je komponenta, která se vyvolá událost v pravidelných intervalech. Tato součást je určená pro prostředí Windows Forms. Pokud potřebujete časovač, který je vhodný pro prostředí serveru, najdete v části [Úvod do serverové časovače](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="key-properties-methods-and-events"></a>Klíčové vlastnosti, metod a události  
 Délka intervalů je definována <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, jehož hodnota je uvedena v milisekundách. Pokud je povoleno komponentu, <xref:System.Windows.Forms.Timer.Tick> událost se vyvolá, každý intervalu. Toto je, kde můžete přidat být spuštěn. Další informace najdete v tématu [postupy: spuštění procedury v nastavení intervalech pomocí součásti Windows Forms Timer](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md). Klíče metody <xref:System.Windows.Forms.Timer> jsou součástí <xref:System.Windows.Forms.Timer.Start%2A> a <xref:System.Windows.Forms.Timer.Stop%2A>, časovač zapnutí a vypnutí. Když časovač je vypnuté, obnoví; neexistuje žádný způsob, jak pozastavit <xref:System.Windows.Forms.Timer> součásti.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Timer>  
 [Komponenta Timer](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Omezení vlastnosti intervalu komponenty Windows Forms Timer](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)
