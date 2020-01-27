---
title: Omezení vlastnosti intervalu komponenty časovače
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 15626a53f0541ff79e2098377d9dfdb4626ac155
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745229"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a>Omezení vlastnosti intervalu součásti Windows Forms Timer
Komponenta model Windows Forms <xref:System.Windows.Forms.Timer> má vlastnost <xref:System.Windows.Forms.Timer.Interval%2A>, která určuje počet milisekund, které budou uplynout mezi jednou událostí časovače a další. V případě, že není komponenta zakázána, časovač nadále přijímá událost <xref:System.Windows.Forms.Timer.Tick> v zhruba stejném časovém intervalu.  
  
 Tato součást je navržená pro model Windows Forms prostředí. Pokud potřebujete časovač, který je vhodný pro serverové prostředí, přečtěte si téma [Úvod k časovačům založeným na serveru](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
## <a name="the-interval-property"></a>Vlastnost interval  
 Vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> má při programování <xref:System.Windows.Forms.Timer> součásti vzít v úvahu několik omezení:  
  
- Pokud vaše aplikace nebo jiná aplikace provádí v systému těžké požadavky – například dlouhé smyčky, náročné výpočty nebo jednotka, síť nebo přístup k portu, vaše aplikace nemusí získat události časovače, jak často vlastnost <xref:System.Windows.Forms.Timer.Interval%2A> určuje.  
  
- Interval není zaručený, aby uplynul přesně včas. Aby se zajistila přesnost, časovač by měl podle potřeby kontrolovat systémové hodiny a nemusí se povést k internímu sledování nahromaděného času.  
  
- Přesnost vlastnosti <xref:System.Windows.Forms.Timer.Interval%2A> je v milisekundách. Některé počítače poskytují čítač s vysokým rozlišením, který má rozlišení vyšší než milisekundy. Dostupnost takového čítače závisí na hardwaru procesoru počítače.
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Timer>
- [Komponenta Timer](timer-component-windows-forms.md)
- [Přehled komponenty Timer](timer-component-overview-windows-forms.md)
