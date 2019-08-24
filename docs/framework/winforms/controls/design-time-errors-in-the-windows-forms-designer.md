---
title: Chyby při návrhu v Návrháři formulářů Windows
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cce9baf1523391e281593428b633c401103b42b5
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015975"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Chyby v době návrhu v Návrhář formulářů

Toto téma vysvětluje význam a použití seznamu chyb v době návrhu, který se zobrazí v aplikaci Visual Studio, když se Návrhář formulářů nepodařilo načíst. Pokud se zobrazí tento seznam chyb, neměli byste ho interpretovat jako chybu v návrháři, ale jako pomůcku pro opravu chyb v kódu.

Základní porozumění tomuto seznamu chyb vám pomůže ladit aplikace tím, že poskytuje podrobné informace o chybách a navrhuje možná řešení.

## <a name="the-design-time-error-list-interface"></a>Rozhraní seznamu chyb v době návrhu

Pokud se Návrhář formulářů nepodařilo načíst, zobrazí se v Návrháři seznam chyb. Chyby jsou seskupené do kategorií. Například pokud máte čtyři instance nedeklarovaných proměnných, budou seskupeny do stejné kategorie chyb. Každá kategorie chyb obsahuje stručný popis, který shrnuje chybu.

Kategorii chyb můžete rozbalit nebo sbalit buď kliknutím na záhlaví kategorie chyby, nebo kliknutím na dvojitou šipku rozbalení/sbalení. Po rozbalení kategorie chyby se zobrazí následující další Help:

- Instance této chyby

- Pomůžete s touto chybou.

- Příspěvky o této chybě ve fórech

### <a name="instances-of-this-error"></a>Instance této chyby

Další Help seznam všech výskytů chyby v aktuálním projektu. Mnoho chyb zahrnuje přesné umístění v následujícím formátu: *[název projektu]* *[název formuláře]* řádek: *[řádek číslo]* sloupec: *[číslo sloupce]* . Odkaz **Přejít na kód** přejde do umístění ve vašem kódu, kde dojde k chybě.

Pokud je zásobník volání spojen s chybou, můžete kliknout na odkaz **Zobrazit zásobník volání** , který dále rozšiřuje chybu pro zobrazení zásobníku volání. Prozkoumání zásobníku může poskytnout cenné informace o ladění. Můžete například sledovat funkce, které byly volány před tím, než došlo k chybě. Zásobník volání je možné vybrat, abyste ho mohli zkopírovat a uložit.

> [!NOTE]
> V Visual Basic seznam chyb v době návrhu nezobrazuje více než jednu chybu, ale může zobrazit více instancí stejné chyby. V vizuálu C++chyby neobsahují odkazy kódu goto nebo odkazy na řádky.

### <a name="forum-posts-about-this-error"></a>Příspěvky o této chybě ve fórech

Další help obsahuje odkaz na příspěvky na fórech související s chybou. Fóra se prohledávají na základě řetězce chybové zprávy. Můžete si také vyzkoušet hledání na následujících fórech:

- [Fórum Návrhář formulářů](https://social.msdn.microsoft.com/Forums/windows/home?forum=winformsdesigner)

- [Fórum model Windows Forms](https://social.msdn.microsoft.com/Forums/windows/home?category=windowsforms)

### <a name="ignore-and-continue"></a>Ignorovat a pokračovat

Můžete se rozhodnout Ignorovat chybový stav a pokračovat v načítání návrháře. Pokud zvolíte tuto akci, může dojít k neočekávanému chování. Například ovládací prvky se nemusí zobrazit na návrhové ploše.

## <a name="see-also"></a>Viz také:

- [Řešení potíží s vývojem v době návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
- [Řešení potíží s vytvářením ovládacích prvků a komponent](troubleshooting-control-and-component-authoring.md)
- [Vývoj ovládacích prvků Windows Forms v době návrhu](developing-windows-forms-controls-at-design-time.md)
- [Návrhář formulářů chybové zprávy](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))
