---
title: ProgressBar – přehled ovládacího prvku (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: 65533bc8f9125666e39c53635f5798573f66ef14
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523178"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar – přehled ovládacího prvku (Windows Forms)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> Ovládací prvek nahradí a přidá funkce, které <xref:System.Windows.Forms.ProgressBar> řízení; však <xref:System.Windows.Forms.ProgressBar> ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.  
  
 Windows Forms <xref:System.Windows.Forms.ProgressBar> ovládací prvek označuje průběh procesu zobrazením odpovídající počet obdélníků uspořádány ve vodorovném panelu. Po dokončení procesu se vyplní panelu. Indikátory průběhu se běžně používají k uživateli přidělit představu, jak jsme si počkat dokončení procesu. například při velkých souborů je načítání.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar> Ovládací prvek může být pouze vodorovně orientovaný na formuláři.  
  
## <a name="key-properties-and-methods"></a>Klíčové vlastnosti a metody  
 Klíčové vlastnosti <xref:System.Windows.Forms.ProgressBar> řízení, představují <xref:System.Windows.Forms.ProgressBar.Value%2A>, <xref:System.Windows.Forms.ProgressBar.Minimum%2A>, a <xref:System.Windows.Forms.ProgressBar.Maximum%2A>. <xref:System.Windows.Forms.ProgressBar.Minimum%2A> a <xref:System.Windows.Forms.ProgressBar.Maximum%2A> vlastnosti nastavte maximální a minimální hodnoty můžete zobrazit indikátor průběhu. <xref:System.Windows.Forms.ProgressBar.Value%2A> Vlastnost představuje pokroku, který provedl směrem k dokončení operace. Vzhledem k tomu, že na panelu se zobrazí v ovládacím prvku se skládá z bloků, zobrazí se hodnota ve <xref:System.Windows.Forms.ProgressBar> pouze blíží ovládacího prvku <xref:System.Windows.Forms.ProgressBar.Value%2A> aktuální hodnoty vlastnosti. Podle velikosti <xref:System.Windows.Forms.ProgressBar> ovládací prvek, <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost určuje, kdy se má zobrazit další blok.  
  
 Nejběžnější způsob, jak aktualizovat hodnotu aktuální průběh je napsat kód pro nastavení <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost. V příkladu načítání velkých souborů může být nastavena maximální velikost souboru v kilobajtech. Například pokud <xref:System.Windows.Forms.ProgressBar.Maximum%2A> vlastnost nastavena na hodnotu 100, <xref:System.Windows.Forms.ProgressBar.Minimum%2A> je nastavena na 10 a <xref:System.Windows.Forms.ProgressBar.Value%2A> je nastavena na 50, se zobrazí 5 obdélníků. Toto je první číslo, které je možné zobrazit.  
  
 Nicméně existují jiné způsoby ke změně hodnoty zobrazí <xref:System.Windows.Forms.ProgressBar> ovládacího prvku, kromě nastavení <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost přímo. <xref:System.Windows.Forms.ProgressBar.Step%2A> Vlastnosti lze zadat hodnotu zvýšit <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost. Potom volání <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> metoda zvýší hodnotu. Přírůstková hodnota se liší, můžete <xref:System.Windows.Forms.ProgressBar.Increment%2A> metoda a zadejte hodnotu, pomocí kterého se má zvýšit <xref:System.Windows.Forms.ProgressBar.Value%2A> vlastnost.  
  
 Je jiný ovládací prvek, který graficky informuje uživatele o aktuální akci <xref:System.Windows.Forms.StatusBar> ovládacího prvku.  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip> a <xref:System.Windows.Forms.ToolStripStatusLabel> ovládací prvky nahradit a přidání funkce, které <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> řídí; však <xref:System.Windows.Forms.StatusBar> a <xref:System.Windows.Forms.StatusBarPanel> ovládací prvky se zachovají pro zpětnou kompatibilitu a budoucí použití, pokud jste Zvolte.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ProgressBar>
- [Ovládací prvek ProgressBar](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
