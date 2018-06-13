---
title: Omezení součásti Windows Forms Timer&#39;s vlastnost intervalu
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: 4808d115ff842c6c0e6b036da9fe20bb1b48f8a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536023"
---
# <a name="limitations-of-the-windows-forms-timer-component39s-interval-property"></a>Omezení součásti Windows Forms Timer&#39;s vlastnost intervalu
Windows Forms <xref:System.Windows.Forms.Timer> součást obsahuje <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost, která určuje počet milisekund, po které se předají mezi jeden časovače událostí a další. Pokud je zakázána, časovač nadále přijímat <xref:System.Windows.Forms.Timer.Tick> událost v přibližně stejné časové intervaly.  
  
 Tato součást je určená pro prostředí Windows Forms. Pokud potřebujete časovač, který je vhodný pro prostředí serveru, najdete v části [Úvod do serverové časovače](http://msdn.microsoft.com/library/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## <a name="the-interval-property"></a>Vlastnost intervalu  
 <xref:System.Windows.Forms.Timer.Interval%2A> Vlastnost má několik omezení ke zvážení, když jsou programování <xref:System.Windows.Forms.Timer> součásti:  
  
-   Aplikace nebo jiné aplikace upravuje velkou požadavky na systém – například dlouho smyčky, náročné výpočty, nebo jednotku, sítě nebo přístup k portu – aplikace nelze získat události časovače tak často, jako <xref:System.Windows.Forms.Timer.Interval%2A> určuje vlastnost.  
  
-   Interval není zaručena uplynout přesně na čas. Aby byla zajištěna přesnost, časovač by měl Zkontrolujte systémové hodiny podle potřeby, nikoli zkuste ke sledování Akumulovaná čas interně.  
  
-   Přesnost <xref:System.Windows.Forms.Timer.Interval%2A> vlastnost je v milisekundách. Některé počítače zadejte ve vysokém rozlišení čítač, který má vyšší než počet milisekund rozlišení. Dostupnost tyto čítače závisí na procesoru hardware počítače. Další informace najdete v článku 172338, "Jak k použití QueryPerformanceCounter do kódu v době," v databázi Microsoft Knowledge Base na http://support.microsoft.com.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Timer>  
 [Komponenta Timer](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)  
 [Přehled komponenty Timer](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)
