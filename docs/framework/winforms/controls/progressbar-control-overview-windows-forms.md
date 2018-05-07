---
title: ProgressBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: bd2b9615b0061a8f2133229edb49357cde69b39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar – přehled ovládacího prvku (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ProgressBar> řízení; však <xref:System.Windows.Forms.ProgressBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar> řízení označuje průběh procesu zobrazením odpovídající počet obdélníků uspořádané ve vodorovném řádku. Po dokončení procesu se naplní panelu. Indikátory průběhu běžně se používají uživatel získat představu o dlouhé čekání dokončení procesu. například když velký soubor je právě načítán.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar> Řízení může být pouze vodorovně orientovány na formuláři.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Klíčové vlastnosti <xref:System.Windows.Forms.ProgressBar> řízení, představují <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, a <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> vlastnosti nastavit maximální a minimální hodnoty může zobrazit indikátor průběhu. <xref:System.Windows.Forms.ProgressBar.Value%2A> Vlastnost představuje proces, který byl změněn na dokončení operace. Protože panelu zobrazí v ovládacím prvku se skládá z bloků, zobrazí se hodnota pomocí <xref:System.Windows.Forms.ProgressBar> řízení pouze blíží <xref:System.Windows.Forms.ProgressBar.Value%2A> aktuální hodnota vlastnosti. Podle velikosti <xref:System.Windows.Forms.ProgressBar> ovládací prvek, <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost určuje, kdy se mají zobrazit další blok.  
  
 Nejběžnější způsob aktualizace aktuální hodnota průběhu je napsat kód, chcete-li nastavit <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost. V příkladu načítání velký soubor může nastavit maximální velikost souboru v kilobajtech. Například pokud <xref:System.Windows.Forms.ProgressBar.Maximum%2A> je nastavena na 100, <xref:System.Windows.Forms.ProgressBar.Minimum%2A> je nastavena na 10 a <xref:System.Windows.Forms.ProgressBar.Value%2A> je nastavena na 50, se zobrazí 5 obdélníky. Toto je polovinu číslo, které mohou být zobrazeny.  
  
 Existují však další způsoby, jak upravit hodnotě zobrazené ve <xref:System.Windows.Forms.ProgressBar> ovládací prvek, bez ohledu na nastavení <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost přímo. <xref:System.Windows.Forms.ProgressBar.Step%2A> Vlastnost lze použít k určení hodnoty se zvýší <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost podle. Potom volání <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metoda se zvýší hodnota. Ke změně hodnoty přírůstku, můžete použít <xref:System.Windows.Forms.ProgressBar.Increment%2A> metoda a zadejte hodnotu, pomocí kterého se zvýší <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost.  
  
 Další ovládací prvek, který graficky informuje uživatele o aktuální akce je <xref:System.Windows.Forms.StatusBar> ovládacího prvku.  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkcí do <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky jsou uchovány pro zpětnou kompatibilitu a budoucí použití, pokud jste Vyberte.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ProgressBar>  
 [Ovládací prvek ProgressBar](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
