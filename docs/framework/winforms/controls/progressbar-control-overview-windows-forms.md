---
title: ProgressBar – přehled ovládacího prvku
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: a0c4a0401d06614ab3ad148b932ebc64080c592c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741277"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar – přehled ovládacího prvku (Windows Forms)
> [!IMPORTANT]
> Ovládací prvek <xref:System.Windows.Forms.ToolStripProgressBar> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.ProgressBar>; Nicméně ovládací prvek <xref:System.Windows.Forms.ProgressBar> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
 Ovládací prvek model Windows Forms <xref:System.Windows.Forms.ProgressBar> indikuje průběh procesu zobrazením vhodného počtu obdélníků uspořádaných na vodorovném panelu. Po dokončení procesu je pruh vyplněn. Indikátory průběhu se běžně používají k poskytnutí toho, jak dlouho chcete počkat na dokončení procesu. např. při načítání velkého souboru.  
  
> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.ProgressBar> může být orientovaný na formuláři pouze vodorovně.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Klíčové vlastnosti ovládacího prvku <xref:System.Windows.Forms.ProgressBar> jsou <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>a <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. Vlastnosti <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> nastaví maximální a minimální hodnoty, se kterými se může indikátor průběhu zobrazit. Vlastnost <xref:System.Windows.Forms.ProgressBar.Value%2A> představuje průběh, který byl proveden směrem k dokončení operace. Vzhledem k tomu, že pruh zobrazený v ovládacím prvku se skládá z bloků, hodnota zobrazená ovládacím prvkem <xref:System.Windows.Forms.ProgressBar> se blíží pouze aktuální hodnotě vlastnosti <xref:System.Windows.Forms.ProgressBar.Value%2A>. Na základě velikosti ovládacího prvku <xref:System.Windows.Forms.ProgressBar> určuje vlastnost <xref:System.Windows.Forms.ProgressBar.Value%2A>, kdy se má zobrazit další blok.  
  
 Nejběžnější způsob, jak aktualizovat aktuální hodnotu průběhu, je napsat kód pro nastavení vlastnosti <xref:System.Windows.Forms.ProgressBar.Value%2A>. V příkladu načtení velkého souboru můžete nastavit maximální velikost souboru v kilobajtech. Pokud je například vlastnost <xref:System.Windows.Forms.ProgressBar.Maximum%2A> nastavena na 100, vlastnost <xref:System.Windows.Forms.ProgressBar.Minimum%2A> je nastavena na hodnotu 10 a vlastnost <xref:System.Windows.Forms.ProgressBar.Value%2A> je nastavena na 50, zobrazí se 5 obdélníků. Toto je polovina čísla, které lze zobrazit.  
  
 Existují však i další způsoby, jak upravit hodnotu zobrazenou ovládacím prvkem <xref:System.Windows.Forms.ProgressBar> a zrušit z nastavení vlastnosti <xref:System.Windows.Forms.ProgressBar.Value%2A> přímo. Vlastnost <xref:System.Windows.Forms.ProgressBar.Step%2A> lze použít k určení hodnoty pro zvýšení hodnoty <xref:System.Windows.Forms.ProgressBar.Value%2A> o. Pak voláním metody <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> zvýší hodnotu. Chcete-li změnit přírůstek hodnoty, můžete použít metodu <xref:System.Windows.Forms.ProgressBar.Increment%2A> a zadat hodnotu, se kterou má být zvýšena vlastnost <xref:System.Windows.Forms.ProgressBar.Value%2A>.  
  
 Jiný ovládací prvek, který graficky informuje uživatele o aktuální akci, je ovládací prvek <xref:System.Windows.Forms.StatusBar>.  
  
> [!IMPORTANT]
> Ovládací prvky <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> nahrazují a přidávají funkce ovládacím prvkům <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel>; ovládací prvky <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> se však uchovávají pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ProgressBar>
- [Ovládací prvek ProgressBar](progressbar-control-windows-forms.md)
