---
title: 'Postupy: Dědění formulářů pomocí dialogového okna Výběr dědičnosti'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 9382f1bf890fb5a886cf547d9b1e9b3031c12eb6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039996"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker"></a>Postupy: Dědění formulářů pomocí výběru dědičnosti

Nejjednodušší způsob, jak dědit formulář nebo jiný objekt, je použít dialogové okno **Výběr dědičnosti** . Díky tomu můžete využít výhod kódu nebo uživatelského rozhraní (UI), které jste už vytvořili v jiných řešeních.

> [!NOTE]
> Aby bylo možné dědit z formuláře pomocí dialogového okna **Výběr dědičnosti** , musí být projekt obsahující tento formulář integrován do spustitelného souboru nebo knihovny DLL. Chcete-li sestavit projekt, v nabídce **sestavení** klikněte na příkaz **Sestavit řešení** .

## <a name="create-a-windows-form-by-using-the-inheritance-picker"></a>Vytvoření formuláře Windows pomocí výběru dědičnosti

1. V aplikaci Visual Studio v nabídce **projekt** vyberte možnost **Přidat formulář Windows**.

   **Přidat novou položku** zobrazí se dialogové okno.

2. Vyhledejte zděděnou šablonu **formuláře** buď z SearchBox, nebo kliknutím na kategorii **model Windows Forms** , vyberte ji a pojmenujte ji do pole **název** . Pokračujte kliknutím na tlačítko **Přidat** .

   Otevře se dialogové okno **Výběr dědičnosti** . Pokud aktuální projekt již obsahuje formuláře, zobrazí se v dialogovém okně **Výběr dědičnosti** .

3. Chcete-li dědit z formuláře v jiném sestavení, klikněte na tlačítko **Procházet** .

4. V dialogovém okně **Vyberte soubor, který obsahuje komponentu, která má dědit z** dialogového okna, přejděte do projektu obsahujícího formulář nebo modul, který si přejete.

5. Kliknutím na název souboru. exe nebo. dll ho vyberte a klikněte na tlačítko **otevřít** .

   Tím se vrátíte k dialogovému oknu **Výběr dědičnosti** , kde je nyní komponenta uvedena, spolu s projektem, ve kterém se nachází.

6. Vyberte součást.

   V **Průzkumník řešení**je komponenta přidána do projektu. Pokud má uživatelské rozhraní, ovládací prvky, které jsou součástí zděděného formuláře, budou označeny glyfem (![snímek obrazovky Visual Basic symbol dědičnosti.](./media/how-to-inherit-forms-using-the-inheritance-picker-dialog-box/visual-basic-inheritance-glyph.gif)) a pokud je tato možnost vybrána, mají ohraničení označující úroveň zabezpečení, kterou ovládací prvek má na setříděný formulář. V následující tabulce jsou uvedena chování, která odpovídají různým úrovním zabezpečení.

    |Úroveň zabezpečení ovládacího prvku|Dostupná interakce prostřednictvím návrháře a editoru kódu s Děděným formulářem|
    |-------------------------------|--------------------------------------------------------------------------------|
    |Public|Standardní ohraničení s úchyty pro změnu velikosti: ovládací prvek může být velikost a přesunutý. K ovládacímu prvku lze přistupovat interně třídou, která je deklaruje a externě jinými třídami.|
    |Chráněno|Standardní ohraničení s úchyty pro změnu velikosti: ovládací prvek může být velikost a přesunutý. Lze k interně přistupovat třídou, která ji deklaruje, a libovolné třídě, která dědí z nadřazené třídy, ale není k ní možné přistupovat externími třídami.|
    |Chráněný interní (chráněný přítel v Visual Basic)|Standardní ohraničení s úchyty pro změnu velikosti: ovládací prvek může být velikost a přesunutý. Lze k němu přistupovat interně třídou, která ji deklaruje, jakoukoliv třídou, která dědí z nadřazené třídy a ostatními členy sestavení, které ji obsahují.|
    |Interní (Friend v Visual Basic)|Standardní ohraničení bez úchytů pro změnu velikosti zobrazené ve formuláři, vlastnosti viditelné v okně **vlastnosti** . Všechny aspekty tohoto ovládacího prvku však budou považovány za jen pro čtení. Ovládací prvek nelze přesunout nebo změnit jeho velikost nebo změnit jeho vlastnosti. Pokud je ovládací prvek kontejnerem jiných ovládacích prvků, jako je například skupinový rámeček, nelze přidat nové ovládací prvky a stávající ovládací prvky nelze odebrat, i když byly tyto ovládací prvky veřejné. K ovládacímu prvku můžou mít pøístup jenom ostatní členové sestavení, který ho obsahuje.|
    |Soukromé|Standardní ohraničení bez úchytů pro změnu velikosti zobrazené ve formuláři, vlastnosti viditelné v okně **vlastnosti** . Všechny aspekty tohoto ovládacího prvku však budou považovány za jen pro čtení. Ovládací prvek nelze přesunout nebo změnit jeho velikost nebo změnit jeho vlastnosti. Pokud je ovládací prvek kontejnerem jiných ovládacích prvků, jako je například skupinový rámeček, nelze přidat nové ovládací prvky a stávající ovládací prvky nelze odebrat, i když byly tyto ovládací prvky veřejné. K ovládacímu prvku může mít pøístup jenom třída, která ho deklaruje.|

     Informace o tom, jak změnit vzhled základního formuláře, najdete v tématu [účinky úpravy vzhledu základního formuláře](effects-of-modifying-base-form-appearance.md).

    > [!NOTE]
    > Pokud kombinujete zděděné ovládací prvky a komponenty se standardními ovládacími prvky a komponentami na model Windows Forms, může dojít ke konfliktům s řazením z. To můžete opravit úpravou pořadí vykreslování, které je provedeno kliknutím v nabídce **Formát** , ukázáním na položku **pořadí**a následným kliknutím na možnost **přenést do popředí** nebo **přenést do pozadí**. Další informace o pořadí vykreslování ovládacích prvků naleznete v tématu [How to: Objekty vrstvy na model Windows Forms](../controls/how-to-layer-objects-on-windows-forms.md).

## <a name="see-also"></a>Viz také:

- [Příkaz Inherits](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [using](~/docs/csharp/language-reference/keywords/using.md)
- [Účinky úpravy vzhledu základního formuláře](effects-of-modifying-base-form-appearance.md)
- [Vizuální dědění modelu Windows Forms](windows-forms-visual-inheritance.md)
