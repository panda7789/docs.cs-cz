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
ms.openlocfilehash: 2e4514686afcbbe0e9ff0b3326c1be212db4f9f8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005153"
---
# <a name="class-statement-visual-basic"></a>Class – příkaz (Visual Basic)
Deklaruje název třídy a zavádí definici proměnných, vlastností, událostí a procedur, které třída zahrnuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
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
|`attributelist`|Volitelné. Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může to být jedna z následujících:<br /><br /> @no__t – 0[veřejných](../../../visual-basic/language-reference/modifiers/public.md)<br />[chráněný](../../../visual-basic/language-reference/modifiers/protected.md) @no__t – 0<br />-    –[přítel](../../../visual-basic/language-reference/modifiers/friend.md)<br />@no__t – 0[privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />[přítel chráněný](../../language-reference/modifiers/protected-friend.md) @no__t – 0<br />- [Private Protected](../../language-reference/modifiers/private-protected.md)<br/><br/> Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`MustInherit`|Volitelné. Viz [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).|  
|`NotInheritable`|Volitelné. Viz [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md).|  
|`Partial`|Volitelné. Označuje částečnou definici třídy. Zobrazit [částečné](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Požadováno. Název této třídy Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Volitelné. Určuje, že se jedná o obecnou třídu.|  
|`typelist`|Povinné, pokud použijete klíčové slovo [of](../../../visual-basic/language-reference/statements/of-clause.md) . Seznam parametrů typu pro tuto třídu. Viz [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelné. Označuje, že tato třída dědí členy jiné třídy. Viz [příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`classname`|Vyžaduje se, pokud použijete příkaz `Inherits`. Název třídy, ze které je tato třída odvozena.|  
|`Implements`|Volitelné. Označuje, že tato třída implementuje členy jednoho nebo více rozhraní. Viz [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Vyžaduje se, pokud použijete příkaz `Implements`. Názvy rozhraní, které tato třída implementuje.|  
|`statements`|Volitelné. Příkazy, které definují členy této třídy.|  
|`End Class`|Požadováno. Ukončí definici `Class`.|  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `Class` definuje nový datový typ. *Třída* je základním stavebním blokem objektově orientovaného programování (OOP). Další informace naleznete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
 @No__t-0 můžete použít pouze v oboru názvů nebo na úrovni modulu. To znamená, že *kontext deklarace* pro třídu musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedura nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Každá instance třídy má životnost nezávisle na všech ostatních instancích. Tato doba života začíná, když je vytvořena [novou klauzulí operátoru](../../../visual-basic/language-reference/operators/new-operator.md) nebo funkcí, jako je například <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>. Končí, když jsou všechny proměnné ukazující na instanci nastavené na [hodnotu Nothing](../../../visual-basic/language-reference/nothing.md) nebo na instance jiných tříd.  
  
 Třídy, které jsou ve výchozím nastavení [typu Friend](../../../visual-basic/language-reference/modifiers/friend.md) Access. Můžete upravit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidly  
  
- **Vnoření.** Můžete definovat jednu třídu v rámci jiné. Vnější třída se nazývá *obsahující třídu*a vnitřní třída se nazývá *vnořená třída*.  
  
- **Dědičnost.** Pokud třída používá [příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), můžete zadat pouze jednu základní třídu nebo rozhraní. Třída nemůže dědit z více než jednoho prvku.  
  
     Třída nemůže dědit z jiné třídy s více omezující úrovní přístupu. Například třída `Public` nemůže dědit z třídy `Friend`.  
  
     Třída nemůže dědit z třídy, ve které je vnořená.  
  
- **Provádění.** Pokud třída používá [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md), je nutné implementovat každého člena definovaného každým rozhraním, které zadáte v `interfacenames`. Výjimkou je přeimplementace člena základní třídy. Další informace naleznete v části "reimplementace" v tématu [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
- **Výchozí vlastnost.** Třída může zadat maximálně jednu vlastnost jako *výchozí vlastnost*. Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Předvídatelně  
  
- **Úroveň přístupu.** V rámci třídy můžete deklarovat každého člena s vlastní úrovní přístupu. Členové třídy jsou výchozí pro [veřejný](../../../visual-basic/language-reference/modifiers/public.md) přístup, s výjimkou proměnných a konstant, což je výchozí nastavení [privátního](../../../visual-basic/language-reference/modifiers/private.md) přístupu. Pokud má třída více omezený přístup než jeden z jejích členů, má úroveň přístupu ke třídě přednost.  
  
- **Oboru.** Třída je v oboru, který obsahuje obor názvů, třídu, strukturu nebo modul.  
  
     Rozsah každého člena třídy je celá třída.  
  
     **Platné.** Visual Basic nepodporuje statické třídy. Funkční ekvivalent statické třídy je poskytován modulem. Další informace naleznete v tématu [příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Členové třídy mají životnost v závislosti na tom, jak a kde jsou deklarovány. Další informace najdete v tématu [Doba života v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).  
  
- **Vydal.** Kód mimo třídu musí kvalifikovat název člena s názvem této třídy.  
  
     Pokud kód uvnitř vnořené třídy vytvoří nekvalifikovaný odkaz na prvek programování, Visual Basic vyhledá prvek nejprve ve vnořené třídě, potom v jeho nadřazené třídě a tak dále k vnějšímu nadřazenému prvku.  
  
## <a name="classes-and-modules"></a>Třídy a moduly  
 Tyto prvky mají hodně podobnosti, ale existují i některé důležité rozdíly.  
  
- **Vede.** Předchozí verze Visual Basic rozpoznávají dva typy modulů: *moduly tříd* (soubory. CLS) a *standardní moduly* (soubory. bas). Aktuální verze volá tyto *třídy* a *moduly*, v uvedeném pořadí.  
  
- **Sdílené členy.** Můžete určit, zda je člen třídy sdíleným členem nebo členem instance.  
  
- **Orientace objektu.** Třídy jsou objektově orientované, ale moduly nejsou. Můžete vytvořit jednu nebo více instancí třídy. Další informace naleznete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Class` k definování třídy a několika členů.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Viz také:

- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Struktury a třídy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Doba života objektu: Vytváření a zničení objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Postupy: Použití obecné třídy](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
