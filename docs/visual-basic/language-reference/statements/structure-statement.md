---
title: Structure – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Structure
- Structure
helpviewer_keywords:
- user-defined types [Visual Basic], Structure statement
- compound data types [Visual Basic]
- Structure keyword [Visual Basic]
- Structure statement [Visual Basic]
- UDT (user-defined types)
- types [Visual Basic], user-defined
ms.assetid: 9bd1deea-2a89-4cdc-812c-6dcbb947c391
ms.openlocfilehash: cec04880dd7cadc627ab090a45468dbad83c8d84
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583211"
---
# <a name="structure-statement"></a>Structure – příkaz
Deklaruje název struktury a zavádí definici proměnných, vlastností, událostí a procedur, které struktura zahrnuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] [ Partial ] _  
Structure name [ ( Of typelist ) ]  
    [ Implements interfacenames ]  
    [ datamemberdeclarations ]  
    [ methodmemberdeclarations ]  
End Structure  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attributelist`|Volitelné. Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může to být jedna z následujících:<br /><br /> -   [veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [chráněno](../../../visual-basic/language-reference/modifiers/protected.md)<br />-    –[přítel](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />[přítel chráněný](../../language-reference/modifiers/protected-friend.md) - <br/>- [Private Protected](../../language-reference/modifiers/private-protected.md) <br /><br /> Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`Partial`|Volitelné. Označuje částečnou definici struktury. Zobrazit [částečné](../../../visual-basic/language-reference/modifiers/partial.md).|  
|`name`|Požadováno. Název této struktury Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Volitelné. Určuje, že se jedná o obecnou strukturu.|  
|`typelist`|Povinné, pokud použijete klíčové slovo [of](../../../visual-basic/language-reference/statements/of-clause.md) . Seznam parametrů typu pro tuto strukturu Viz [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Implements`|Volitelné. Označuje, že tato struktura implementuje členy jednoho nebo více rozhraní. Viz [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md).|  
|`interfacenames`|Vyžaduje se, pokud použijete příkaz `Implements`. Názvy rozhraní, které tato struktura implementuje.|  
|`datamemberdeclarations`|Požadováno. Nula nebo více `Const`, `Dim`, `Enum` nebo `Event` příkazy pro deklaraci *datových členů* struktury.|  
|`methodmemberdeclarations`|Volitelné. Nula nebo více deklarací `Function`, `Operator`, `Property` nebo `Sub` procedur, které slouží jako *Členové metody* struktury.|  
|`End Structure`|Požadováno. Ukončí definici `Structure`.|  
  
## <a name="remarks"></a>Poznámky  
 Příkaz `Structure` definuje typ složené hodnoty, kterou můžete přizpůsobit. *Struktura* je generalizace uživatelsky definovaného typu (UDT) předchozích verzí Visual Basic. Další informace najdete v tématu [struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md).  
  
 Struktury podporují mnoho stejných funkcí jako třídy. Například struktury mohou mít vlastnosti a postupy, mohou implementovat rozhraní a mohou mít parametrizované konstruktory. Existují však významné rozdíly mezi strukturami a třídami v oblastech, jako jsou dědičnost, deklarace a použití. Třídy jsou také typy odkazů a struktury jsou typy hodnot. Další informace naleznete v tématu [struktury a třídy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md).  
  
 @No__t_0 můžete použít jenom na úrovni oboru názvů nebo modulu. To znamená, že *kontext deklarace* struktury musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedura nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Struktury se ve výchozím nastavení přistupují k [příteli](../../../visual-basic/language-reference/modifiers/friend.md) . Můžete upravit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidly  
  
- **Vnoření.** Můžete definovat jednu strukturu v rámci jiné. Vnější struktura se nazývá *obsažená struktura*a vnitřní struktura se nazývá *vnořená struktura*. Nemůžete ale přistupovat k členům vnořené struktury prostřednictvím obsahující struktury. Místo toho je nutné deklarovat proměnnou datového typu vnořené struktury.  
  
