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
ms.openlocfilehash: 7bc2d6a6b3e01cd7efa00763d3b9bf3a0026be6f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975872"
---
# <a name="class-statement-visual-basic"></a>Class – příkaz (Visual Basic)
Deklaruje název třídy a zavádí definici proměnných, vlastností, událostí a postupy, které tvoří třídu.  
  
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
|`attributelist`|Volitelné. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend –](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />-   [Chráněné typu Friend](../../language-reference/modifiers/protected-friend.md)<br />- [Privátní, chráněné](../../language-reference/modifiers/private-protected.md)<br/><br/> Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Volitelné. Zobrazit [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Volitelné. Zobrazit [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Volitelné. Označuje částečnou definici třídy. Zobrazit [částečné](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Povinný parametr. Název této třídy. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Volitelné. Určuje, že se jedná o obecnou třídu.|  
|`typelist`|Povinné, pokud používáte [z](../../../visual-basic/language-reference/statements/of-clause.md) – klíčové slovo. Seznam parametrů typu pro tuto třídu. Zobrazit [seznamu](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelné. Označuje, že tato třída dědí členy jiné třídy. Zobrazit [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Povinné, pokud používáte `Inherits` příkazu. Název třídy, ze kterého tato třída odvozená.|  
|`Implements`|Volitelné. Označuje, že tato třída implementuje členy jednoho nebo více rozhraní. Zobrazit [implementuje příkaz](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Povinné, pokud používáte `Implements` příkazu. Názvy rozhraní, které tato třída implementuje.|  
|`statements`|Volitelné. Příkazy, které definují členy této třídy.|  
|`End Class`|Povinný parametr. Ukončuje `Class` definice.|  
  
## <a name="remarks"></a>Poznámky  
 A `Class` prohlášení definuje nového datového typu. A *třídy* je základním stavebním blokem objektově orientované programování (OOP). Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 Můžete použít `Class` pouze na úrovni oboru názvů nebo modulu. To znamená, *kontextu deklarace* pro třídu musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nesmí být procedura nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Každá instance třídy má životnost nezávislou na všech ostatních instancích. Tato doba života začíná, když je vytvořena [operátor New](../../../visual-basic/language-reference/operators/new-operator.md) klauzule nebo funkcí, jako <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Končí při byly nastaveny všechny proměnné odkazující na instanci [nic](../../../visual-basic/language-reference/nothing.md) nebo instancí jiné třídy.  
  
 Třídy výchozí [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup. Můžete nastavit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>pravidla  
  
-   **Vnoření.** Můžete definovat jednu třídu v rámci jiného. Vnější třída se nazývá *obsahující třídu*, a vnitřní třída se nazývá *vnořenou třídu*.  
  
-   **Dědičnost.** Pokud třída používá [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md), můžete zadat pouze jednu základní třídu nebo rozhraní. Třída nemůže dědit z více než jeden element.  
  
     Třída nemůže dědit z jiné třídy s více omezující úroveň přístupu. Například `Public` třída nemůže dědit od třídy `Friend` třídy.  
  
     Třída nemůže dědit ze třídy do něho vnořený.  
  
-   **Implementace.** Pokud třída používá [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md), musíte implementovat každého člena definovaného každým rozhraním, zadejte v `interfacenames`. Jedinou výjimkou je to je patřící třídě člena základní třídy. Další informace najdete v tématu "Patřící třídě" [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
-   **Výchozí vlastnost.** Třída může určit nejvýše jednu vlastnost jako jeho *výchozí vlastnost*. Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** V rámci třídy můžete deklarovat každého člena se svou vlastní úroveň přístupu. Členy třídy ve výchozím nastavení [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup, s výjimkou proměnné a konstanty, které výchozí [privátní](../../../visual-basic/language-reference/modifiers/private.md) přístup. Pokud třída má omezený přístup k více než jeden z jejích členů, úroveň přístupu ke třídě přednost.  
  
-   **Obor.** Třída je v oboru v celém jeho nadřazeného oboru názvů, třídy, struktury nebo modulu.  
  
     Obor každého člena třídy je celá třída.  
  
     **Doba platnosti.** Visual Basic nepodporuje statické třídy. Ekvivalentní statická třída poskytuje modulu. Další informace najdete v tématu [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Členy třídy mají životnost v závislosti na tom, jak a kde jsou deklarovány. Další informace najdete v tématu [životnosti v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
-   **Kvalifikace.** Kód mimo třídu musí kvalifikovat název člena s názvem třídy.  
  
     Pokud kód uvnitř vnořené třídy vytváří nekvalifikovaný odkaz na programovací prvek, Visual Basic vyhledá prvek nejprve ve vnořené třídy, pak v jeho obsahující třídy, a tak dále navýšení kapacity na vnější obsahující element.  
  
## <a name="classes-and-modules"></a>Třídy a moduly  
 Tyto prvky řada podobností, ale existuje několik důležitých rozdílů.  
  
-   **Terminologie.** Předchozí verzí jazyka Visual Basic rozpoznat dva typy modulů: *moduly tříd* (.cls soubory) a *standardní moduly* (BAS soubory). Aktuální verze volá tyto *třídy* a *moduly*v uvedeném pořadí.  
  
-   **Sdílené členy.** Můžete řídit, jestli je sdílené člen třídy nebo člena instance.  
  
-   **Objekt orientace.** Třídy jsou objektově orientované, ale nejsou moduly. Můžete vytvořit jednu nebo víc instancí třídy. Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Class` příkaz k definování třídy a několik členů.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Viz také:
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Struktury a třídy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Doba života objektu: Způsob vytváření a zničení objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
