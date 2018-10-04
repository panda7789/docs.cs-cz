---
title: Module – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Module
- vb.Module
helpviewer_keywords:
- modules, classes
- modules
- Module statement [Visual Basic]
- modules, declaring
- standard modules
- classes [Visual Basic], vs. modules
- declarations [Visual Basic], modules
ms.assetid: a1243afc-14a5-45df-95d5-51118aeac362
ms.openlocfilehash: 5628224a08fe5f12cf2a81b179c4998001174354
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779868"
---
# <a name="module-statement"></a>Module – příkaz
Deklaruje název modulu a zavádí definici proměnných, vlastností, událostí a postupů, které se skládá z modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb 
[ <attributelist> ] [ accessmodifier ]  Module name  
    [ statements ]  
End Module  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Volitelné. Může být jedna z následujících akcí:  
  
-   [Public](../../../visual-basic/language-reference/modifiers/public.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
 Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `name`  
 Požadováno. Název tohoto modulu. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
 `statements`  
 Volitelné. Příkazy, které definují proměnné, vlastnosti, události, postupy a vnořené typy tohoto modulu.  
  
 `End Module`  
 Ukončuje `Module` definice.  
  
## <a name="remarks"></a>Poznámky  
 A `Module` prohlášení definuje typ odkazu, který je k dispozici v rámci svého oboru názvů. A *modulu* (říká se jim *standardní modul*) se podobá do třídy, ale některé důležité rozdíly. Každý modul nemá přesně jednu instanci a není nutné vytvořit či přiřazen proměnné. Moduly nepodporují dědičnosti nebo implementovat rozhraní. Všimněte si, že je modul *typ* v tom smyslu, že třídu nebo strukturu – programovací element má datový typ modulu nelze deklarovat.  
  
 Můžete použít `Module` pouze na úrovni oboru názvů. To znamená, že *kontext deklarace* modulu musí být zdrojový soubor nebo obor názvů a nemůže být třída, struktura, modulu, rozhraní, procedura nebo blok. Nelze vnořovat modulu jiný modul, nebo v rámci libovolného typu. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Modul má stejnou dobu života jako aplikaci. Protože všechny její členy jsou `Shared`, mají také životnosti rovna vlastnosti programu.  
  
 Moduly ve výchozím nastavení [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup. Můžete nastavit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Všichni členové modulu jsou implicitně `Shared`.  
  
## <a name="classes-and-modules"></a>Třídy a moduly  
 Tyto prvky řada podobností, ale existuje několik důležitých rozdílů.  
  
-   **Terminologie.** Předchozí verzí jazyka Visual Basic rozpoznat dva typy modulů: *moduly tříd* (.cls soubory) a *standardní moduly* (BAS soubory). Aktuální verze volá tyto *třídy* a *moduly*v uvedeném pořadí.  
  
-   **Sdílené členy.** Můžete řídit, jestli je sdílené člen třídy nebo člena instance.  
  
-   **Objekt orientace.** Třídy jsou objektově orientované, ale nejsou moduly. Proto pouze třídy může být vytvořen jako objekty. Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="rules"></a>pravidla  
  
-   **Modifikátory.** Všichni členové modulu jsou implicitně [Shared](../../../visual-basic/language-reference/modifiers/shared.md). Nelze použít `Shared` – klíčové slovo deklarace člena a není možné pozměnit sdílený stav kteréhokoli člena.  
  
-   **Dědičnost.** Modul nemůže dědit z libovolného typu jiného než <xref:System.Object>, ze které všechny moduly dědit. Konkrétně se jeden modul nemůže dědit z jiné.  
  
     Nelze použít [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md) v definici modulu ani k určení <xref:System.Object>.  
  
-   **Výchozí vlastnost.** V modulu nejde definovat žádné výchozí vlastnosti. Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** V rámci modulu můžete deklarovat každého člena se svou vlastní úroveň přístupu. Modul členy ve výchozím nastavení [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup, s výjimkou proměnné a konstanty, které výchozí [privátní](../../../visual-basic/language-reference/modifiers/private.md) přístup. Pokud modul má omezený přístup k více než jeden z jejích členů, úroveň přístupu zadaného modulu přednost.  
  
-   **Obor.** Modul je v oboru v rámci svého oboru názvů.  
  
     Obor každého člena modulu je celý modul. Všimněte si, že všichni členové této oblasti podstupovali *zadejte povýšení*, což způsobí, že jejich obor má být převeden na obor názvů obsahující modul. Další informace najdete v tématu [propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md).  
  
-   **Kvalifikace.** Máte více modulů v projektu a je možné deklarovat členy se stejným názvem ve dvou nebo více modulů. Pokud je odkaz z mimo modul, však musí kvalifikovat všechny odkazy na tento člen s názvem příslušný modul. Další informace najdete v tématu [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrStatements#69](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/module-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Příkaz Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Propagace typu](../../../visual-basic/programming-guide/language-features/declared-elements/type-promotion.md)