- **Deklarace člena** Musíte deklarovat každého člena struktury. Člen struktury nemůže být [chráněný](../../../visual-basic/language-reference/modifiers/protected.md) ani `Protected Friend`, protože nic nemůže dědit ze struktury. Samotnou strukturu však lze `Protected` nebo `Protected Friend`.  
  
     V rámci struktury můžete deklarovat nula nebo více nesdílených proměnných nebo nesdílených nevlastních událostí. Nemůžete mít jenom konstanty, vlastnosti a postupy, i když některé z nich nejsou sdílené.  
  
- **Operace.** V rámci deklarace nelze inicializovat hodnotu žádného nesdíleného datového členu struktury. Takový datový člen musíte buď inicializovat pomocí parametrizovaného konstruktoru ve struktuře, nebo přiřadit hodnotu členu po vytvoření instance struktury.  
  
- **Dědičnost.** Struktura nemůže dědit z jiného typu než <xref:System.ValueType>, ze kterého všechny struktury dědí. Konkrétně jedna struktura nemůže dědit od druhé.  
  
     [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md) nelze použít v definici struktury, ani pro určení <xref:System.ValueType>.  
  
- **Provádění.** Pokud struktura používá [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md), je nutné implementovat každého člena definovaného každým rozhraním, které zadáte v `interfacenames`.  
  
- **Výchozí vlastnost.** Struktura může určovat maximálně jednu vlastnost jako *výchozí vlastnost*pomocí [výchozího](../../../visual-basic/language-reference/modifiers/default.md) modifikátoru. Další informace najdete v tématu [výchozí](../../../visual-basic/language-reference/modifiers/default.md).  
  
## <a name="behavior"></a>Předvídatelně  
  
- **Úroveň přístupu.** V rámci struktury můžete deklarovat každého člena s vlastní úrovní přístupu. Všechny členy struktury jsou ve výchozím nastavení [veřejným](../../../visual-basic/language-reference/modifiers/public.md) přístupem. Všimněte si, že pokud má struktura vlastní více úrovní přístupu, automaticky se tím omezí přístup k jejím členům, i když upravíte jejich úrovně přístupu modifikátory přístupu.  
  
- **Oboru.** Struktura je v oboru, který obsahuje obor názvů, třídu, strukturu nebo modul.  
  
     Rozsah každého člena struktury je celá struktura.  
  
- **Platné.** Struktura sama o sobě nemá život. Místo toho má každá instance struktury životnost nezávisle na všech ostatních instancích.  
  
     Doba životnosti instance začíná, když je vytvořena [novou klauzulí operátoru](../../../visual-basic/language-reference/operators/new-operator.md) . Končí v případě, že skončí životnost proměnné, která ho obsahuje.  
  
     Nemůžete roztáhnout dobu života instance struktury. Modul nabízí sbližování funkcí statické struktury. Další informace naleznete v tématu [příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md).  
  
     Členové struktury mají životnost v závislosti na tom, jak a kde jsou deklarovány. Další informace naleznete v části "doba života" v [příkazu třídy](../../../visual-basic/language-reference/statements/class-statement.md).  
  
- **Vydal.** Kód mimo strukturu musí kvalifikovat název člena s názvem této struktury.  
  
     Pokud kód uvnitř vnořené struktury vytvoří nekvalifikovaný odkaz na prvek programování, Visual Basic vyhledá prvek nejprve ve vnořené struktuře, poté v jeho obsahující struktuře a tak dále k vnějšímu nadřazenému prvku. Další informace naleznete v tématu [odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
- **Spotřeba paměti.** Stejně jako u všech složených datových typů nemůžete bezpečně vypočítat celkovou spotřebu paměti struktury tím, že přidáváte dohromady jmenovité přidělení úložiště jeho členů. Navíc nemůžete bezpečně předpokládat, že pořadí úložiště v paměti je stejné jako vaše pořadí deklarace. Pokud potřebujete řídit rozložení úložiště struktury, můžete použít atribut <xref:System.Runtime.InteropServices.StructLayoutAttribute> u příkazu `Structure`.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Structure` k definování sady souvisejících dat pro zaměstnance. Zobrazuje použití `Public`, `Friend` a `Private` členů, aby odrážela citlivost datových položek. Také ukazuje proceduru, vlastnost a členy události.  
  
 [!code-vb[VbVbalrStatements#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)
- [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Struktury a třídy](../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
