---
title: 'Postupy: Nastavení pořadí karet ve formulářích Windows'
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
ms.openlocfilehash: ca5b9c29d9138d4e17fbf187e35951dbec614aab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539848"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Postupy: Nastavení pořadí karet ve formulářích Windows
Pořadí je v pořadí, ve kterém uživatel přesune fokus z jednoho ovládacího prvku na jiný, stisknutím klávesy TAB. Každý formulář má svou vlastní pořadí. Výchozí pořadí je stejný jako pořadí, ve které jste vytvořili ovládací prvky. Pořadí číslování začíná nula.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-tab-order-of-a-control"></a>Chcete-li nastavit pořadí ovládacího prvku  
  
1.  Na **zobrazení** nabídky, klikněte na tlačítko **pořadí karet**.  
  
     Tím dojde k aktivaci režimu výběru pořadí prvků na formuláři. Číslo (představující <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost) se zobrazí v levém horním rohu každého ovládacího prvku.  
  
2.  Klikněte na ovládací prvky postupně pořadí, které chcete vytvořit.  
  
    > [!NOTE]
    >  Místní ovládacího prvku v rámci pořadí karet můžete nastavit na jakoukoli hodnotu větší než nebo rovna 0. Pokud dojde k duplikáty, vyhodnotí pořadí dvou ovládacích prvků a je – ovládací prvek v horní části se záložkami první. (Pořadí je vizuální rozvržení ovládací prvky ve formuláři podél osy z formuláře [hloubka]. Pořadí vykreslování určuje ovládacích prvků, které jsou před ostatní ovládací prvky.) Další informace o pořadí z-order, najdete v části [vrstvení objektů ve formulářích Windows](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
3.  Po dokončení klikněte na tlačítko **pořadí karet** na **zobrazení** znovu chcete ukončit režim karta pořadí, v nabídce.  
  
    > [!NOTE]
    >  Ovládací prvky, které nelze získat fokus, jakož i zakázaná a neviditelná ovládacích prvků, nemají <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnosti a jsou neobsažených v pořadí. Jako stisknutí klávesy TAB, tyto ovládací prvky se přeskočí.  
  
 Alternativně lze nastavit pořadí prvků v okně Vlastnosti pomocí <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost. <xref:System.Windows.Forms.Control.TabIndex%2A> Vlastnost ovládacího prvku určuje, kde je umístěn v pořadí. Ve výchozím nastavení, má první prvek vykreslovat <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu 0, druhý má <xref:System.Windows.Forms.Control.TabIndex%2A> 1 a tak dále.  
  
 Kromě toho ve výchozím nastavení <xref:System.Windows.Forms.GroupBox> ovládací prvek má svou vlastní <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu, která je celé číslo. A <xref:System.Windows.Forms.GroupBox> samotném ovládacím prvku nemůže být vybrán jako aktivní v době běhu. Proto každý ovládací prvek v rámci <xref:System.Windows.Forms.GroupBox> má svou vlastní decimal <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu, počínaje.0. Samozřejmě, jako <xref:System.Windows.Forms.Control.TabIndex%2A> z <xref:System.Windows.Forms.GroupBox> řízení se zvýší, ovládací prvky v něm se zvýší odpovídajícím způsobem. Pokud jste změnili <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu od 5 do 6, <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu prvního ovládacího prvku v jeho skupiny automaticky změní na 6.0 a tak dále.  
  
 Nakonec některý z ovládacích prvků mnoho na formuláři mohou být přeskočeny v pořadí. Obvykle stisknutím klávesy TAB postupně v době běhu vybírá každý ovládací prvek v pořadí. Vypnutím <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost, můžete použít ovládací prvek předaná pořadí prvků formuláře.  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>Odebrání pořadí ovládacího prvku  
  
1.  Nastavte ovládacího prvku <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost `false` v okně Vlastnosti.  
  
     A řídit, jehož <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost byla nastavena na `false` stále udržuje pozici v pořadí, i když při procházení ovládacích prvků pomocí klávesy TAB bylo přeskočeno ovládacího prvku.  
  
    > [!NOTE]
    >  Skupina přepínacích tlačítek má do jedné karty zastavit v době běhu. Vybrané tlačítko (to znamená, tlačítko s jeho <xref:System.Windows.Forms.RadioButton.Checked%2A> vlastnost nastavena na hodnotu `true`) má jeho <xref:System.Windows.Forms.Control.TabStop%2A> automaticky nastavena na `true`, zatímco jiné tlačítka mají jejich <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost nastavena na hodnotu `false`. Další informace o seskupení <xref:System.Windows.Forms.RadioButton> najdete v části ovládací prvky, [seskupení Windows Forms RadioButton – ovládací prvky funkce jako sada](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## <a name="see-also"></a>Viz také  
 [Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/index.md)  
 [Uspořádávání ovládacích prvků ve Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Ovládací prvky Windows Forms podle funkce](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
