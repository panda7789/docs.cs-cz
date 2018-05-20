---
title: Class – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Class
helpviewer_keywords:
- class modules
- Class statement [Visual Basic]
- classes [Visual Basic], fields
- fields [Visual Basic], of classes
- class types [Visual Basic], class statements
- classes [Visual Basic], creating
- classes [Visual Basic], data members
- data members [Visual Basic], of classes
ms.assetid: f2664f38-eb5a-4d4b-a374-1d041521fb6c
ms.openlocfilehash: 1d81ce148e237df6997934f70c294630f6cc7b8d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
---
# <a name="class-statement-visual-basic"></a>Class – příkaz (Visual Basic)
Deklaruje název třídy a představuje definici proměnné, vlastností, události a postupy, které zahrnuje třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] [ Partial ] _  
Class name [ ( Of typelist ) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ statements ]  
End Class  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attributelist`|Volitelné. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chráněný](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [Chráněné Friend](../../language-reference/modifiers/protected-friend.md)<br />- [Privátní chráněný](../../language-reference/modifiers/private-protected.md)<br/><br/> V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Volitelné. V tématu [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Volitelné. V tématu [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Volitelné. Určuje definici částečné třídy. V tématu [částečné](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Požadováno. Název této třídy. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Volitelné. Určuje, že toto je obecná třída.|  
|`typelist`|Vyžaduje, pokud použijete [z](../../../visual-basic/language-reference/statements/of-clause.md) – klíčové slovo. Seznam parametrů typu pro tuto třídu. V tématu [zadejte seznam](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelné. Označuje, že tato třída dědí členy jiné třídy. V tématu [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Vyžaduje, pokud použijete `Inherits` příkaz. Název třídy, ze které je tato třída odvozena.|  
|`Implements`|Volitelné. Označuje, že tato třída implementuje členy jedno nebo více rozhraní. V tématu [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Vyžaduje, pokud použijete `Implements` příkaz. Názvy rozhraní, které tato třída implementuje.|  
|`statements`|Volitelné. Příkazy, které definují členy této třídy.|  
|`End Class`|Požadováno. Ukončí `Class` definice.|  
  
## <a name="remarks"></a>Poznámky  
 A `Class` příkaz definuje nový datový typ. A *třída* je základní stavební blok objektově orientované programování (mimoprocesová aplikace VOLÁNA). Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Můžete použít `Class` pouze na úrovni oboru názvů nebo modul. To znamená *deklarace kontextu* pro třídu musí být zdrojový soubor, obor názvů, třídy, struktury, modul nebo rozhraní a nemůže být procedura nebo bloku. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Každá instance třídy má životnost nezávislé na všechny ostatní instance. Tato doba platnosti začíná, když je vytvořené [operátor New](../../../visual-basic/language-reference/operators/new-operator.md) klauzule nebo funkcí, jako <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Ho ukončí všechny proměnné odkazující na instanci být nastaven [nic](../../../visual-basic/language-reference/nothing.md) nebo instancí jiné třídy.  
  
 Výchozí nastavení třídy [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup. Můžete nastavit jejich úrovně přístupu s modifikátory přístupu. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Vnoření.** Můžete definovat jednu třídu v rámci jiného. Vnější třídy se nazývá *obsahující třídu*, a vnitřní třídy se nazývá *vnořené třídy*.  
  
-   **Dědičnost.** Pokud se používá třída [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md), můžete určit pouze jeden základní třídu nebo rozhraní. Třída nemůže Zdědit z více než jeden element.  
  
     Třída nemůže Zdědit z jiné třídy s více omezující úroveň přístupu. Například `Public` třída nemůže Zdědit z `Friend` třídy.  
  
     Třída nemůže Zdědit z ní vnořené třídy.  
  
-   **Implementace.** Pokud se používá třída [Implements – příkaz](../../../visual-basic/language-reference/statements/implements-statement.md), je nutné implementovat každý člen definované každé rozhraní, zadejte v `interfacenames`. Výjimkou je opětovná implementace člena základní třídy. Další informace najdete v tématu "Opětovná implementace" v [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Výchozí vlastnost.** Třídu můžete zadat maximálně jednu vlastnost jako jeho *výchozí vlastnost*. Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** V rámci třídy můžou deklarovat každého člena s vlastní úrovně přístupu. Členy třídy výchozí [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup kromě proměnných a konstant, které používá výchozí [privátní](../../../visual-basic/language-reference/modifiers/private.md) přístup. Pokud třída má omezený přístup k více než jeden z jejích členů, úroveň přístupu ke třídě přednost.  
  
-   **Rozsah.** Třída je v oboru v celé jeho obsahující obor názvů, třídy, struktury nebo modulu.  
  
     Rozsah každý člen třídy je celou třídu.  
  
     **Doba platnosti.** Visual Basic nepodporuje statické třídy. Ekvivalentní statická třída poskytuje modul. Další informace najdete v tématu [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Členy třídy mají v závislosti na tom, jak a kde jsou deklarovány životnosti. Další informace najdete v tématu [doba platnosti v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Kvalifikace.** Kód mimo třídu musí kvalifikaci jméno člena s názvem třídy.  
  
     Pokud kód uvnitř vnořené třídy vytváří nekvalifikované odkaz na element programování, Visual Basic vyhledá pro element nejprve v vnořené třídy, pak ve své obsahující třídy, a tak dále nejkrajnější obsahující elementu.  
  
## <a name="classes-and-modules"></a>Třídy a modulů  
 Tyto prvky mít mnoho podobností, ale existuje několik důležitých rozdílů.  
  
-   **Terminologie.** Předchozí verze jazyka Visual Basic rozpoznat dva typy modulů: *třídy modulů* (.cls soubory) a *standardní moduly* (BAS soubory). Aktuální verze volá tyto *třídy* a *moduly*, v uvedeném pořadí.  
  
-   **Sdílení členové.** Můžete určit, zda je sdílenou člena třídy nebo instance člena.  
  
-   **Objekt orientace.** Třídy jsou objektově orientované, ale nejsou moduly. Můžete vytvořit jeden nebo více instancí třídy. Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Class` příkaz zadat třídu a několik členů.  
  
 [!code-vb[VbVbalrStatements#62](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/class-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Struktury a třídy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Doba života objektu: Vytváření a zničení objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
