---
title: 'Postupy: Dědění formulářů pomocí dialogového okna Výběr dědičnosti'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 49c24b12616834ecc532a5568c0971e3dd75cfd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker-dialog-box"></a>Postupy: Dědění formulářů pomocí dialogového okna Výběr dědičnosti
Nejjednodušší způsob, jak dědit formuláře nebo jiného objektu je použití **výběr dědičnosti** dialogové okno. Pomocí něho můžete využít výhod kódu nebo uživatelské rozhraní (UI), již jste vytvořili v jiných řešení.  
  
> [!NOTE]
>  Aby bylo možné zdědit z formuláře s **výběr dědičnosti** dialogové okno, projekt obsahující tato forma musí mít sestavily do spustitelného souboru nebo knihovny DLL. Pro sestavení projektu, zvolte **sestavit řešení** z **sestavení** nabídky.  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-windows-form-inherited-from-an-existing-form-by-using-the-inheritance-picker"></a>K vytvoření formuláře Windows zděděno z existujícího formuláře pomocí nástroje pro výběr dědičnosti  
  
1.  Z **projektu** nabídce zvolte **přidat formuláře Windows**.  
  
     **Přidat novou položku** otevře se dialogové okno.  
  
2.  Vyberte **zděděná formuláře** šablony a pojmenujte ho **název** pole. Klikněte **přidat** tlačítko Pokračovat.  
  
     **Výběr dědičnosti** otevře se dialogové okno. Pokud aktuální projekt již obsahuje formulářů, jsou zobrazeny v **výběr dědičnosti** dialogové okno.  
  
3.  Dědění z formuláře v jiném sestavení, klikněte **Procházet** tlačítko.  
  
4.  V rámci **vyberte soubor, který obsahuje komponentu dědění z** dialogové okno pole, přejděte do projektu obsahující formulář nebo modul požadavky.  
  
5.  Klikněte na název souboru .exe nebo .dll, vyberte ho a klikněte na tlačítko **otevřete** tlačítko.  
  
     Tím se vrátíte do **výběr dědičnosti** dialogové okno, kde komponentu je nyní obsažena, společně s projektu, ve kterém se nachází.  
  
6.  Vyberte komponentu.  
  
     V **Průzkumníku**, součást se přidá do projektu. Pokud má uživatelské rozhraní, ovládací prvky, které jsou součástí zděděné formuláře, budou označeny glyf (![VisualBasicInheritanceSymbol – snímek obrazovky](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")), a pokud vybraná, mít ohraničení, která udává, úroveň zabezpečení, který má ovládací prvek na formuláři superclassed. Chování, které odpovídají různé úrovně zabezpečení jsou uvedené v následující tabulce.  
  
    |Úroveň zabezpečení ovládacího prvku|K dispozici interakce prostřednictvím Designer a Editor kódu s zděděné formuláře|  
    |-------------------------------|--------------------------------------------------------------------------------|  
    |Public|Standardní ohraničení s úchyty: řízení může být velikost a přesunout. Ovládací prvek je přístupná interně podle třídy, která ji deklaruje a externě podle jiné třídy.|  
    |Chráněno|Standardní ohraničení s úchyty: řízení může být velikost a přesunout. Je přístupný interně třídu, která ji deklaruje a každá třída, která dědí z nadřazené třídy, ale nelze získat přístup, externí třídy.|  
    |Chráněné vnitřní (chráněné Friend v jazyce Visual Basic)|Standardní ohraničení s úchyty: řízení může být velikost a přesunout. Je možné přistupovat interně podle třídy, který deklaruje ho, třídou, která dědí z nadřazené třídy a ostatním členům sestavení, který jej obsahuje.|  
    |Vnitřní (Friend v jazyce Visual Basic)|Standardní ohraničení s žádné úchyty zobrazen ve formuláři, vlastnosti viditelné v **vlastnosti** okno. Všechny aspekty ovládacího prvku se však považovat za jen pro čtení. Nelze přesunout nebo velikost ovládacího prvku nebo změnit jeho vlastnosti. Pokud ovládací prvek je kontejner jiných ovládacích prvků, podobně jako u skupiny nelze přidat nové ovládací prvky a stávající ovládací prvky nelze odebrat, i když tyto ovládací prvky byly veřejné. Ovládací prvek jsou přístupné pouze ostatní členové sestavení, který jej obsahuje.|  
    |Soukromé|Standardní ohraničení s žádné úchyty zobrazen ve formuláři, vlastnosti viditelné v **vlastnosti** okno. Všechny aspekty ovládacího prvku se však považovat za jen pro čtení. Nelze přesunout nebo velikost ovládacího prvku nebo změnit jeho vlastnosti. Pokud ovládací prvek je kontejner jiných ovládacích prvků, podobně jako u skupiny nelze přidat nové ovládací prvky a stávající ovládací prvky nelze odebrat, i když tyto ovládací prvky byly veřejné. Ovládací prvek jsou přístupné pouze podle třídy, který deklaruje ho.|  
  
     Informace o tom, jak změnit vzhled podkladového formuláře najdete v tématu [účinky úpravy vzhledu základního formuláře](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md).  
  
    > [!NOTE]
    >  Když zkombinujete s standardní ovládací prvky a součásti v rozhraní Windows Forms zděděné ovládací prvky a součásti, můžete se setkat je v konfliktu s pořadí z-ordering. Můžete to vyřešit změnou pořadí, které se provádí v kliknete na **formátu** nabídky, přejdete na příkaz **pořadí**a pak levým na **přenést dopředu** nebo  **Přenést do pozadí**. Další informace o pořadí vykreslování ovládacích prvků najdete v tématu [postup: vrstva objektů ve formulářích Windows](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md).  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Inherits](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [using](~/docs/csharp/language-reference/keywords/using.md)  
 [Účinky úpravy vzhledu základního formuláře](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [Vizuální dědění modelu Windows Forms](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
