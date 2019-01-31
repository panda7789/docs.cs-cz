---
title: Omezení vlastnosti intervalu součásti Windows Forms Timer
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 2d8e25d9d27c0908f2d794a0c3c9646024984764
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269667"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Omezení vlastnosti intervalu součásti Windows Forms Timer
Windows Forms <xref:System.Windows.Forms.Timer> komponenta má <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, která určuje počet milisekund, které prochází mezi jeden časovače událostí a dalších. Pokud součást je zakázáno, časovač bude dál přijímat <xref:System.Windows.Forms.Timer.Tick> událost v intervalech přibližně stejnou dobu.  
  
 Tato součást je určená pro prostředí Windows Forms. Pokud potřebujete časovač, který je vhodný pro prostředí serveru, přečtěte si [Úvod do serverových časovače](https://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="the-interval-property"></a>Vlastnost Interval  
 <xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost má několik omezení ke zvážení, když programujete <xref:System.Windows.Forms.Timer> komponenty:  
  
-   Pokud vaše aplikace nebo jiná aplikace provádí kladou velké požadavky na systém – například dlouho smyčky, náročné na výpočty, nebo jednotku, sítě nebo přístup k – aplikace nelze získat události časovače tak často, jako <xref:System.Windows.Forms.Timer.Interval%2A> určuje vlastnost.  
  
-   Není zaručeno, že interval uplyne přesně včas. Aby se zajistila přesnost, časovač by měl zkontrolovat systémové hodiny podle potřeby, spíše než zkuste udržovat přehled o celkové čas interně.  
  
-   Přesnost <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost je v milisekundách. Některé počítače zadejte ve vysokém rozlišení čítač, který má vyšší než milisekund rozlišení. Dostupnost tyto čítače závisí na hardwaru procesoru vašeho počítače.
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Timer>
- [Komponenta Timer](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)
- [Přehled komponenty Timer](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
