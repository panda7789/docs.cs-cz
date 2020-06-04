---
title: Class – příkaz
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
ms.openlocfilehash: bdb73772dfe0e6d49d89a4ef006b1bceac14c8ee
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397152"
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
  
|Pojem|Definice|  
|---|---|  
|`attributelist`|Nepovinný parametr. Viz [seznam atributů](attribute-list.md).|  
|`accessmodifier`|Nepovinný parametr. Může to být jedna z následujících:<br /><br /> -   [Republik](../modifiers/public.md)<br />-   [Proti](../modifiers/protected.md)<br />-   [Friend](../modifiers/friend.md)<br />-   [Hlášen](../modifiers/private.md)<br />-   [Chráněný přítel](../modifiers/protected-friend.md)<br />- [Soukromé chráněné](../modifiers/private-protected.md)<br/><br/> Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Nepovinný parametr. Viz [Shadows](../modifiers/shadows.md).|  
|`MustInherit`|Nepovinný parametr. Viz [MustInherit](../modifiers/mustinherit.md).|  
|`NotInheritable`|Nepovinný parametr. Viz [NotInheritable](../modifiers/notinheritable.md).|  
|`Partial`|Nepovinný parametr. Označuje částečnou definici třídy. Zobrazit [částečné](../modifiers/partial.md).|  
|`name`|Povinná hodnota. Název této třídy Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Nepovinný parametr. Určuje, že se jedná o obecnou třídu.|  
|`typelist`|Povinné, pokud použijete klíčové slovo [of](of-clause.md) . Seznam parametrů typu pro tuto třídu. Viz [seznam typů](type-list.md).|  
|`Inherits`|Nepovinný parametr. Označuje, že tato třída dědí členy jiné třídy. Viz [příkaz Inherits](inherits-statement.md).|  
|`classname`|Vyžaduje se, pokud použijete `Inherits` příkaz. Název třídy, ze které je tato třída odvozena.|  
|`Implements`|Nepovinný parametr. Označuje, že tato třída implementuje členy jednoho nebo více rozhraní. Viz [příkaz Implements](implements-statement.md).|  
|`interfacenames`|Vyžaduje se, pokud použijete `Implements` příkaz. Názvy rozhraní, které tato třída implementuje.|  
|`statements`|Nepovinný parametr. Příkazy, které definují členy této třídy.|  
|`End Class`|Povinná hodnota. Ukončí `Class` definici.|  
  
## <a name="remarks"></a>Poznámky  
 `Class`Příkaz definuje nový datový typ. *Třída* je základním stavebním blokem objektově orientovaného programování (OOP). Další informace naleznete v tématu [objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md).  
  
 Můžete použít `Class` pouze v oboru názvů nebo na úrovni modulu. To znamená, že *kontext deklarace* pro třídu musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedura nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).  
  
 Každá instance třídy má životnost nezávisle na všech ostatních instancích. Tato doba životnosti začíná, když je vytvořena [novou klauzulí operátoru](../operators/new-operator.md) nebo funkcí, jako je například <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A> . Končí, když jsou všechny proměnné ukazující na instanci nastavené na [hodnotu Nothing](../nothing.md) nebo na instance jiných tříd.  
  
 Třídy, které jsou ve výchozím nastavení [typu Friend](../modifiers/friend.md) Access. Můžete upravit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
- **Vnoření.** Můžete definovat jednu třídu v rámci jiné. Vnější třída se nazývá *obsahující třídu*a vnitřní třída se nazývá *vnořená třída*.  
  
- **Dědičnost.** Pokud třída používá [příkaz Inherits](inherits-statement.md), můžete zadat pouze jednu základní třídu nebo rozhraní. Třída nemůže dědit z více než jednoho prvku.  
  
     Třída nemůže dědit z jiné třídy s více omezující úrovní přístupu. `Public`Třída například nemůže dědit z `Friend` třídy.  
  
     Třída nemůže dědit z třídy, ve které je vnořená.  
  
- **Provádění.** Pokud třída používá [příkaz Implements](implements-statement.md), je nutné implementovat každého člena definovaného každým rozhraním, které zadáte v `interfacenames` . Výjimkou je přeimplementace člena základní třídy. Další informace naleznete v části "reimplementace" v tématu [Implements](implements-clause.md).  
  
- **Výchozí vlastnost.** Třída může zadat maximálně jednu vlastnost jako *výchozí vlastnost*. Další informace najdete v tématu [výchozí](../modifiers/default.md).  
  
## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** V rámci třídy můžete deklarovat každého člena s vlastní úrovní přístupu. Členové třídy jsou výchozí pro [veřejný](../modifiers/public.md) přístup, s výjimkou proměnných a konstant, což je výchozí nastavení [privátního](../modifiers/private.md) přístupu. Pokud má třída více omezený přístup než jeden z jejích členů, má úroveň přístupu ke třídě přednost.  
  
- **Oboru.** Třída je v oboru, který obsahuje obor názvů, třídu, strukturu nebo modul.  
  
     Rozsah každého člena třídy je celá třída.  
  
     **Platné.** Visual Basic nepodporuje statické třídy. Funkční ekvivalent statické třídy je poskytován modulem. Další informace naleznete v tématu [příkaz Module](module-statement.md).  
  
     Členové třídy mají životnost v závislosti na tom, jak a kde jsou deklarovány. Další informace najdete v tématu [Doba života v Visual Basic](../../programming-guide/language-features/declared-elements/lifetime.md).  
  
- **Vydal.** Kód mimo třídu musí kvalifikovat název člena s názvem této třídy.  
  
     Pokud kód uvnitř vnořené třídy vytvoří nekvalifikovaný odkaz na prvek programování, Visual Basic vyhledá prvek nejprve ve vnořené třídě, potom v jeho nadřazené třídě a tak dále k vnějšímu nadřazenému prvku.  
  
## <a name="classes-and-modules"></a>Třídy a moduly  
 Tyto prvky mají hodně podobnosti, ale existují i některé důležité rozdíly.  
  
- **Vede.** Předchozí verze Visual Basic rozpoznávají dva typy modulů: *moduly tříd* (soubory. CLS) a *standardní moduly* (soubory. bas). Aktuální verze volá tyto *třídy* a *moduly*, v uvedeném pořadí.  
  
- **Sdílené členy.** Můžete určit, zda je člen třídy sdíleným členem nebo členem instance.  
  
- **Orientace objektu.** Třídy jsou objektově orientované, ale moduly nejsou. Můžete vytvořit jednu nebo více instancí třídy. Další informace naleznete v tématu [objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Class` příkaz k definování třídy a několika členů.  
  
 [!code-vb[VbVbalrStatements#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#62)]  
  
## <a name="see-also"></a>Viz také

- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
- [Struktury a třídy](../../programming-guide/language-features/data-types/structures-and-classes.md)
- [Interface – příkaz](interface-statement.md)
- [Module – příkaz](module-statement.md)
- [Property – příkaz](property-statement.md)
- [Doba života objektu: Vytváření a zničení objektů](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Postupy: Použití obecné třídy](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
