---
title: ProgressBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: 7dd434492cd688527ddbce5aaffa442a0b40a9e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968309"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar – přehled ovládacího prvku (Windows Forms)
> [!IMPORTANT]
> Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.ProgressBar> <xref:System.Windows.Forms.ProgressBar> ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.ToolStripProgressBar>  
  
 Model Windows Forms <xref:System.Windows.Forms.ProgressBar> ovládací prvek indikuje průběh procesu zobrazením vhodného počtu obdélníků uspořádaných do vodorovného pruhu. Po dokončení procesu je pruh vyplněn. Indikátory průběhu se běžně používají k poskytnutí toho, jak dlouho chcete počkat na dokončení procesu. např. při načítání velkého souboru.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ProgressBar> Ovládací prvek může být orientovaný na formuláři pouze vodorovně.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Klíčové vlastnosti <xref:System.Windows.Forms.ProgressBar> ovládacího prvku jsou <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>a <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. Vlastnosti <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a<xref:System.Windows.Forms.ProgressBar.Maximum%2A> nastaví maximální a minimální hodnoty, které může indikátor průběhu zobrazit. <xref:System.Windows.Forms.ProgressBar.Value%2A> Vlastnost představuje průběh, který byl proveden směrem k dokončení operace. Vzhledem k tomu, že pruh zobrazený v ovládacím prvku se skládá z bloků, hodnota <xref:System.Windows.Forms.ProgressBar> zobrazená ovládacím prvkem bude <xref:System.Windows.Forms.ProgressBar.Value%2A> odpovídat pouze aktuální hodnotě vlastnosti. Na základě velikosti <xref:System.Windows.Forms.ProgressBar> ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost určuje, kdy se má zobrazit další blok.  
  
 Nejběžnější způsob, jak aktualizovat aktuální hodnotu průběhu, je napsat kód pro nastavení <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnosti. V příkladu načtení velkého souboru můžete nastavit maximální velikost souboru v kilobajtech. Například pokud <xref:System.Windows.Forms.ProgressBar.Maximum%2A> je vlastnost nastavena na hodnotu 100 <xref:System.Windows.Forms.ProgressBar.Minimum%2A> , vlastnost je nastavena <xref:System.Windows.Forms.ProgressBar.Value%2A> na hodnotu 10 a vlastnost je nastavena na 50, zobrazí se 5 obdélníků. Toto je polovina čísla, které lze zobrazit.  
  
 Existují však i <xref:System.Windows.Forms.ProgressBar> další způsoby, jak upravit hodnotu zobrazenou ovládacím prvkem, kromě <xref:System.Windows.Forms.ProgressBar.Value%2A> nastavení vlastnosti přímo. Vlastnost může být použita k zadání hodnoty, o kterou se má <xref:System.Windows.Forms.ProgressBar.Value%2A> zvýšit hodnota vlastnosti. <xref:System.Windows.Forms.ProgressBar.Step%2A> Potom volání <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metody zvýší hodnotu. Chcete-li změnit přírůstek hodnoty, můžete použít <xref:System.Windows.Forms.ProgressBar.Increment%2A> metodu a zadat hodnotu, se kterou chcete <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost zvýšit.  
  
 Jiný ovládací prvek, který graficky informuje uživatele o aktuální akci, <xref:System.Windows.Forms.StatusBar> je ovládací prvek.  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.ToolStripStatusLabel> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBarPanel> Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a nahrazují<xref:System.Windows.Forms.StatusBar> a přidávají funkce ovládacím prvkům a; ovládací prvky a jsou však uchovávány pro zpětnou kompatibilitu i pro budoucí použití, pokud výběrem.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ProgressBar>
- [Ovládací prvek ProgressBar](progressbar-control-windows-forms.md)
