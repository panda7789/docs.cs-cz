---
title: 'Postupy: Nastavení pořadí ovládacích prvků ve Windows Forms'
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
ms.openlocfilehash: 50f5f91a946aeebc4d82630b25d18d8f8d2ea4be
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339902"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Postupy: Nastavení pořadí ovládacích prvků ve Windows Forms
Pořadí je v tom pořadí, ve kterém uživatel přesune fokus z jednoho ovládacího prvku na jiný stisknutím klávesy TAB. Každý formulář má svůj vlastní pořadí. Výchozí pořadí je stejné jako pořadí, ve které jste vytvořili ovládací prvky. Pořadí karet číslování začíná nulou.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-set-the-tab-order-of-a-control"></a>Chcete-li nastavit pořadí ovládacího prvku  
  
1. Na **zobrazení** nabídky, klikněte na tlačítko **pořadí**.  
  
     Tím se aktivuje režim výběru pořadí prvků ve formuláři. Číslo (představující <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost) se zobrazí v levém horním rohu každého ovládacího prvku.  
  
2. Klepněte na ovládací prvky nasazují postupně, aby pořadí prvků, které chcete vytvořit.  
  
    > [!NOTE]
    >  Místo ovládacího prvku v rámci pořadí karet lze nastavit na libovolnou hodnotu větší než nebo rovna 0. Pokud dojde k duplicity, je vyhodnocen pořadí vykreslování dvou ovládacích prvků a ovládací prvek v horní části na kartách první. (Pořadí vykreslování je vizuální rozvržení ovládací prvky ve formuláři podél osy z formuláře [hloubka]. Pořadí vykreslování určuje, jaké ovládací prvky jsou před další ovládací prvky.) Další informace o pořadí vykreslování, naleznete v tématu [vrstvení objektů ve formulářích Windows](how-to-layer-objects-on-windows-forms.md).  
  
3. Jakmile budete hotovi, klikněte na tlačítko **pořadí** na **zobrazení** nabídku ukončit režim pořadí karty.  
  
    > [!NOTE]
    >  Ovládací prvky, které nelze získat fokus, stejně jako ovládací prvky zakázané a neviditelná, nemají <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost a jsou není zahrnuta v pořadí karet. Jako uživatel stiskne klávesu TAB, tyto ovládací prvky se přeskočí.  
  
 Alternativně lze nastavit pořadí prvků v okně Vlastnosti pomocí <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost. <xref:System.Windows.Forms.Control.TabIndex%2A> Vlastnost ovládacího prvku určuje, kde je umístěn v pořadí. Ve výchozím nastavení, má první ovládací prvek vykreslen <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu 0, je druhý <xref:System.Windows.Forms.Control.TabIndex%2A> 1 a tak dále.  
  
 Kromě toho ve výchozím nastavení <xref:System.Windows.Forms.GroupBox> ovládací prvek má svůj vlastní <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu, která představuje celé číslo. A <xref:System.Windows.Forms.GroupBox> samotný ovládací prvek nemůže mít fokus v době běhu. Díky tomu se každý ovládací prvek v rámci <xref:System.Windows.Forms.GroupBox> má svůj vlastní desetinné <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu počínaje.0. Přirozeně, jako <xref:System.Windows.Forms.Control.TabIndex%2A> z <xref:System.Windows.Forms.GroupBox> se zvýší, ovládací prvek, ovládací prvky v ní se zvýší odpovídajícím způsobem. Pokud jste změnili <xref:System.Windows.Forms.Control.TabIndex%2A> hodnotu od 5 do 6, <xref:System.Windows.Forms.Control.TabIndex%2A> prvním ovládacím prvku v jeho skupině automaticky změní na 6.0 a tak dále.  
  
 Nakonec libovolný ovládací prvek n na formuláři mohou být přeskočeny v pořadí. Obvykle klávesy TAB postupně v době běhu vybere všechny ovládací prvky v pořadí karet. Tím, že vypíná <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost, lze nastavení ovládacího prvku předaný pořadí prvků formuláře.  
  
#### <a name="to-remove-a-control-from-the-tab-order"></a>Odebrat ovládací prvek v pořadí karet  
  
1. Nastavit u tohoto prvku <xref:System.Windows.Forms.Control.TabStop%2A> vlastnost `false` v okně Vlastnosti.  
  
     A ovládací prvek, jehož <xref:System.Windows.Forms.Control.TabStop%2A> je nastavená vlastnost `false` stále udržuje jeho pozice v pořadí, i v případě, že ovládací prvek bude přeskočena při přepínání mezi ovládací prvky pomocí klávesy TAB.  
  
    > [!NOTE]
    >  Skupina přepínacích tlačítek je do jedné karty zastavit v době běhu. Vybraného tlačítka (tj. tlačítko s jeho <xref:System.Windows.Forms.RadioButton.Checked%2A> vlastnost nastavena na hodnotu `true`) má jeho <xref:System.Windows.Forms.Control.TabStop%2A> automaticky nastavena na `true`, i když má další tlačítka jejich <xref:System.Windows.Forms.Control.TabStop%2A> nastavenou na `false`. Další informace o seskupování <xref:System.Windows.Forms.RadioButton> ovládacích prvků, naleznete v tématu [seskupení Windows Forms ovládací prvky RadioButton do funkce v podobě sady](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky Windows Forms](index.md)
- [Uspořádávání ovládacích prvků ve Windows Forms](arranging-controls-on-windows-forms.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Ovládací prvky Windows Forms podle funkce](windows-forms-controls-by-function.md)
