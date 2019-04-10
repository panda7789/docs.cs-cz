---
title: 'Postupy: Dědění formulářů pomocí dialogového okna Výběr dědičnosti'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], forms
- Inheritance Picker dialog box
- inherited forms [Windows Forms], creating
ms.assetid: 969b4c04-12aa-4297-93a2-0ae747447823
ms.openlocfilehash: 74dfd1bb2c47a8e377a2ed74934f742dff6cd64a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212281"
---
# <a name="how-to-inherit-forms-using-the-inheritance-picker-dialog-box"></a>Postupy: Dědění formulářů pomocí dialogového okna Výběr dědičnosti
Nejjednodušší způsob, jak dědit formuláře nebo jiný objekt je použít **výběr dědičnosti** dialogové okno. Pomocí něho můžete využít výhod kódu nebo uživatelské rozhraní (UI), již jste vytvořili v jiných řešení.  
  
> [!NOTE]
>  Aby bylo možné zdědit z formuláře s **výběr dědičnosti** dialogovém okně projekt, který obsahuje, které tvoří musí sestavené do spustitelného souboru nebo knihovny DLL. Sestavte projekt, zvolte **sestavit řešení** z **sestavení** nabídky.  
>   
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-create-a-windows-form-inherited-from-an-existing-form-by-using-the-inheritance-picker"></a>Vytvoření formuláře Windows dědí z existujícího formuláře pomocí dialogového okna Výběr dědičnosti  
  
1.  Z **projektu** nabídce zvolte **přidat formulář Windows**.  
  
     **Přidat novou položku** zobrazí se dialogové okno.  
  
2.  Hledání **zděděné formuláře** šablony z searchbox nebo kliknutím na **Windows Forms** kategorii, vyberte ho a pojmenujte ho v **název** pole. Klikněte na tlačítko **přidat** tlačítka budete pokračovat.  
  
     **Výběr dědičnosti** zobrazí se dialogové okno. Pokud projekt již obsahuje formuláře, jsou zobrazená v **výběr dědičnosti** dialogové okno.  
  
3.  Chcete-li dědit z formuláře v jiném sestavení, klikněte na tlačítko **Procházet** tlačítko.  
  
4.  V rámci **vyberte soubor, který obsahuje komponentu dědit z** dialogové okno, přejděte na projekt, který obsahuje formuláře nebo vyžadujete modulu.  
  
5.  Klikněte na název souboru .exe nebo .dll, který se vyberte ho a klikněte **otevřít** tlačítko.  
  
     Tím se vrátíte do **výběr dědičnosti** dialogové okno, kde komponenta je teď uvedený spolu s projektu, ve kterém se nachází.  
  
6.  Vyberte komponentu.  
  
     V **Průzkumníka řešení**, součást je přidána do projektu. Pokud má uživatelské rozhraní, ovládací prvky, které jsou součástí Zděděný formulář, budou označeny piktogram (![snímek jazyka Visual Basic dědičnosti symbol.](./media/how-to-inherit-forms-using-the-inheritance-picker-dialog-box/visual-basic-inheritance-glyph.gif)) a pokud je vybráno, ohraničený označující úroveň zabezpečení, který má ovládací prvek na supertřídu formuláře. Chování, které odpovídají různé úrovně zabezpečení jsou uvedeny v následující tabulce.  
  
    |Úroveň zabezpečení ovládacího prvku|K dispozici interakce prostřednictvím Návrhář a Editor kódu s zděděné formuláře|  
    |-------------------------------|--------------------------------------------------------------------------------|  
    |Public|Standardní ohraničení s úchyty pro změnu velikosti: ovládací prvek může být velikosti a přesunutí. Ovládací prvek je přístupný interně třídou, která jej deklaruje a externě podle jiných tříd.|  
    |Chráněno|Standardní ohraničení s úchyty pro změnu velikosti: ovládací prvek může být velikosti a přesunutí. Je přístupný interně třídu, která jej deklaruje a jakoukoli třídu, která dědí z nadřazené třídy, ale není přístupná externím třídy.|  
    |Chráněné vnitřní (chráněné spřátelené v jazyce Visual Basic)|Standardní ohraničení s úchyty pro změnu velikosti: ovládací prvek může být velikosti a přesunutí. Je přístupný interně třídu, která jej deklaruje, všechny třídy, která dědí z nadřazené třídy a ostatní členové sestavení, který jej obsahuje.|  
    |Interním (spřátelené v jazyce Visual Basic)|Standardní ohraničení s žádné úchyty pro změnu velikosti zobrazen ve formuláři, vlastnosti, které jsou viditelné v **vlastnosti** okna. Nicméně všechny aspekty ovládacího prvku se budou považovat za jen pro čtení. Nelze přesunout nebo velikost ovládacího prvku nebo změnit jeho vlastnosti. Pokud je ovládací prvek kontejneru jiných ovládacích prvků, jako je skupinový rámeček nové ovládací prvky nelze přidat, a nelze ji odebrat existující ovládací prvky, i v případě, že tyto ovládací prvky byly veřejné. Ovládací prvek je přístupný pouze ostatní členové sestavení, který jej obsahuje.|  
    |Soukromé|Standardní ohraničení s žádné úchyty pro změnu velikosti zobrazen ve formuláři, vlastnosti, které jsou viditelné v **vlastnosti** okna. Nicméně všechny aspekty ovládacího prvku se budou považovat za jen pro čtení. Nelze přesunout nebo velikost ovládacího prvku nebo změnit jeho vlastnosti. Pokud je ovládací prvek kontejneru jiných ovládacích prvků, jako je skupinový rámeček nové ovládací prvky nelze přidat, a nelze ji odebrat existující ovládací prvky, i v případě, že tyto ovládací prvky byly veřejné. Ovládací prvek je přístupný pouze pomocí třídy, která jej deklaruje.|  
  
     Informace o tom, jak změnit vzhled podkladového formuláře, naleznete v tématu [účinky úpravy vzhledu základního formuláře](effects-of-modifying-base-form-appearance.md).  
  
    > [!NOTE]
    >  Když zkombinujete zděděný ovládací prvky a součásti se standardní ovládací prvky a komponenty v aplikaci Windows Forms, může dojít, je v konfliktu s pořadí vykreslování. Můžete tento problém můžete vyřešit tak, že upravíte pořadí vykreslování, které se provádí v klikněte na **formátu** nabídky, přejdete na **pořadí**a pak levým na **přenést dopředu** nebo  **Přenést do pozadí**. Další informace o pořadí vykreslování ovládacích prvků naleznete v tématu [jak: Vrstvení objektů ve Windows Forms](../controls/how-to-layer-objects-on-windows-forms.md).  
  
## <a name="see-also"></a>Viz také:

- [Inherits – příkaz](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [používání](~/docs/csharp/language-reference/keywords/using.md)
- [Účinky úpravy vzhledu základního formuláře](effects-of-modifying-base-form-appearance.md)
- [Vizuální dědění Windows Forms](windows-forms-visual-inheritance.md)
